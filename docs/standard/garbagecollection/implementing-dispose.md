---
title: "Implémentation d’une méthode Dispose"
description: "Implémentation d’une méthode Dispose"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: eca6cdc3-6a14-4296-86fb-1eb2f21455b0
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: dfe2cebfbcf1f4c2697683ebda8c1e11567fd015

---

# <a name="implementing-a-dispose-method"></a>Implémentation d’une méthode Dispose

Vous implémentez une méthode [Dispose](xref:System.IDisposable.Dispose) pour libérer les ressources non managées utilisées par votre application. Le Garbage collector .NET n’alloue pas de mémoire non managée, et n’en libère pas non plus. 

Le modèle pour supprimer un objet, dénommé « modèle de suppression », impose un ordre sur la durée de vie d’un objet. Le modèle de suppression est utilisé uniquement pour les objets qui accèdent à des ressources non managées, telles que les handles de fichiers et de canaux, les handles d’attente, les handles d’attente ou les pointeurs vers les blocs de mémoire non managée. Cela est dû au fait que le récupérateur de mémoire est très efficace pour récupérer les objets managés inutilisés, mais ne peut pas récupérer les objets non managés.

Le modèle de suppression comporte deux variantes :

* Vous encapsulez chaque ressource non managée utilisée par un type dans un handle sécurisé (autrement dit, dans une classe dérivée de [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)). Dans ce cas, vous implémentez l’interface [IDisposable](xref:System.IDisposable) et une méthode `Dispose(Boolean)` supplémentaire. Il s’agit de la variante recommandée. Elle ne requiert pas le remplacement de la méthode [Object.Finalize](xref:System.Object.Finalize). 

> [!NOTE]
> L’espace de noms [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) fournit un ensemble de classes dérivées de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle), qui sont répertoriées dans la section [Utilisation des handles sécurisés](#using-safe-handles). Si vous ne parvenez pas à trouver une classe qui convient pour libérer votre ressource non managée, vous pouvez implémenter votre propre sous-classe de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle). 
 
* Vous implémentez l’interface [IDisposable](xref:System.IDisposable) et une méthode `Dispose(Boolean`) supplémentaire, puis vous remplacez la méthode [Object.Finalize](xref:System.Object.Finalize). Vous devez remplacer [Finalize](xref:System.Object.Finalize) pour garantir que les ressources non managées sont supprimées si votre implémentation de [IDisposable.Dispose](xref:System.IDisposable.Dispose) n’est pas appelée par un consommateur de votre type. Si vous utilisez la technique recommandée présentée dans le point précédent, la classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) effectue cette opération en votre nom. 

Pour garantir que les ressources sont toujours correctement nettoyées, une méthode [Dispose](xref:System.IDisposable.Dispose) doit pouvoir être appelée à plusieurs reprises sans lever d’exception. 

L’exemple de code fourni pour la méthode [GC.KeepAlive](xref:System.GC.KeepAlive(System.Object)) affiche la façon dont un garbage collection agressif peut entraîner l’exécution d’un finaliseur pendant qu’un membre de l’objet demandé est toujours en cours d’exécution. Il est conseillé d’appeler la méthode [KeepAlive](xref:System.GC.KeepAlive(System.Object)) à la fin d’une méthode `Dispose` longue.

## <a name="dispose-and-disposeboolean"></a>Dispose() et Dispose(Boolean)

L’interface [IDisposable](xref:System.IDisposable) exige l’implémentation d’une méthode unique sans paramètre, [Dispose](xref:System.IDisposable.Dispose). Toutefois, le modèle de suppression requiert deux méthodes `Dispose` à implémenter : 

* Implémentation non virtuelle publique de [IDisposable.Dispose](xref:System.IDisposable.Dispose) (`NonInheritable` en Visual Basic) qui n’a aucun paramètre.

* Méthode virtuelle (`Overridable` en Visual Basic) `Dispose` dont la signature est :

  ```cs
  protected virtual void Dispose(bool disposing)
  ```

  ```vb
  Protected Overridable Sub Dispose(disposing As Boolean)
  ```

### <a name="the-dispose-overload"></a>Surcharge de Dispose()

Comme la méthode `NonInheritable` sans paramètre non virtuelle (`Dispose` en Visual Basic) publique est appelée par un consommateur de type, son objectif est de libérer les ressources non managées et d'indiquer que le finaliseur, s'il en existe un, ne doit pas s'exécuter. De ce fait, son implémentation standard est la suivante :

