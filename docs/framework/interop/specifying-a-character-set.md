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
ms.openlocfilehash: 3e97c640472156c1a47ad125bffeaf39b8eb0762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="02ca2-102">Spécification d'un jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="02ca2-102">Specifying a Character Set</span></span>
<span data-ttu-id="02ca2-103">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> contrôle le marshaling des chaînes et détermine de quelle façon l’appel de code non managé recherche des noms de fonction dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="02ca2-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="02ca2-104">Cette rubrique décrit ces deux comportements.</span><span class="sxs-lookup"><span data-stu-id="02ca2-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="02ca2-105">Certaines API exportent deux versions de fonctions qui acceptent des arguments de chaîne : caractères étroits (ANSI) et caractères larges (Unicode).</span><span class="sxs-lookup"><span data-stu-id="02ca2-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="02ca2-106">L’API Win32, par exemple, inclut les noms de point d’entrée suivants pour la fonction **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="02ca2-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="02ca2-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="02ca2-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="02ca2-108">Fournit un formatage ANSI pour les caractères sur un octet, caractérisé par l’ajout de la lettre A au nom du point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="02ca2-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="02ca2-109">Les appels à **MessageBoxA** marshalent toujours les chaînes au format ANSI, comme c’est généralement le cas sur les plateformes Windows 95 et Windows 98.</span><span class="sxs-lookup"><span data-stu-id="02ca2-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="02ca2-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="02ca2-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="02ca2-111">Fournit un formatage Unicode pour les caractères sur deux octets, caractérisé par l’ajout de la lettre W au nom du point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="02ca2-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="02ca2-112">Les appels à **MessageBoxW** marshalent toujours les chaînes au format Unicode, comme c’est généralement le cas sur les plateformes Windows NT, Windows 2000 et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="02ca2-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="02ca2-113">Marshaling de chaînes et correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="02ca2-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="02ca2-114">Le champ **CharSet** accepte les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="02ca2-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="02ca2-115">**CharSet.Ansi** (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="02ca2-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="02ca2-116">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="02ca2-116">String marshaling</span></span>  
  
     <span data-ttu-id="02ca2-117">L’appel de code non managé marshale les chaînes de leur format managé (Unicode) au format ANSI.</span><span class="sxs-lookup"><span data-stu-id="02ca2-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="02ca2-118">Correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="02ca2-118">Name matching</span></span>  
  
     <span data-ttu-id="02ca2-119">Quand le champ <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> a la valeur **true** (valeur par défaut dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]), l’appel de code non managé recherche uniquement le nom que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="02ca2-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="02ca2-120">Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.</span><span class="sxs-lookup"><span data-stu-id="02ca2-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="02ca2-121">Quand le champ **ExactSpelling** a la valeur **false** (valeur par défaut dans C++ et C#), l’appel de code non managé recherche d’abord l’alias non altéré (**MessageBox**), puis il recherche le nom altéré (**MessageBoxA**) si l’alias non altéré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="02ca2-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="02ca2-122">Notez que la correspondance de noms ANSI et la correspondance de noms Unicode n’ont pas le même comportement.</span><span class="sxs-lookup"><span data-stu-id="02ca2-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="02ca2-123">**CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="02ca2-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="02ca2-124">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="02ca2-124">String marshaling</span></span>  
  
     <span data-ttu-id="02ca2-125">L’appel de code non managé copie les chaînes de leur format managé (Unicode) au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="02ca2-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="02ca2-126">Correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="02ca2-126">Name matching</span></span>  
  
     <span data-ttu-id="02ca2-127">Quand le champ **ExactSpelling** a la valeur **true** (valeur par défaut dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]), l’appel de code non managé recherche uniquement le nom que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="02ca2-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="02ca2-128">Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.</span><span class="sxs-lookup"><span data-stu-id="02ca2-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="02ca2-129">Quand le champ **ExactSpelling** a la valeur **false** (valeur par défaut dans C++ et C#), l’appel de code non managé recherche d’abord le nom altéré (**MessageBoxW**), puis il recherche l’alias non altéré (**MessageBox**) si le nom altéré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="02ca2-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="02ca2-130">Notez que la correspondance de noms Unicode et la correspondance de noms ANSI n’ont pas le même comportement.</span><span class="sxs-lookup"><span data-stu-id="02ca2-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="02ca2-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="02ca2-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="02ca2-132">L’appel de code non managé choisit le format Unicode ou le format ANSI au moment de l’exécution, en fonction de la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="02ca2-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="02ca2-133">Spécification d’un jeu de caractères dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02ca2-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="02ca2-134">L’exemple suivant déclare la fonction **MessageBox** trois fois, chaque fois avec un comportement de jeu de caractères différent.</span><span class="sxs-lookup"><span data-stu-id="02ca2-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="02ca2-135">Vous pouvez spécifier le comportement de jeu de caractères dans Visual Basic en ajoutant le mot clé **Ansi**, **Unicode** ou **Auto** à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="02ca2-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="02ca2-136">Si vous omettez le mot clé de jeu de caractères, comme c’est le cas dans la première instruction de déclaration, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est par défaut défini sur le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="02ca2-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="02ca2-137">Dans l’exemple, la deuxième et la troisième instructions spécifient explicitement un jeu de caractères à l’aide d’un mot clé.</span><span class="sxs-lookup"><span data-stu-id="02ca2-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="02ca2-138">Spécification d’un jeu de caractères dans C# et C++</span><span class="sxs-lookup"><span data-stu-id="02ca2-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="02ca2-139">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifie le jeu de caractères sous-jacent au format ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="02ca2-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="02ca2-140">Le jeu de caractères contrôle de quelle manière les arguments de chaîne d’une méthode doivent être marshalés.</span><span class="sxs-lookup"><span data-stu-id="02ca2-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="02ca2-141">Spécifiez le jeu de caractères de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="02ca2-141">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="02ca2-142">L’exemple suivant montre trois définitions managées de la fonction **MessageBox** attribuées pour spécifier un jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="02ca2-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="02ca2-143">Dans la première définition, du fait de son omission, le champ **CharSet** est par défaut défini sur le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="02ca2-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02ca2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ca2-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="02ca2-145">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="02ca2-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="02ca2-146">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="02ca2-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="02ca2-147">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="02ca2-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
