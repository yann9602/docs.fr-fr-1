---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="c7bac-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="c7bac-102">/optionstrict</span></span>
<span data-ttu-id="c7bac-103">Applique une sémantique de type stricte pour restreindre les conversions de types implicites.</span><span class="sxs-lookup"><span data-stu-id="c7bac-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7bac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7bac-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7bac-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7bac-105">Arguments</span></span>  
 <span data-ttu-id="c7bac-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c7bac-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c7bac-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="c7bac-107">Optional.</span></span> <span data-ttu-id="c7bac-108">Le `/optionstrict+` option restreint les conversions de types implicites.</span><span class="sxs-lookup"><span data-stu-id="c7bac-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="c7bac-109">La valeur par défaut de cette option est `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="c7bac-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="c7bac-110">Le `/optionstrict+` option est identique à `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="c7bac-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="c7bac-111">Vous pouvez utiliser à la fois pour la sémantique de type permissive.</span><span class="sxs-lookup"><span data-stu-id="c7bac-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="c7bac-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c7bac-112">Required.</span></span> <span data-ttu-id="c7bac-113">Avertir lors de la syntaxe de langue stricte n’est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="c7bac-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7bac-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7bac-114">Remarks</span></span>  
 <span data-ttu-id="c7bac-115">Lorsque `/optionstrict+` est activée, seules les conversions étendues peuvent être effectuées implicitement.</span><span class="sxs-lookup"><span data-stu-id="c7bac-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="c7bac-116">Implicite conversions restrictives lors des conversions de types, tels que l’attribution un `Decimal` type d’objet à un objet de type entier, sont signalées comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="c7bac-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="c7bac-117">Pour générer des avertissements pour les conversions restrictives implicites, utilisez `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="c7bac-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="c7bac-118">Utilisez `/nowarn:numberlist` à ignorer certains avertissements et `/warnaserror:numberlist` à traiter certains avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="c7bac-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="c7bac-119">Pour définir /optionstrict dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7bac-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="c7bac-120">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="c7bac-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c7bac-121">Sur le **projet** menu, cliquez sur **propriétés.**</span><span class="sxs-lookup"><span data-stu-id="c7bac-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="c7bac-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="c7bac-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="c7bac-123">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="c7bac-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="c7bac-124">Modifiez la valeur dans la **Option Strict** boîte.</span><span class="sxs-lookup"><span data-stu-id="c7bac-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="c7bac-125">Pour définir /optionstrict par programme</span><span class="sxs-lookup"><span data-stu-id="c7bac-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="c7bac-126">Consultez [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c7bac-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7bac-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7bac-127">Example</span></span>  
 <span data-ttu-id="c7bac-128">Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.</span><span class="sxs-lookup"><span data-stu-id="c7bac-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7bac-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7bac-129">See Also</span></span>  
 [<span data-ttu-id="c7bac-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7bac-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c7bac-131">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="c7bac-131">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="c7bac-132">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c7bac-132">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="c7bac-133">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="c7bac-133">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="c7bac-134">/nowarn</span><span class="sxs-lookup"><span data-stu-id="c7bac-134">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="c7bac-135">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7bac-135">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="c7bac-136">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="c7bac-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="c7bac-137">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7bac-137">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="c7bac-138">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="c7bac-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