```cs
public void Dispose()
{
   // Dispose of unmanaged resources.
   Dispose(true);
   // Suppress finalization.
   GC.SuppressFinalize(this);
}
```

```vb
Public Sub Dispose() _
           Implements IDisposable.Dispose
   ' Dispose of unmanaged resources.
   Dispose(True)
   ' Suppress finalization.
   GC.SuppressFinalize(Me)
End Sub
```

La méthode `Dispose` effectue le nettoyage de tous les objets. Le Garbage collector n’a plus donc besoin d’appeler la substitution [Object.Finalize](xref:System.Object.Finalize)des objets. Par conséquent, l’appel à la méthode [GC.SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) empêche le Garbage collector d’exécuter le finaliseur. Si le type n’a pas de finaliseur, l’appel à [SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) n’a aucun effet. Notez que le travail réel de libération des ressources non managées est effectué par la deuxième surcharge de la méthode `Dispose`.

### <a name="the-disposeboolean-overload"></a>Surcharge de Dispose(Boolean)

Dans la seconde surcharge, le paramètre *disposing* est un [Boolean](xref:System.Boolean) qui indique si l’appel de la méthode provient d’une méthode [Dispose](xref:System.IDisposable.Dispose) (sa valeur est `true`) ou d’un finaliseur (sa valeur est `false`). 

Le corps de la méthode se compose de deux blocs de code : 

* Un bloc qui libère les ressources non managées. Ce bloc s’exécute indépendamment de la valeur du paramètre *disposing*. 

* Un bloc conditionnel qui libère les ressources managées. Ce bloc s’exécute si la valeur de *disposing* est `true`. Les ressources managées qu'il libère peuvent inclure : 

    **Objets managés qui implémentent IDisposable**. Le bloc conditionnel peut être utilisé pour appeler leur implémentation de [Dispose](xref:System.IDisposable.Dispose). Si vous avez utilisé un handle sécurisé pour encapsuler votre ressource non managée, vous devez appeler l’implémentation de [SafeHandle.Dispose(Boolean](xref:System.Runtime.InteropServices.SafeHandle.Dispose(System.Boolean)) ici. 

    **Objets managés qui consomment de grandes quantités de mémoire ou consomment des ressources rares.** La libération de ces objets explicitement dans la méthode `Dispose` les libère plus rapidement que s'ils ont été récupérés de façon non déterministe par le récupérateur de mémoire. 


Si l’appel de la méthode vient d’un finaliseur (autrement dit, si *disposing* a la valeur `false`), seul le code qui libère les ressources non managées s’exécute. Étant donné que l'ordre dans lequel le récupérateur de mémoire détruit les objets managés pendant la finalisation n'est pas défini, l'appel de cette surcharge `Dispose` avec la valeur `false` empêche le finaliseur d'essayer de libérer les ressources managées qui peuvent avoir déjà été récupérées. 

## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implémentation du modèle de suppression d'une classe de base

Si vous implémentez le modèle de suppression d’une classe de base, vous devez spécifier ce qui suit : 

> [!IMPORTANT]
> Vous devez implémenter ce modèle pour toutes les classes de base qui implémentent [IDisposable](xref:System.IDisposable) et qui ne sont pas `sealed`. 
 
* Une implémentation de [Dispose](xref:System.IDisposable.Dispose) qui appelle la méthode `Dispose(Boolean)`. 

* Une méthode `Dispose(Boolean)` qui effectue le travail réel de libération des ressources. 

* Une classe dérivée de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode [Object.Finalize](xref:System.Object.Finalize). La classe [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) fournit un finaliseur qui vous permet de ne pas avoir à en coder un. 

Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui utilise un handle sécurisé. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub
End Class
```

> [!NOTE] 
> L’exemple précédent utilise un objet [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) pour illustrer le modèle, mais il est possible d’utiliser à la place n’importe quel objet dérivé de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle). Notez que l’exemple n’instancie pas correctement son objet [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle). 
 
Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui remplace [Object.Finalize](xref:System.Object.Finalize). 

```cs
using System;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }

   ~BaseClass()
   {
      Dispose(false);
   }
}
```

```vb
Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)      
   End Sub
