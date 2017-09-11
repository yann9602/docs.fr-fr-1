---
title: Options du compilateur C#
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.options
dev_langs:
- CSharp
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 02cfb7708959057de593506db55e4f31f5ab4fd0
ms.openlocfilehash: 7c5f5274a5685e50fb7f1d06771b0340200d1c3f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="c-compiler-options"></a><span data-ttu-id="a81f0-102">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="a81f0-102">C# Compiler Options</span></span>
<span data-ttu-id="a81f0-103">Le compilateur produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="a81f0-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="a81f0-104">Chaque option du compilateur est disponible sous deux formes : **-option** et **/option**.</span><span class="sxs-lookup"><span data-stu-id="a81f0-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="a81f0-105">La documentation ne présente que la forme **/option**.</span><span class="sxs-lookup"><span data-stu-id="a81f0-105">The documentation only shows the **/option** form.</span></span>  
  
 <span data-ttu-id="a81f0-106">Dans Visual Web Developer 2008, vous définissez les options du compilateur dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="a81f0-106">In Visual Web Developer 2008, you set compiler options in the web.config file.</span></span> <span data-ttu-id="a81f0-107">Pour plus d’informations, consultez [\<compilateur> Élément](https://msdn.microsoft.com/library/y9x69bzw).</span><span class="sxs-lookup"><span data-stu-id="a81f0-107">For more information, see [\<compiler> Element](https://msdn.microsoft.com/library/y9x69bzw).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a81f0-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a81f0-108">In This Section</span></span>  
 [<span data-ttu-id="a81f0-109">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="a81f0-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="a81f0-110">Informations sur la création d’une application Visual C# à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a81f0-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="a81f0-111">Comment : définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a81f0-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="a81f0-112">Explique comment exécuter vsvars32.bat pour permettre les générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a81f0-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="a81f0-113">Options du compilateur C# par catégorie</span><span class="sxs-lookup"><span data-stu-id="a81f0-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="a81f0-114">Liste par catégorie des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a81f0-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="a81f0-115">Options du compilateur C# par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="a81f0-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="a81f0-116">Liste alphabétique des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a81f0-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a81f0-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a81f0-117">Related Sections</span></span>  
 [<span data-ttu-id="a81f0-118">Page Générer, Concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="a81f0-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="a81f0-119">Définition des propriétés qui régissent la façon dont votre projet est compilé, généré et débogué.</span><span class="sxs-lookup"><span data-stu-id="a81f0-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="a81f0-120">Contient des informations sur les étapes de génération personnalisée dans les projets Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a81f0-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="a81f0-121">Générations personnalisées et par défaut</span><span class="sxs-lookup"><span data-stu-id="a81f0-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="a81f0-122">Informations sur les configurations et les types de génération.</span><span class="sxs-lookup"><span data-stu-id="a81f0-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="a81f0-123">Préparation et gestion des générations</span><span class="sxs-lookup"><span data-stu-id="a81f0-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="a81f0-124">Procédures de génération dans l’environnement de développement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a81f0-124">Procedures for building within the Visual Studio development environment.</span></span>

