---
title: "Génération à partir de la ligne de commande (Visual Basic) | Documents Microsoft"
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
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
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
ms.openlocfilehash: e7550a4a54637ea5ef425a1cb7ae02abd07808a8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="26dc2-102">Génération à partir de la ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26dc2-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="26dc2-103">Un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet se compose d’un ou plusieurs fichiers source séparés.</span><span class="sxs-lookup"><span data-stu-id="26dc2-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project is made up of one or more separate source files.</span></span> <span data-ttu-id="26dc2-104">Pendant le processus appelé compilation, ces fichiers sont regroupés en un seul package, un seul fichier exécutable qui peut être exécuté en tant qu’application.</span><span class="sxs-lookup"><span data-stu-id="26dc2-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="26dc2-105">fournit un compilateur de ligne de commande comme alternative aux programmes de compilation dans le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="26dc2-105"> provides a command-line compiler as an alternative to compiling programs from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] integrated development environment (IDE).</span></span> <span data-ttu-id="26dc2-106">Le compilateur de ligne de commande est conçu pour les situations dans lesquelles vous nécessitent l’ensemble des fonctionnalités de l’IDE, par exemple, lorsque vous êtes à l’aide ou écriture pour les ordinateurs avec un espace mémoire ou stockage limitées sur le système.</span><span class="sxs-lookup"><span data-stu-id="26dc2-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
 <span data-ttu-id="26dc2-107">Lors de la compilation à partir de la ligne de commande, vous devez explicitement référencer Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bibliothèque d’exécution via la `/reference` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="26dc2-107">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
 <span data-ttu-id="26dc2-108">Pour compiler des fichiers sources à partir la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choisissez le **générer** commande à partir de la **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="26dc2-108">To compile source files from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="26dc2-109">Lorsque vous générez des fichiers de projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur les **vbc** commande et ses commutateurs dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="26dc2-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="26dc2-110">Pour afficher ces informations, ouvrez le [boîte de dialogue Options, projets et Solutions, générer et exécuter](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez la **niveau de détail de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de détail.</span><span class="sxs-lookup"><span data-stu-id="26dc2-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="26dc2-111">Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="26dc2-111">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="26dc2-112">Vous pouvez compiler des fichiers projet (.vbproj) à une invite de commandes à l’aide de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="26dc2-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="26dc2-113">Pour plus d’informations, consultez [référence de ligne de commande](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) et [procédure pas à pas : utilisation de MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span><span class="sxs-lookup"><span data-stu-id="26dc2-113">For more information, see [Command-Line Reference](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26dc2-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="26dc2-114">In This Section</span></span>  
 [<span data-ttu-id="26dc2-115">Guide pratique : appeler le compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="26dc2-115">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="26dc2-116">Décrit comment appeler le compilateur de ligne de commande à l’invite de commandes MS-DOS ou à partir d’un sous-répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="26dc2-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="26dc2-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="26dc2-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="26dc2-118">Fournit une liste d’exemples de lignes de commande que vous pouvez modifier pour votre usage personnel.</span><span class="sxs-lookup"><span data-stu-id="26dc2-118">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="26dc2-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="26dc2-119">Related Sections</span></span>  
 [<span data-ttu-id="26dc2-120">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26dc2-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="26dc2-121">Fournit des listes d’options du compilateur, organisées par ordre alphabétique ou par objet.</span><span class="sxs-lookup"><span data-stu-id="26dc2-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="26dc2-122">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="26dc2-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="26dc2-123">Décrit comment compiler des sections de code.</span><span class="sxs-lookup"><span data-stu-id="26dc2-123">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="26dc2-124">Génération et nettoyage de solutions et de projets dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26dc2-124">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="26dc2-125">Explique comment organiser ce qui figureront dans les différentes générations, choisir les propriétés du projet et vous assurer que les projets sont générés dans l’ordre correct.</span><span class="sxs-lookup"><span data-stu-id="26dc2-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