End Class
```

> [!NOTE]
> En C#, vous substituez [Object.Finalize](xref:System.Object.Finalize) en définissant un `destructor`. 


## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implémentation du modèle de suppression d’une classe dérivée

Une classe dérivée d’une classe qui implémente l’interface [IDisposable](xref:System.IDisposable) ne doit pas implémenter [IDisposable](xref:System.IDisposable), car l’implémentation de la classe de base de [IDisposable.Dispose](xref:System.IDisposable.Dispose) est héritée par ses classes dérivées. À la place, pour implémenter le modèle de suppression d’une classe dérivée, vous fournissez ce qui suit : 

* Une méthode `protected Dispose(Boolean)` qui substitue la méthode de la classe de base et effectue le travail réel de libération des ressources de la classe dérivée. Cette méthode doit également appeler la méthode `Dispose(Boolean)` de la classe de base et lui passer une valeur `true` pour l’argument *disposing*. 

* Une classe dérivée de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode [Object.Finalize](xref:System.Object.Finalize). La classe [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)fournit un finaliseur qui vous permet de ne pas avoir à en coder un. Si vous fournissez un finaliseur, il doit appeler la surcharge `Dispose(Boolean)` avec un argument *disposing* égal à `false`. 

Voici le modèle général d’implémentation du modèle de suppression d’une classe dérivée qui utilise un handle sécurisé : 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //

      disposed = true;
      // Call base class implementation.
      base.Dispose(disposing);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class DerivedClass : Inherits BaseClass 
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call base class implementation.
      MyBase.Dispose(disposing)
   End Sub
End Class
```

> [!NOTE] 
> L’exemple précédent utilise un objet [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) pour illustrer le modèle, mais il est possible d’utiliser à la place n’importe quel objet dérivé de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle). Notez que l’exemple n’instancie pas correctement son objet [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle). 

Voici le modèle général d’implémentation du modèle de suppression d’une classe dérivée qui remplace [Object.Finalize](xref:System.Object.Finalize) :

```cs
using System;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;

      // Call the base class implementation.
      base.Dispose(disposing);
   }

   ~DerivedClass()
   {
      Dispose(false);
   }
}
```

```vb
Class DerivedClass : Inherits BaseClass
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call the base class implementation.
      MyBase.Dispose(disposing)
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)
   End Sub 
End Class
```

> [!NOTE]
> En C#, vous substituez [Object.Finalize](xref:System.Object.Finalize) en définissant un `destructor`.

## <a name="using-safe-handles"></a>Utilisation des handles sécurisés

L’écriture de code pour le finaliseur d’un objet est une tâche complexe qui peut provoquer des problèmes si elle n’est pas effectuée correctement. Par conséquent, nous vous recommandons de construire des objets [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) au lieu d’implémenter un finaliseur.

Les classes dérivées de la classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) simplifient les problèmes de durée de vie des objets en assignant et en libérant des handles sans interruption. Elles contiennent un finaliseur critique dont le fonctionnement pendant le déchargement d'un domaine d'application est garanti. Les classes dérivées suivantes de l’espace de noms [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) fournissent des handles sécurisés : 

* La classe [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle), [SafeMemoryMappedFileHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle) et [SafePipeHandle](xref:Microsoft.Win32.SafeHandles.SafePipeHandle), pour les fichiers, les fichiers mappés en mémoire et les canaux. 

* La classe [SafeMemoryMappedViewHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle), pour les vues de la mémoire. 

* Les classes [SafeNCryptKeyHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptkeyhandle(v=vs.110).aspx), [SafeNCryptProviderHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptproviderhandle(v=vs.110).aspx) et [SafeNCryptSecretHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptsecrethandle(v=vs.110).aspx), pour les constructions de chiffrement.

* La classe [SafeRegistryHandle](xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle), pour les clés de Registre. 

* La classe [SafeWaitHandle](xref:Microsoft.Win32.SafeHandles.SafeWaitHandle), pour les handles d’attente. 

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Utilisation d’un handle sécurisé pour implémenter le modèle de suppression d’une classe de base

L'exemple suivant illustre le modèle de suppression d'une classe de base, `DisposableStreamResource`, qui utilise un handle sécurisé pour encapsuler les ressources non managées. Il définit une classe `DisposableResource`qui utilise un [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) pour encapsuler un objet [Stream](xref:System.IO.Stream) qui représente un fichier ouvert. La méthode `DisposableResource` inclut également une seule propriété, `Size`, qui retourne le nombre total d'octets du flux de fichier. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;

