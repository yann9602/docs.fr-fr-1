---
title: "Utilisation d’objets implémentant IDisposable"
description: "Utilisation d’objets implémentant IDisposable"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: df780a6e-734e-44b8-9747-9f7783f79e20
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 42b82c6a906a803b45976c01a55e585cd3b7542f

---

# <a name="using-objects-that-implement-idisposable"></a>Utilisation d’objets implémentant IDisposable

Le Garbage collector du Common Language Runtime libère la mémoire utilisée par les objets non managés, mais les types qui utilisent les ressources non managées implémentent l’interface [IDisposable](xref:System.IDisposable) pour permettre la récupération de cette mémoire non managée. Une fois que vous avez fini d’utiliser un objet qui implémente [IDisposable](xref:System.IDisposable), vous devez appeler l’implémentation de [IDisposable.Dispose](xref:System.IDisposable.Dispose) de l’objet. Vous pouvez le faire de deux façons :

* Avec l’instruction `using`C# ou l’instruction `Using`Visual Basic.

* En implémentant un bloc `try/finally`. 

## <a name="the-using-statement"></a>Instruction using

L’instruction `using`en C# et l’instruction `Using` en Visual Basic simplifient le code que vous devez écrire pour créer et nettoyer un objet. L’instruction `using` obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l’objet. Toutefois, l’instruction `using` est utile uniquement pour les objets utilisés dans la portée de la méthode dans laquelle elles sont construites. 

L’exemple suivant utilise l’instruction `using` pour créer et libérer un objet [System.IO.StreamReader](xref:System.IO.StreamReader).

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      using (StreamReader s = new StreamReader("File1.txt")) {
         int charsRead = 0;
         while (s.Peek() != -1) {
            charsRead = s.Read(buffer, 0, buffer.Length);
            //
            // Process characters read.
            //   
         }
         s.Close();    
      }

   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
      Using s As New StreamReader("File1.txt")
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      End Using
   End Sub
End Module
```

Notez que, bien que la classe [StreamReader](xref:System.IO.StreamReader) implémente l’interface [IDisposable](xref:System.IDisposable), ce qui signifie qu’elle utilise une ressource non managée, l’exemple n’appelle pas explicitement la méthode [StreamReader.Dispose](xref:System.IO.StreamReader.Dispose(System.Boolean)). Quand le compilateur C# ou Visual Basic rencontre l’instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try/finally`. 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      {
         StreamReader s = new StreamReader("File1.txt"); 
         try {
            int charsRead = 0;
            while (s.Peek() != -1) {
               charsRead = s.Read(buffer, 0, buffer.Length);
               //
               // Process characters read.
               //   
            }
            s.Close();
         }
         finally {
            if (s != null)
               ((IDisposable)s).Dispose();     
         }       
      }
   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
''      Dim s As New StreamReader("File1.txt")
With s As New StreamReader("File1.txt")
      Try
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      Finally
         If s IsNot Nothing Then DirectCast(s, IDisposable).Dispose()
      End Try
End With
   End Sub
End Module
```

L’instruction `using` en C# vous permet d’acquérir plusieurs ressources dans une seule instruction, ce qui revient en interne à plusieurs instructions using imbriquées. L’exemple suivant instancie deux objets [StreamReader](xref:System.IO.StreamReader) pour lire le contenu de deux fichiers différents. 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer1 = new Char[50], buffer2 = new Char[50];

      using (StreamReader version1 = new StreamReader("file1.txt"),
                          version2 = new StreamReader("file2.txt")) {
         int charsRead1, charsRead2 = 0;
         while (version1.Peek() != -1 && version2.Peek() != -1) {
            charsRead1 = version1.Read(buffer1, 0, buffer1.Length);
            charsRead2 = version2.Read(buffer2, 0, buffer2.Length);
            //
            // Process characters read.
            //
         }
         version1.Close();
         version2.Close();
      }
   }
}
```

## <a name="tryfinally-block"></a>Bloc try/finally

Au lieu d’encapsuler un bloc `try/finally` dans une instruction `using`, vous pouvez choisir d’implémenter le bloc `try/finally` directement. Il peut s'agir de votre style personnel en matière de codage, ou vous pouvez procéder ainsi pour l'une des raisons suivantes : 

* Pour insérer un bloc `catch` afin de gérer toutes les exceptions levées dans le bloc `try`. Sinon, toutes les exceptions levées par l’instruction `using` ne sont pas gérées, de même que toutes les exceptions levées dans le bloc `using` si un bloc `try/catch` n’est pas présent. 

* Pour instancier un objet qui implémente [IDisposable](xref:System.IDisposable) dont la portée n’est pas locale au bloc dans lequel elle est déclarée. 

L’exemple suivant est similaire à l’exemple précédent, mais il utilise un bloc `try/catch/finally` pour instancier, utiliser et supprimer un objet [StreamReader](xref:System.IO.StreamReader), ainsi que pour gérer les exceptions levées par le constructeur [StreamReader](xref:System.IO.StreamReader) et sa méthode [ReadToEnd](xref:System.IO.StreamReader.ReadToEnd). Notez que le code du bloc `finally` vérifie que l’objet qui implémente [IDisposable](xref:System.IDisposable) n’est pas `null` avant d’appeler la méthode [Dispose](xref:System.IDisposable.Dispose). La non-exécution de cette opération peut générer une exception [NullReferenceException](xref:System.NullReferenceException) au moment de l’exécution. 

```cs
using System;
using System.Globalization;
using System.IO;

public class Example
{
   public static void Main()
   {
      StreamReader sr = null;
      try {
         sr = new StreamReader("file1.txt");
         String contents = sr.ReadToEnd();
         sr.Close();
         Console.WriteLine("The file has {0} text elements.", 
                           new StringInfo(contents).LengthInTextElements);    
      }      
      catch (FileNotFoundException) {
         Console.WriteLine("The file cannot be found.");
      }   
      catch (IOException) {
         Console.WriteLine("An I/O error has occurred.");
      }
      catch (OutOfMemoryException) {
         Console.WriteLine("There is insufficient memory to read the file.");   
      }
      finally {
         if (sr != null) sr.Dispose();     
      }
   }
}
```

```vb
Imports System.Globalization
Imports System.IO

Module Example
   Public Sub Main()
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader("file1.txt")
         Dim contents As String = sr.ReadToEnd()
         sr.Close()
         Console.WriteLine("The file has {0} text elements.", 
                           New StringInfo(contents).LengthInTextElements)    
      Catch e As FileNotFoundException
         Console.WriteLine("The file cannot be found.")
      Catch e As IOException
         Console.WriteLine("An I/O error has occurred.")
      Catch e As OutOfMemoryException
         Console.WriteLine("There is insufficient memory to read the file.")   
      Finally 
         If sr IsNot Nothing Then sr.Dispose()     
      End Try
   End Sub
End Module
```

Vous pouvez suivre ce modèle de base si vous choisissez d’implémenter (ou que vous devez implémenter) un bloc `try/finally`, car votre langage de programmation ne prend pas en charge l’instruction `using` mais autorise les appels directs à la méthode [Dispose](xref:System.IDisposable.Dispose). 

## <a name="see-also"></a>Voir aussi

[Nettoyage de ressources non managées](unmanaged.md)





<!--HONumber=Nov16_HO3-->


