---
title: "Passing Structures | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "platform invoke, calling unmanaged functions"
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Passing Structures
De nombreuses fonctions non managées comptent sur vous pour passer, en tant que paramètre à la fonction, des membres de structures \(types définis par l'utilisateur en Visual Basic\) ou des membres de classes qui sont définis dans du code managé.  Lorsque vous passez des structures ou des classes à du code non managé à l'aide de l'appel de code non managé, vous devez fournir des informations supplémentaires pour préserver la mise en forme et l'alignement d'origine.  Cette rubrique présente l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> que vous utilisez pour définir des types mis en forme.  Pour des structures et des classes managées, vous pouvez effectuer une sélection parmi plusieurs comportements prévisibles de mise en forme fournis par l'énumération **LayoutKind**.  
  
 Une différence importante entre les types structure et classe constitue le point central des concepts présentés dans cette rubrique.  Les structures sont des types valeur et les classes sont des types référence ; les classes fournissent toujours au moins un niveau d'indirection de mémoire \(un pointeur vers une valeur\).  Cette différence est importante parce que des fonctions non managées exigent souvent une indirection, comme le montrent les signatures contenues dans la première colonne du tableau suivant.  Les déclarations de classes et de structures managées figurant dans les autres colonnes montrent le degré auquel vous pouvez ajuster le niveau d'indirection dans votre déclaration.  Les déclarations sont fournies à la fois pour Visual Basic et Visual C\#.  
  
|Signature non managée|Déclaration managée :                <br /> aucune indirection               <br />  `Structure MyType`  <br />  `struct MyType;`|Déclaration managée :                <br /> un niveau d'indirection.               <br />  `Class MyType`  <br />  `class MyType;`|  
|---------------------------|---------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Exige aucun niveau d'indirection.|`DoWork(ByVal x As MyType)`  <br />  `DoWork(MyType x)`<br /><br /> Ajoute aucun niveau d'indirection.|Impossible parce qu'il y a déjà un niveau d'indirection.|  
|`DoWork(MyType* x);`<br /><br /> Exige un niveau d'indirection.|`DoWork(ByRef x As MyType)`  <br />  `DoWork(ref MyType x)`<br /><br /> Ajoute un niveau d'indirection.|`DoWork(ByVal x As MyType)`  <br />  `DoWork(MyType x)`<br /><br /> Ajoute aucun niveau d'indirection.|  
|`DoWork(MyType** x);`<br /><br /> Exige deux niveaux d'indirection.|Impossible car **ByRef** **ByRef** ou `ref` `ref` ne peut être utilisé.|`DoWork(ByRef x As MyType)`  <br />  `DoWork(ref MyType x)`<br /><br /> Ajoute un niveau d'indirection.|  
  
 Le tableau décrit les instructions suivantes pour les déclarations d'appel de code non managé :  
  
-   Utilisez une structure passée par valeur lorsque la fonction non managée n'exige aucune indirection.  
  
-   Utilisez une structure passée par référence ou une classe passée par valeur lorsque la fonction non managée exige un niveau d'indirection.  
  
-   Utilisez une classe passée par référence lorsque la fonction non managée exige deux niveaux d'indirection.  
  
## Déclaration et passage de structures  
 L'exemple suivant montre comment définir les structures `Point` et `Rect` dans du code managé et passer les types en tant que paramètres à la fonction **PtInRect** dans le fichier User32.dll.  **PtInRect** possède la signature non managée suivante :  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Notez que vous devez passer la structure Rect par référence, car la fonction nécessite un pointeur vers un type RECT.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## Déclaration et passage de classes  
 Vous pouvez passer les membres d'une classe à une fonction DLL non managée, à partir du moment où la classe possède une disposition de membre fixe.  L'exemple suivant montre comment passer les membres d'une classe `MySystemTime`, qui sont définis dans un ordre séquentiel, à **GetSystemTime** dans le fichier User32.dll.  **GetSystemTime** possède la signature non managée suivante :  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Contrairement aux types valeur, les classes ont toujours au moins un niveau d'indirection.  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## Voir aussi  
 [Calling a DLL Function](../../../docs/framework/interop/calling-a-dll-function.md)   
 [StructLayoutAttribute, classe](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)   
 [StructLayoutAttribute, classe](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)   
 [FieldOffsetAttribute, classe](frlrfSystemRuntimeInteropServicesFieldOffsetAttributeClassTopic)