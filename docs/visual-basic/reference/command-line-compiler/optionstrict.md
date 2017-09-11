---
title: /optionstrict | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c22445cb53ca4f5621cf7aa69ab840b26f8e08c9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="optionstrict"></a><span data-ttu-id="8ca17-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="8ca17-102">/optionstrict</span></span>
<span data-ttu-id="8ca17-103">Applique une sémantique de type stricte pour restreindre les conversions de type implicite.</span><span class="sxs-lookup"><span data-stu-id="8ca17-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ca17-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ca17-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8ca17-105">Arguments</span></span>  
 <span data-ttu-id="8ca17-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8ca17-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8ca17-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ca17-107">Optional.</span></span> <span data-ttu-id="8ca17-108">La `/optionstrict+` option restreint les conversions de type implicite.</span><span class="sxs-lookup"><span data-stu-id="8ca17-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="8ca17-109">La valeur par défaut pour cette option est `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="8ca17-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="8ca17-110">Le `/optionstrict+` option est identique à `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="8ca17-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="8ca17-111">Vous pouvez utiliser les deux pour la sémantique de type permissive.</span><span class="sxs-lookup"><span data-stu-id="8ca17-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="8ca17-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ca17-112">Required.</span></span> <span data-ttu-id="8ca17-113">Avertir lorsque la syntaxe de langue stricte n'est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="8ca17-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca17-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ca17-114">Remarks</span></span>  
 <span data-ttu-id="8ca17-115">Lorsque `/optionstrict+` est activée, seules les conversions étendues peuvent être effectuées implicitement.</span><span class="sxs-lookup"><span data-stu-id="8ca17-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="8ca17-116">Conversions, tels que l’attribution restrictives implicites un `Decimal` type d’objet à un objet de type entier, sont signalées comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8ca17-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="8ca17-117">Pour générer des avertissements pour les conversions restrictives implicites, utilisez `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="8ca17-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="8ca17-118">Utilisez `/nowarn:numberlist` pour ignorer certains avertissements et `/warnaserror:numberlist` à traiter certains avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8ca17-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="8ca17-119">Pour définir /optionstrict dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ca17-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="8ca17-120">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="8ca17-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8ca17-121">Sur le **projet** menu, cliquez sur **propriétés.**</span><span class="sxs-lookup"><span data-stu-id="8ca17-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="8ca17-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="8ca17-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="8ca17-123">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="8ca17-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="8ca17-124">Modifiez la valeur dans la **Option Strict** boîte.</span><span class="sxs-lookup"><span data-stu-id="8ca17-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="8ca17-125">Pour définir /optionstrict par programme</span><span class="sxs-lookup"><span data-stu-id="8ca17-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="8ca17-126">Consultez la page [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ca17-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca17-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ca17-127">Example</span></span>  
 <span data-ttu-id="8ca17-128">Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.</span><span class="sxs-lookup"><span data-stu-id="8ca17-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ca17-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ca17-129">See Also</span></span>  
 <span data-ttu-id="8ca17-130">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8ca17-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="8ca17-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="8ca17-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="8ca17-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span></span>  
<span data-ttu-id="8ca17-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span></span>  
<span data-ttu-id="8ca17-136"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-136"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="8ca17-137"> [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8ca17-137"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="8ca17-138"> [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="8ca17-138"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
