---
title: "Specifying an Entry Point | Microsoft Docs"
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
  - "EntryPoint field"
  - "platform invoke, attribute fields"
  - "attribute fields in platform invoke, EntryPoint"
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Specifying an Entry Point
Un point d'entrée identifie l'emplacement d'une fonction dans une DLL.  Dans un projet managé, le point d'entrée ordinal ou nominal d'origine d'une fonction cible identifie cette fonction sur les limites d'interopérabilité.  De plus, vous pouvez mapper le point d'entrée à un nom différent, en attribuant effectivement un nouveau nom à la fonction.  
  
 La liste suivante récapitule les raisons pouvant être à l'origine de l'attribution d'un nouveau nom à une fonction DLL :  
  
-   pour éviter d'utiliser des noms de fonction API respectant la casse ;  
  
-   pour respecter des normes d'attribution de noms existantes ;  
  
-   pour prendre en charge des fonctions acceptant des types de données différents \(en déclarant plusieurs versions de la même fonction DLL\) ;  
  
-   pour simplifier l'utilisation d'interfaces API contenant des versions ANSI et Unicode.  
  
 Cette rubrique indique comment renommer une fonction DLL dans du code managé.  
  
## Attribution d'un nouveau nom à une fonction dans Visual Basic  
 Visual Basic utilise le mot clé **Function** dans l'instruction **Declare** pour définir le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=fullName>.  L'exemple suivant illustre une déclaration de base.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 Vous pouvez remplacer le point d'entrée **MessageBox** par **MsgBox** en incluant le mot clé **Alias** dans votre définition, comme le montre l'exemple suivant.  Dans les deux exemples, le mot clé **Auto** rend inutile la spécification de la version du jeu de caractères du point d'entrée.  Pour plus d'informations sur la sélection d'un jeu de caractères, consultez [Spécification d'un jeu de caractères](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## Attribution d'un nouveau nom à une fonction dans C\# et C\+\+  
 Vous pouvez utiliser le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=fullName> pour spécifier une fonction DLL par son nom ou son ordinal.  Si le nom de la fonction figurant dans la définition de votre méthode est le même que celui du point d'entrée dans la DLL, vous n'avez alors pas à identifier explicitement la fonction avec le champ **EntryPoint**.  Sinon, utilisez l'une des formes d'attribut suivantes pour indiquer un nom ou un ordinal :  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 Notez que vous devez préfixer un ordinal avec le signe dièse \(\#\).  
  
 L'exemple suivant montre comment remplacer **MessageBoxA** par **MsgBox** dans votre code à l'aide du champ **EntryPoint**.  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md)   
 [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)