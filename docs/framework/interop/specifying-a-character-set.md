---
title: "Specifying a Character Set | Microsoft Docs"
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
  - "platform invoke, attribute fields"
  - "attribute fields in platform invoke, CharSet"
  - "CharSet field"
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Specifying a Character Set
Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> contrôle le marshaling des chaînes et détermine comment l'appel de code non managé trouve des noms de fonction dans une DLL.  Cette rubrique décrit ces deux comportements.  
  
 Certaines interfaces API exportent deux versions de fonctions acceptant des arguments de chaîne : étroite \(ANSI\) et large \(Unicode\).  L'interface API Win32, par exemple, inclut les noms de point d'entrée suivants pour la fonction **MessageBox** :  
  
-   **MessageBoxA**  
  
     Fournit un formatage ANSI pour les caractères à 1 octet, caractérisé par un « A » ajouté au nom du point d'entrée.  Les appels vers **MessageBoxA** marshalent toujours les chaînes au format ANSI, comme cela est souvent le cas sur les plateformes Windows 95 et Windows 98.  
  
-   **MessageBoxW**  
  
     Fournit un formatage Unicode pour les caractères à 2 octets, caractérisé par un « W » ajouté au nom du point d'entrée.  Les appels vers **MessageBoxW** marshalent toujours les chaînes au format Unicode, comme cela est souvent le cas sur les plateformes Windows NT, Windows 2000 et Windows XP.  
  
## Marshaling de chaînes et correspondance de noms  
 Le champ **CharSet** accepte les valeurs suivantes :  
  
 **CharSet.Ansi** \(valeur par défaut\)  
  
-   Marshaling de chaînes  
  
     L'appel de code non managé marshale les chaînes de leur format managé \(Unicode\) en format ANSI.  
  
-   Correspondance de noms  
  
     Lorsque le champ <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=fullName> a la valeur **true**, comme cela est le cas par défaut en [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], l'appel de code non managé ne recherche que le nom que vous spécifiez.  Par exemple, si vous spécifiez **MessageBox**, l'appel de code non managé recherche **MessageBox** et il échoue lorsqu'il ne parvient pas à localiser le nom orthographié précisément de cette manière.  
  
     Lorsque le champ **ExactSpelling** a la valeur **false**, comme c'est le cas par défaut dans C\+\+ et C\#, l'appel de code non managé recherche en premier lieu l'alias non décomposé \(**MessageBox**\) et en second lieu le nom décomposé \(**MessageBoxA**\) si l'alias non décomposé reste introuvable.  Notez que le fonctionnement des recherches de correspondances de noms ANSI diffère du fonctionnement de la recherche de correspondance de noms Unicode.  
  
 **CharSet.Unicode**  
  
-   Marshaling de chaînes  
  
     L'appel de code non managé copie les chaînes de leur format managé \(Unicode\) en format Unicode.  
  
-   Correspondance de noms  
  
     Lorsque le champ **ExactSpelling** a la valeur **true**, comme cela est le cas par défaut en [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], l'appel de code non managé ne recherche que le nom que vous spécifiez.  Par exemple, si vous spécifiez **MessageBox**, l'appel de code non managé recherche **MessageBox** et il échoue lorsqu'il ne parvient pas à localiser le nom orthographié précisément de cette manière.  
  
     Lorsque le champ **ExactSpelling** a la valeur **false**, comme c'est le cas par défaut dans C\+\+ et C\#, l'appel de code non managé recherche alors en premier lieu le nom décomposé \(**MessageBoxW**\) et en second lieu l'alias non décomposé \(**MessageBox**\) si le nom décomposé reste introuvable.  Notez que le fonctionnement des recherches de correspondances de noms Unicode diffère du fonctionnement de la recherche de correspondances de noms ANSI.  
  
 **CharSet.Auto**  
  
-   L'appel de code non managé opte pour le format ANSI ou pour le format Unicode au moment de l'exécution, en fonction de la plateforme cible.  
  
## Spécification d'un jeu de caractères dans Visual Basic  
 L'exemple suivant montre comment déclarer la fonction **MessageBox** trois fois, à chaque fois avec un comportement de jeu de caractères différent.  Vous pouvez spécifier un comportement de jeu de caractères en Visual Basic en ajoutant le mot clé **Ansi**, **Unicode** ou **Auto** à l'instruction de déclaration.  
  
 Si vous n'indiquez pas le mot clé de jeu de caractères, comme dans la première instruction de déclaration, le jeu de caractères ANSI est affecté par défaut au champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName>.  La deuxième et la troisième instructions contenues dans l'exemple spécifient explicitement un jeu de caractères avec un mot clé.  
  
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
  
## Spécification d'un jeu de caractères dans C\# et C\+\+  
 Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> identifie le jeu de caractères sous\-jacent comme étant ANSI ou Unicode.  Le jeu de caractères contrôle le mode de marshaling des arguments de chaîne d'une méthode.  Utilisez l'une des formes suivantes pour indiquer le jeu de caractères :  
  
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
  
 L'exemple suivant illustre trois définitions managées de la fonction **MessageBox** attribuées pour spécifier un jeu de caractères.  En cas d'oubli dans la première définition, le jeu de caractères ANSI est alors affecté par défaut au champ **CharSet**.  
  
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
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md)   
 [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)