public class DisposableStreamResource : IDisposable
{
   // Define constants.
   protected const uint GENERIC_READ = 0x80000000;
   protected const uint FILE_SHARE_READ = 0x00000001;
   protected const uint OPEN_EXISTING = 3;
   protected const uint FILE_ATTRIBUTE_NORMAL = 0x80;
   protected IntPtr INVALID_HANDLE_VALUE = new IntPtr(-1);
   private const int INVALID_FILE_SIZE = unchecked((int) 0xFFFFFFFF);

   // Define Windows APIs.
   [DllImport("kernel32.dll", EntryPoint = "CreateFileW", CharSet = CharSet.Unicode)]
   protected static extern IntPtr CreateFile (
                                  string lpFileName, uint dwDesiredAccess, 
                                  uint dwShareMode, IntPtr lpSecurityAttributes, 
                                  uint dwCreationDisposition, uint dwFlagsAndAttributes, 
                                  IntPtr hTemplateFile);

   [DllImport("kernel32.dll")]
   private static extern int GetFileSize(SafeFileHandle hFile, out int lpFileSizeHigh);

   // Define locals.
   private bool disposed = false;
   private SafeFileHandle safeHandle; 
   private long bufferSize;
   private int upperWord;

   public DisposableStreamResource(string filename)
   {
      if (filename == null)
         throw new ArgumentNullException("The filename cannot be null.");
      else if (filename == "")
         throw new ArgumentException("The filename cannot be an empty string.");

      IntPtr handle = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                 IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                 IntPtr.Zero);
      if (handle != INVALID_HANDLE_VALUE)
         safeHandle = new SafeFileHandle(handle, true);
      else
         throw new FileNotFoundException(String.Format("Cannot open '{0}'", filename));

      // Get file size.
      bufferSize = GetFileSize(safeHandle, out upperWord); 
      if (bufferSize == INVALID_FILE_SIZE)
         bufferSize = -1;
      else if (upperWord > 0) 
         bufferSize = (((long)upperWord) << 32) + bufferSize;
   }

   public long Size 
   { get { return bufferSize; } }

   public void Dispose()
   {
      Dispose(true);
      GC.SuppressFinalize(this);
   }           

   protected virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Dispose of managed resources here.
      if (disposing)
         safeHandle.Dispose();

      // Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = true;
   }  
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource : Implements IDisposable
   ' Define constants.
   Protected Const GENERIC_READ As UInteger = &H80000000ui
   Protected Const FILE_SHARE_READ As UInteger = &H0000000i
   Protected Const OPEN_EXISTING As UInteger = 3
   Protected Const FILE_ATTRIBUTE_NORMAL As UInteger = &H80
   Protected INVALID_HANDLE_VALUE As New IntPtr(-1)
   Private Const INVALID_FILE_SIZE As Integer = &HFFFFFFFF

   ' Define Windows APIs.
   Protected Declare Function CreateFile Lib "kernel32" Alias "CreateFileA" (
                                         lpFileName As String, dwDesiredAccess As UInt32, 
                                         dwShareMode As UInt32, lpSecurityAttributes As IntPtr, 
                                         dwCreationDisposition As UInt32, dwFlagsAndAttributes As UInt32, 
                                         hTemplateFile As IntPtr) As IntPtr
   Private Declare Function GetFileSize Lib "kernel32" (hFile As SafeFileHandle, 
                                                        ByRef lpFileSizeHigh As Integer) As Integer

   ' Define locals.
   Private disposed As Boolean = False
   Private safeHandle As SafeFileHandle 
   Private bufferSize As Long 
   Private upperWord As Integer

   Public Sub New(filename As String)
      If filename Is Nothing Then
         Throw New ArgumentNullException("The filename cannot be null.")
      Else If filename = ""
         Throw New ArgumentException("The filename cannot be an empty string.")
      End If

      Dim handle As IntPtr = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                        IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                        IntPtr.Zero)
      If handle <> INVALID_HANDLE_VALUE Then
         safeHandle = New SafeFileHandle(handle, True)
      Else
         Throw New FileNotFoundException(String.Format("Cannot open '{0}'", filename))
      End If

      ' Get file size.
      bufferSize = GetFileSize(safeHandle, upperWord) 
      If bufferSize = INVALID_FILE_SIZE Then
         bufferSize = -1
      Else If upperWord > 0 Then 
         bufferSize = (CLng(upperWord) << 32) + bufferSize
      End If     
   End Sub

   Public ReadOnly Property Size As Long
      Get
         Return bufferSize
      End Get
   End Property

   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
   End Sub           

   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Dispose of managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      ' Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = True
   End Sub  
