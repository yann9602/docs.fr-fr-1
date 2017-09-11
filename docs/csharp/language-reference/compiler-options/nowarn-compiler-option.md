---
title: -nowarn (options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
dev_langs:
- CSharp
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
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
ms.openlocfilehash: 3bae7e6d16c044b8f1aeba26de434cdf17479e82
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nowarn-c-compiler-options"></a><span data-ttu-id="e24ec-102">/nowarn (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e24ec-102">/nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="e24ec-103">L’option **/nowarn** vous permet de désactiver l’affichage d’un ou de plusieurs avertissements par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e24ec-103">The **/nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="e24ec-104">Séparez les numéros des avertissements par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e24ec-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24ec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24ec-105">Syntax</span></span>  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e24ec-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e24ec-106">Arguments</span></span>  
 <span data-ttu-id="e24ec-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="e24ec-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="e24ec-108">Numéro de chaque avertissement que le compilateur ne doit pas afficher.</span><span class="sxs-lookup"><span data-stu-id="e24ec-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e24ec-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e24ec-109">Remarks</span></span>  
 <span data-ttu-id="e24ec-110">Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e24ec-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="e24ec-111">Par exemple, si vous souhaitez supprimer l’avertissement CS0028, spécifiez `/nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="e24ec-111">For example, if you want to suppress CS0028, you could specify `/nowarn:28`.</span></span>  
  
 <span data-ttu-id="e24ec-112">Le compilateur ignore automatiquement les numéros des avertissements passés à `/nowarn` qui étaient valides dans les versions précédentes, mais qui ont été supprimés dans le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e24ec-112">The compiler will silently ignore warning numbers passed to `/nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="e24ec-113">Par exemple, l’avertissement CS0679 était valide dans le compilateur dans Visual Studio .NET 2002, mais il a été supprimé depuis cette version.</span><span class="sxs-lookup"><span data-stu-id="e24ec-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="e24ec-114">Les avertissements suivants ne peuvent pas être supprimés avec l’option `/nowarn` :</span><span class="sxs-lookup"><span data-stu-id="e24ec-114">The following warnings cannot be suppressed by the `/nowarn` option:</span></span>  
  
-   <span data-ttu-id="e24ec-115">Avertissement du compilateur (niveau 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="e24ec-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="e24ec-116">Avertissement du compilateur (niveau 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="e24ec-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="e24ec-117">Avertissement du compilateur (niveau 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="e24ec-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e24ec-118">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e24ec-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e24ec-119">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="e24ec-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="e24ec-120">Pour plus de détails, consultez [Générer, page du Concepteur de projet (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="e24ec-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="e24ec-121">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="e24ec-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="e24ec-122">Modifiez la propriété **Supprimer les avertissements**.</span><span class="sxs-lookup"><span data-stu-id="e24ec-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="e24ec-123">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="e24ec-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24ec-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e24ec-124">See Also</span></span>  
 <span data-ttu-id="e24ec-125">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="e24ec-125">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="e24ec-126">[Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties) </span><span class="sxs-lookup"><span data-stu-id="e24ec-126">[Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties) </span></span>  
 [<span data-ttu-id="e24ec-127">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e24ec-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)

