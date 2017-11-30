---
title: "Spécification d'un point d'entrée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7406e256acaea0c535c222386c529c4087bbdc6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-entry-point"></a>Spécification d'un point d'entrée
Un point d’entrée identifie l’emplacement d’une fonction dans une DLL. Dans un projet managé, le nom d’origine ou le point d’entrée ordinal d’une fonction cible identifie cette fonction dans les limites d’interopérabilité. De plus, vous pouvez mapper le point d’entrée à un autre nom pour renommer la fonction de façon plus appropriée.  
  
 Voici une liste de raisons possibles pour renommer une fonction DLL :  
  
-   Éviter d’utiliser des noms de fonction API respectant la casse.  
  
-   Utiliser un nom respectant les conventions de nommage actuelles.  
  
-   Prendre en charge les fonctions qui acceptent différents types de données (en déclarant plusieurs versions de la même fonction DLL).  
  
-   Simplifier l’utilisation des API qui contiennent des versions ANSI et Unicode.  
  
 Cette rubrique montre comment renommer une fonction DLL dans du code managé.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Renommer une fonction dans Visual Basic  
 Visual Basic utilise le mot clé **Function** dans l’instruction **Declare** pour définir le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>. L’exemple suivant illustre une déclaration simple.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 Vous pouvez remplacer le point d’entrée **MessageBox** par **MsgBox** en incluant le mot clé **Alias** dans votre définition, comme dans l’exemple suivant. Dans les deux exemples, le mot clé **Auto** vous évite de devoir spécifier la version du jeu de caractères pour le point d’entrée. Pour plus d’informations sur la sélection d’un jeu de caractères, consultez [Spécification d’un jeu de caractères](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a>Renommer une fonction dans C# et C++  
 Vous pouvez utiliser le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pour spécifier une fonction DLL à l’aide d’un nom ou d’un ordinal. Si le nom de la fonction dans votre définition de méthode est le même que le point d’entrée dans la DLL, vous n’avez pas besoin d’identifier explicitement la fonction à l’aide du champ **EntryPoint**. Sinon, utilisez l’une des formes d’attribut suivantes pour spécifier un nom ou un ordinal :  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 Notez que vous devez ajouter le préfixe # (signe dièse) à un ordinal.  
  
 L’exemple suivant montre comment remplacer **MessageBoxA** par **MsgBox** dans votre code à l’aide du champ **EntryPoint**.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Exemples d'appel de code non managé](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling de données à l’aide de l’appel de code managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
