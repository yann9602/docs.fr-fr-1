---
title: -warnaserror (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warnaserror
dev_langs:
- CSharp
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: df29fd760e0e4a002f1b5078d85370a74f322e23
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="warnaserror-c-compiler-options"></a><span data-ttu-id="9a995-102">/warnaserror (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9a995-102">/warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="9a995-103">L’option **/warnaserror+** considère tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9a995-103">The **/warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a995-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a995-104">Syntax</span></span>  
  
```console  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a995-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a995-105">Remarks</span></span>  
 <span data-ttu-id="9a995-106">Les messages qui d’ordinaire auraient été signalés comme des avertissements s’affichent en tant qu’erreurs, et le processus de génération est arrêté (aucun fichier de sortie n’est généré).</span><span class="sxs-lookup"><span data-stu-id="9a995-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="9a995-107">Comme **/warnaserror** est activé par défaut, les avertissements n’empêchent pas la génération d’un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9a995-107">By default, **/warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="9a995-108">Du fait de **/warnaserror**, qui est identique à **/warnaserror+**, les avertissements sont considérés comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9a995-108">**/warnaserror**, which is the same as **/warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="9a995-109">Le cas échéant, si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9a995-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="9a995-110">Utilisez [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) pour spécifier le niveau des avertissements que le compilateur doit afficher.</span><span class="sxs-lookup"><span data-stu-id="9a995-110">Use [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="9a995-111">Utilisez [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) pour désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="9a995-111">Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9a995-112">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a995-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="9a995-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="9a995-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="9a995-114">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="9a995-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="9a995-115">Modifiez la propriété **Considérer les avertissements comme des erreurs**.</span><span class="sxs-lookup"><span data-stu-id="9a995-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
     <span data-ttu-id="9a995-116">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a995-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a995-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a995-117">Example</span></span>  
 <span data-ttu-id="9a995-118">Compilez `in.cs` et faites en sorte que le compilateur n’affiche aucun avertissement :</span><span class="sxs-lookup"><span data-stu-id="9a995-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a995-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a995-119">See Also</span></span>  
 <span data-ttu-id="9a995-120">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a995-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="9a995-121">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="9a995-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

