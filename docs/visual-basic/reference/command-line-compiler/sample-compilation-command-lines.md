---
title: Exemples de lignes de commande de Compilation (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e58006c05f498ec1a9dbf5194fbc9bcdd281ab63
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="6be99-102">Exemples de lignes de commande de compilation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6be99-102">Sample Compilation Command Lines (Visual Basic)</span></span>
<span data-ttu-id="6be99-103">Comme alternative à la compilation de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programmes depuis [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], vous pouvez les compiler depuis la ligne de commande pour produire des fichiers exécutables (.exe) ou des fichiers de bibliothèque de liens dynamiques (.dll).</span><span class="sxs-lookup"><span data-stu-id="6be99-103">As an alternative to compiling [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs from within [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="6be99-104">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur de ligne de commande prend en charge un ensemble complet d’options qui contrôlent les fichiers d’entrée et de sortie, assemblys et de débogage et les options de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="6be99-104">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="6be99-105">Chaque option est disponible sous deux formes interchangeables : `-``option` et `/``option`.</span><span class="sxs-lookup"><span data-stu-id="6be99-105">Each option is available in two interchangeable forms: `-``option` and `/``option`.</span></span> <span data-ttu-id="6be99-106">Cette documentation ne décrit que le `/``option` formulaire.</span><span class="sxs-lookup"><span data-stu-id="6be99-106">This documentation shows only the `/``option` form.</span></span>  
  
 <span data-ttu-id="6be99-107">Le tableau suivant répertorie certains exemples de ligne de commande que vous pouvez modifier pour votre usage personnel.</span><span class="sxs-lookup"><span data-stu-id="6be99-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="6be99-108">Pour</span><span class="sxs-lookup"><span data-stu-id="6be99-108">To</span></span>|<span data-ttu-id="6be99-109">Utilisez</span><span class="sxs-lookup"><span data-stu-id="6be99-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="6be99-110">Compiler File.vb et créer File.exe</span><span class="sxs-lookup"><span data-stu-id="6be99-110">Compile File.vb and create File.exe</span></span>|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="6be99-111">Compiler File.vb et créer File.dll</span><span class="sxs-lookup"><span data-stu-id="6be99-111">Compile File.vb and create File.dll</span></span>|`vbc /target:library File.vb`|  
|<span data-ttu-id="6be99-112">Compiler File.vb et créer My.exe</span><span class="sxs-lookup"><span data-stu-id="6be99-112">Compile File.vb and create My.exe</span></span>|`vbc /out:My.exe File.vb`|  
|<span data-ttu-id="6be99-113">Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sur les fichiers dans le répertoire actif, avec les optimisations et `DEBUG` symbole est défini, afin de produire File2.exe</span><span class="sxs-lookup"><span data-stu-id="6be99-113">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|<span data-ttu-id="6be99-114">Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les fichiers dans le répertoire en cours, en produisant une version debug de File2.dll sans afficher le logo ou les avertissements</span><span class="sxs-lookup"><span data-stu-id="6be99-114">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|<span data-ttu-id="6be99-115">Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fichiers dans le répertoire en cours en Something.dll</span><span class="sxs-lookup"><span data-stu-id="6be99-115">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory to Something.dll</span></span>|`vbc /target:library /out:Something.dll *.vb`|  
  
 <span data-ttu-id="6be99-116">Lors de la compilation à partir de la ligne de commande, vous devez explicitement référencer Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bibliothèque d’exécution via la `/reference` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="6be99-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="6be99-117">Lorsque vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur les **vbc** commande avec les options du compilateur dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="6be99-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="6be99-118">Pour afficher ces informations, ouvrez le [boîte de dialogue Options, projets et Solutions, générer et exécuter](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez la **niveau de détail de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de détail.</span><span class="sxs-lookup"><span data-stu-id="6be99-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="6be99-119">Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="6be99-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be99-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6be99-120">See Also</span></span>  
 <span data-ttu-id="6be99-121">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6be99-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6be99-122"> [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span><span class="sxs-lookup"><span data-stu-id="6be99-122"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span></span>
