---
title: "Suppression des espaces et des caractères d’une chaîne"
description: "Suppression des espaces et des caractères d’une chaîne"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 95d818bc-2661-43f6-adb8-13b53abf9682
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 6105861882c3bfd525a2d902fd2600f5da10417d

---

# <a name="trimming-and-removing-characters-from-strings"></a>Suppression des espaces et des caractères d’une chaîne

Si vous analysez une phrase en mots individuels, vous risquez d’obtenir des mots incluant des espaces vides (également appelés espaces blancs) à chaque extrémité du mot. Dans ce cas, vous pouvez utiliser l’une des méthodes de suppression de la classe [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) pour supprimer n’importe quel nombre d’espaces ou d’autres caractères à partir d’une position spécifiée dans la chaîne. Le tableau suivant décrit les méthodes de suppression disponibles.

Nom de la méthode | Utilisation
----------- | ---
[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | Supprime les espaces blancs ou caractères spécifiés dans un tableau de caractères à partir du début et la fin d’une chaîne.
[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) | Supprime les caractères spécifiés dans un tableau de caractères à partir de la fin d’une chaîne.
[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) | Supprime les caractères spécifiés dans un tableau de caractères à partir du début d’une chaîne.
[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) | Supprime un nombre spécifié de caractères à partir de la position d’index spécifiée dans une chaîne.


## <a name="trim"></a>Trim

Vous pouvez facilement supprimer les espaces blancs situés aux deux extrémités d’une chaîne à l’aide de la méthode [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim), comme indiqué dans l’exemple suivant.

```csharp
string MyString = " Big   ";
Console.WriteLine("Hello{0}World!", MyString);
string TrimString = MyString.Trim();
Console.WriteLine("Hello{0}World!", TrimString);
//       The example displays the following output:
//             Hello Big   World!
//             HelloBigWorld!
```

```vb
Dim MyString As String = " Big   "
Console.WriteLine("Hello{0}World!", MyString)
Dim TrimString As String = MyString.Trim()
Console.WriteLine("Hello{0}World!", TrimString)
' The example displays the following output:
'       Hello Big   World!
'       HelloBigWorld!
```

Vous pouvez également supprimer les caractères que vous spécifiez dans un tableau de caractères à partir du début et de la fin d’une chaîne. L’exemple suivant permet de supprimer les espaces blancs, les points et les astérisques.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String header = "* A Short String. *";
      Console.WriteLine(header);
      Console.WriteLine(header.Trim( new Char[] { ' ', '*', '.' } ));
   }
}
// The example displays the following output:
//       * A Short String. *
//       A Short String
```

```vb
Module Example
   Public Sub Main()
      Dim header As String = "* A Short String. *"
      Console.WriteLine(header)
      Console.WriteLine(header.Trim( { " "c, "*"c, "."c } ))
   End Sub
End Module
' The example displays the following output:
'       * A Short String. *
'       A Short String
```

## <a name="trimend"></a>TrimEnd

La méthode [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) supprime les caractères à partir de la fin d’une chaîne, créant ainsi un objet String. Un tableau de caractères est passé à cette méthode pour spécifier les caractères à supprimer. L’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression. La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.

L’exemple suivant supprime les dernières lettres d’une chaîne à l’aide de la méthode TrimEnd. Dans cet exemple, la position du caractère `'r'` et du caractère `'W'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance. Remarquez que ce code supprime le dernier mot de `MyString` plus une partie du premier.

```csharp
string MyString = "Hello World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

Ce code affiche `He` dans la console.

L’exemple suivant supprime le dernier mot d’une chaîne à l’aide de la méthode [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])). Dans ce code, une virgule suit le mot `Hello` et, étant donné que la virgule n’est pas spécifiée dans le tableau de caractères à supprimer, la suppression s’arrête au niveau de la virgule.

```csharp
string MyString = "Hello, World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello, World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

Ce code affiche `Hello,` dans la console.

## <a name="trimstart"></a>TrimStart

La méthode [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) est similaire à la méthode [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), si ce n’est qu’elle crée une chaîne en supprimant les caractères à partir du début d’un objet string existant. Un tableau de caractères est passé à la méthode [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) pour spécifier les caractères à supprimer. Comme avec la méthode [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), l’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression. La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.

L’exemple suivant supprime le premier mot d’une chaîne. Dans cet exemple, la position du caractère `'l'` et du caractère `'H'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance.

```csharp
string MyString = "Hello World!";
char[] MyChar = {'e', 'H','l','o',' ' };
string NewString = MyString.TrimStart(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"e","H","l","o"," " }
Dim NewString As String = MyString.TrimStart(MyChar)
Console.WriteLine(NewString)
```

Ce code affiche `World!` dans la console.

## <a name="remove"></a>Remove

La méthode [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) supprime un nombre spécifié de caractères en commençant à la position spécifiée dans une chaîne existante. Cette méthode suppose un index de base zéro.

L’exemple suivant supprime dix caractères d’une chaîne en commençant à la position cinq d’un index de base zéro de la chaîne.

```csharp
string MyString = "Hello Beautiful World!";
Console.WriteLine(MyString.Remove(5,10));
// The example displays the following output:
//         Hello World!  
```

```vb
Dim MyString As String = "Hello Beautiful World!"
Console.WriteLine(MyString.Remove(5,10))
' The example displays the following output:
'         Hello World!
```

Vous pouvez également supprimer un caractère spécifié ou une sous-chaîne spécifiée d’une chaîne en appelant la méthode [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) et en spécifiant une chaîne vide ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) comme valeur de remplacement. L’exemple suivant supprime toutes les virgules d’une chaîne.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String phrase = "a cold, dark night";
      Console.WriteLine("Before: {0}", phrase);
      phrase = phrase.Replace(",", "");
      Console.WriteLine("After: {0}", phrase);
   }
}
// The example displays the following output:
//       Before: a cold, dark night
//       After: a cold dark night
```

```vb
Module Example
   Public Sub Main()
      Dim phrase As String = "a cold, dark night"
      Console.WriteLine("Before: {0}", phrase)
      phrase = phrase.Replace(",", "")
      Console.WriteLine("After: {0}", phrase)
   End Sub
End Module
' The example displays the following output:
'       Before: a cold, dark night
'       After: a cold dark night
```

## <a name="see-also"></a>Voir aussi

[Opérations de chaînes de base](basic-string-operations.md)




<!--HONumber=Nov16_HO3-->