End Class
```

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Utilisation d'un handle sécurisé pour implémenter le modèle de suppression d'une classe dérivée

L'exemple suivant illustre le modèle de suppression d'une classe dérivée, `DisposableStreamResource2`, qui hérite de la classe `DisposableStreamResource` présentée dans l'exemple précédent. La classe ajoute une méthode supplémentaire, `WriteFileInfo`, et utilise un objet [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) pour encapsuler le handle du fichier accessible en écriture. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;
using System.Threading;

public class DisposableStreamResource2 : DisposableStreamResource
{
   // Define additional constants.
   protected const uint GENERIC_WRITE = 0x40000000; 
   protected const uint OPEN_ALWAYS = 4;

   // Define additional APIs.
   [DllImport("kernel32.dll")]   
   protected static extern bool WriteFile(
                                SafeFileHandle safeHandle, string lpBuffer, 
                                int nNumberOfBytesToWrite, out int lpNumberOfBytesWritten,
                                IntPtr lpOverlapped);

   // Define locals.
   private bool disposed = false;
   private string filename;
   private bool created = false;
   private SafeFileHandle safeHandle;

   public DisposableStreamResource2(string filename) : base(filename)
   {
      this.filename = filename;
   }

   public void WriteFileInfo()
   { 
      if (! created) {
         IntPtr hFile = CreateFile(xref:".\FileInfo.txt", GENERIC_WRITE, 0, 
                                   IntPtr.Zero, OPEN_ALWAYS, 
                                   FILE_ATTRIBUTE_NORMAL, IntPtr.Zero);
         if (hFile != INVALID_HANDLE_VALUE)
            safeHandle = new SafeFileHandle(hFile, true);
         else
            throw new IOException("Unable to create output file.");

         created = true;
      }

      string output = String.Format("{0}: {1:N0} bytes\n", filename, Size);
      int bytesWritten;
      bool result = WriteFile(safeHandle, output, output.Length, out bytesWritten, IntPtr.Zero);                                     
   }

   protected new virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Release any managed resources here.
      if (disposing)
         safeHandle.Dispose();

      disposed = true;

      // Release any unmanaged resources not wrapped by safe handles here.

      // Call the base class implementation.
      base.Dispose(true);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource2 : Inherits DisposableStreamResource
   ' Define additional constants.
   Protected Const GENERIC_WRITE As Integer = &H40000000 
   Protected Const OPEN_ALWAYS As Integer = 4

   ' Define additional APIs.
   Protected Declare Function WriteFile Lib "kernel32.dll" (
                              safeHandle As SafeFileHandle, lpBuffer As String, 
                              nNumberOfBytesToWrite As Integer, ByRef lpNumberOfBytesWritten As Integer,
                              lpOverlapped As Object) As Boolean

   ' Define locals.
   Private disposed As Boolean = False
   Private filename As String
   Private created As Boolean = False
   Private safeHandle As SafeFileHandle

   Public Sub New(filename As String)
      MyBase.New(filename)
      Me.filename = filename
   End Sub

   Public Sub WriteFileInfo() 
      If Not created Then
         Dim hFile As IntPtr = CreateFile(".\FileInfo.txt", GENERIC_WRITE, 0, 
                                          IntPtr.Zero, OPEN_ALWAYS, 
                                          FILE_ATTRIBUTE_NORMAL, IntPtr.Zero)
         If hFile <> INVALID_HANDLE_VALUE Then
            safeHandle = New SafeFileHandle(hFile, True)
         Else
            Throw New IOException("Unable to create output file.")
         End If
         created = True
      End If
      Dim output As String = String.Format("{0}: {1:N0} bytes {2}", filename, Size, 
                                           vbCrLf)
      WriteFile(safeHandle, output, output.Length, 0&, Nothing)                                     
   End Sub

   Protected Overloads Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Release any managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      disposed = True
      ' Release any unmanaged resources not wrapped by safe handles here.

      ' Call the base class implementation.
      MyBase.Dispose(True)
   End Sub
End Class
```

## <a name="see-also"></a>Voir aussi

[SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object))

[IDisposable](xref:System.IDisposable)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)

[Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles)

[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)



<!--HONumber=Nov16_HO1-->


