---
title: "Spécification d'un jeu de caractères"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb2ae519b4a3d52c590f050ba728286898373ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-a-character-set"></a>Spécification d'un jeu de caractères
Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> contrôle le marshaling des chaînes et détermine de quelle façon l’appel de code non managé recherche des noms de fonction dans une DLL. Cette rubrique décrit ces deux comportements.  
  
 Certaines API exportent deux versions de fonctions qui acceptent des arguments de chaîne : caractères étroits (ANSI) et caractères larges (Unicode). L’API Win32, par exemple, inclut les noms de point d’entrée suivants pour la fonction **MessageBox** :  
  
-   **MessageBoxA**  
  
     Fournit un formatage ANSI pour les caractères sur un octet, caractérisé par l’ajout de la lettre A au nom du point d’entrée. Les appels à **MessageBoxA** marshalent toujours les chaînes au format ANSI, comme c’est généralement le cas sur les plateformes Windows 95 et Windows 98.  
  
-   **MessageBoxW**  
  
     Fournit un formatage Unicode pour les caractères sur deux octets, caractérisé par l’ajout de la lettre W au nom du point d’entrée. Les appels à **MessageBoxW** marshalent toujours les chaînes au format Unicode, comme c’est généralement le cas sur les plateformes Windows NT, Windows 2000 et Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Marshaling de chaînes et correspondance de noms  
 Le champ **CharSet** accepte les valeurs suivantes :  
  
 **CharSet.Ansi** (valeur par défaut)  
  
-   Marshaling de chaînes  
  
     L’appel de code non managé marshale les chaînes de leur format managé (Unicode) au format ANSI.  
  
-   Correspondance de noms  
  
     Quand le champ <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> a la valeur **true** (valeur par défaut dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]), l’appel de code non managé recherche uniquement le nom que vous spécifiez. Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.  
  
     Quand le champ **ExactSpelling** a la valeur **false** (valeur par défaut dans C++ et C#), l’appel de code non managé recherche d’abord l’alias non altéré (**MessageBox**), puis il recherche le nom altéré (**MessageBoxA**) si l’alias non altéré est introuvable. Notez que la correspondance de noms ANSI et la correspondance de noms Unicode n’ont pas le même comportement.  
  
 **CharSet.Unicode**  
  
-   Marshaling de chaînes  
  
     L’appel de code non managé copie les chaînes de leur format managé (Unicode) au format Unicode.  
  
-   Correspondance de noms  
  
     Quand le champ **ExactSpelling** a la valeur **true** (valeur par défaut dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]), l’appel de code non managé recherche uniquement le nom que vous spécifiez. Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.  
  
     Quand le champ **ExactSpelling** a la valeur **false** (valeur par défaut dans C++ et C#), l’appel de code non managé recherche d’abord le nom altéré (**MessageBoxW**), puis il recherche l’alias non altéré (**MessageBox**) si le nom altéré est introuvable. Notez que la correspondance de noms Unicode et la correspondance de noms ANSI n’ont pas le même comportement.  
  
 **CharSet.Auto**  
  
-   L’appel de code non managé choisit le format Unicode ou le format ANSI au moment de l’exécution, en fonction de la plateforme cible.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Spécification d’un jeu de caractères dans Visual Basic  
 L’exemple suivant déclare la fonction **MessageBox** trois fois, chaque fois avec un comportement de jeu de caractères différent. Vous pouvez spécifier le comportement de jeu de caractères dans Visual Basic en ajoutant le mot clé **Ansi**, **Unicode** ou **Auto** à l’instruction de déclaration.  
  
 Si vous omettez le mot clé de jeu de caractères, comme c’est le cas dans la première instruction de déclaration, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est par défaut défini sur le jeu de caractères ANSI. Dans l’exemple, la deuxième et la troisième instructions spécifient explicitement un jeu de caractères à l’aide d’un mot clé.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Spécification d’un jeu de caractères dans C# et C++  
 Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifie le jeu de caractères sous-jacent au format ANSI ou Unicode. Le jeu de caractères contrôle de quelle manière les arguments de chaîne d’une méthode doivent être marshalés. Spécifiez le jeu de caractères de l’une des manières suivantes :  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 L’exemple suivant montre trois définitions managées de la fonction **MessageBox** attribuées pour spécifier un jeu de caractères. Dans la première définition, du fait de son omission, le champ **CharSet** est par défaut défini sur le jeu de caractères ANSI.  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Exemples d'appel de code non managé](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling de données à l’aide de l’appel de code managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
