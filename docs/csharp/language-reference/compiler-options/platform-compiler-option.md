---
title: -platform (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d03e12ae60b9a0145dcb58765ae00f756f84ca56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="platform-c-compiler-options"></a><span data-ttu-id="d85de-102">/platform (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="d85de-102">/platform (C# Compiler Options)</span></span>
<span data-ttu-id="d85de-103">Spécifie la version du CLR (Common Language Runtime) qui peut exécuter l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d85de-103">Specifies which version of the common language runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d85de-104">Syntax</span></span>  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d85de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d85de-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="d85de-106">anycpu (valeur par défaut), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.</span><span class="sxs-lookup"><span data-stu-id="d85de-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85de-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d85de-107">Remarks</span></span>  
  
-   <span data-ttu-id="d85de-108">**anycpu** (valeur par défaut) compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="d85de-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d85de-109">Votre application s’exécute en tant que processus 64 bits dans la mesure du possible et repasse en 32 bits quand seul ce mode est disponible.</span><span class="sxs-lookup"><span data-stu-id="d85de-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="d85de-110">**anycpu32bitpreferred** compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="d85de-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d85de-111">Votre application s’exécute en mode 32 bits sur les systèmes qui prennent en charge les applications 64 bits et 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d85de-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="d85de-112">Vous pouvez spécifier cette option uniquement pour les projets qui ciblent le .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d85de-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="d85de-113">**ARM** compile votre assembly pour qu’il s’exécute sur un ordinateur doté d’un processeur ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="d85de-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="d85de-114">**x64** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d’instructions AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="d85de-114">**x64** compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="d85de-115">**x86** compile votre assembly pour qu’il soit exécuté par le CLR 32 bits x86.</span><span class="sxs-lookup"><span data-stu-id="d85de-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible common language runtime.</span></span>  
  
-   <span data-ttu-id="d85de-116">**Itanium** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur doté d’un processeur Itanium.</span><span class="sxs-lookup"><span data-stu-id="d85de-116">**Itanium** compiles your assembly to be run by the 64-bit common language runtime on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="d85de-117">Sur un système d'exploitation Windows 64 bits :</span><span class="sxs-lookup"><span data-stu-id="d85de-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="d85de-118">Les assemblys compilés avec **/platform:x86** s’exécutent sur le CLR 32 bits fonctionnant sous WOW64.</span><span class="sxs-lookup"><span data-stu-id="d85de-118">Assemblies compiled with **/platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="d85de-119">Une DLL compilée avec **/platform:anycpu** s’exécute sur le même CLR que le processus dans lequel elle est chargée.</span><span class="sxs-lookup"><span data-stu-id="d85de-119">A DLL compiled with the **/platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="d85de-120">Les fichiers exécutables compilés avec **/platform:anycpu** s’exécutent sur le CLR 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d85de-120">Executables that are compiled with the **/platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="d85de-121">Les fichiers exécutables compilés avec **/platform:anycpu32bitpreferred** s’exécutent sur le CLR 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d85de-121">Executables compiled with **/platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="d85de-122">Le paramètre **anycpu32bitpreferred** ne vaut que pour les fichiers exécutables (.EXE) et nécessite le .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d85de-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="d85de-123">Pour plus d’informations sur le développement d’une application s’exécutant sur un système d’exploitation Windows 64 bits, consultez [Applications 64 bits](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d85de-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d85de-124">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d85de-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d85de-125">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="d85de-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="d85de-126">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="d85de-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d85de-127">Modifiez la propriété **Plateforme cible** puis, pour les projets qui ciblent le .NET Framework 4.5, cochez ou décochez la case **Préférer 32 bits**.</span><span class="sxs-lookup"><span data-stu-id="d85de-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="d85de-128">**Notez que /platform** n’est pas disponible dans l’environnement de développement de Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="d85de-128">**Note /platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="d85de-129">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="d85de-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d85de-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d85de-130">Example</span></span>  
 <span data-ttu-id="d85de-131">L’exemple suivant montre comment utiliser l’option **/platform** pour préciser que l’application doit être exécutée par le CLR 64 bits sur un système d’exploitation Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d85de-131">The following example shows how to use the **/platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d85de-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d85de-132">See Also</span></span>  
 [<span data-ttu-id="d85de-133">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="d85de-133">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="d85de-134">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="d85de-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
