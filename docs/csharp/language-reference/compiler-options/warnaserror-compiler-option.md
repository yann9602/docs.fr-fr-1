---
title: -warnaserror (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a341fe9760d7fdb0e4df7046cf356e550b4adb9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="6f10b-102">-warnaserror (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="6f10b-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="6f10b-103">L’option **-warnaserror+** considère tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f10b-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f10b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f10b-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6f10b-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6f10b-105">Remarks</span></span>  
 <span data-ttu-id="6f10b-106">Les messages qui d’ordinaire auraient été signalés comme des avertissements s’affichent en tant qu’erreurs, et le processus de génération est arrêté (aucun fichier de sortie n’est généré).</span><span class="sxs-lookup"><span data-stu-id="6f10b-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="6f10b-107">Comme **-warnaserror** est activé par défaut, les avertissements n’empêchent pas la génération d’un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="6f10b-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="6f10b-108">Du fait de **-warnaserror**, qui est identique à **-warnaserror+**, les avertissements sont considérés comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f10b-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="6f10b-109">Le cas échéant, si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f10b-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="6f10b-110">Utilisez [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) pour spécifier le niveau des avertissements que le compilateur doit afficher.</span><span class="sxs-lookup"><span data-stu-id="6f10b-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="6f10b-111">Utilisez [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) pour désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="6f10b-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6f10b-112">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f10b-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6f10b-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="6f10b-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="6f10b-114">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="6f10b-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6f10b-115">Modifiez la propriété **Considérer les avertissements comme des erreurs**.</span><span class="sxs-lookup"><span data-stu-id="6f10b-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="6f10b-116">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="6f10b-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f10b-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f10b-117">Example</span></span>  
 <span data-ttu-id="6f10b-118">Compilez `in.cs` et faites en sorte que le compilateur n’affiche aucun avertissement :</span><span class="sxs-lookup"><span data-stu-id="6f10b-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f10b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f10b-119">See Also</span></span>  
 [<span data-ttu-id="6f10b-120">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="6f10b-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6f10b-121">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="6f10b-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
