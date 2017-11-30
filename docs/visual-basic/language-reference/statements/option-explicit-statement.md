---
title: Option Explicit, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d39b3d7cf5096e3b263938d32e017eae5708e042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="f70b6-102">Option Explicit, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70b6-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="f70b6-103">Force la déclaration explicite de toutes les variables dans un fichier, ou permet les déclarations implicites de variables.</span><span class="sxs-lookup"><span data-stu-id="f70b6-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f70b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f70b6-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="f70b6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f70b6-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="f70b6-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f70b6-106">Optional.</span></span> <span data-ttu-id="f70b6-107">Permet de `Option Explicit` la vérification.</span><span class="sxs-lookup"><span data-stu-id="f70b6-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="f70b6-108">Si `On` ou `Off` n’est pas spécifié, la valeur par défaut est `On`.</span><span class="sxs-lookup"><span data-stu-id="f70b6-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="f70b6-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f70b6-109">Optional.</span></span> <span data-ttu-id="f70b6-110">Désactive `Option Explicit` la vérification.</span><span class="sxs-lookup"><span data-stu-id="f70b6-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f70b6-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f70b6-111">Remarks</span></span>  
 <span data-ttu-id="f70b6-112">Lorsque `Option Explicit On` ou `Option Explicit` apparaît dans un fichier, vous devez déclarer explicitement toutes les variables à l’aide de la `Dim` ou `ReDim` instructions.</span><span class="sxs-lookup"><span data-stu-id="f70b6-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="f70b6-113">Si vous essayez d’utiliser un nom de variable non déclarée, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f70b6-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="f70b6-114">La `Option Explicit Off` instruction permet une déclaration implicite des variables.</span><span class="sxs-lookup"><span data-stu-id="f70b6-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="f70b6-115">Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="f70b6-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f70b6-116">Paramètre `Option Explicit` à `Off` n’est généralement pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="f70b6-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="f70b6-117">Si vous orthographiez un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="f70b6-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="f70b6-118">Lorsqu’une instruction Option Explicit n’est pas présente</span><span class="sxs-lookup"><span data-stu-id="f70b6-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="f70b6-119">Si le code source ne contient pas un `Option Explicit` instruction, le **Option Explicit** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f70b6-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="f70b6-120">Si le compilateur de ligne de commande est utilisé, le [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) option du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f70b6-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="f70b6-121">Pour définir Option Explicit dans l’IDE</span><span class="sxs-lookup"><span data-stu-id="f70b6-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="f70b6-122">Dans l’**Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="f70b6-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="f70b6-123">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f70b6-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="f70b6-124">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="f70b6-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="f70b6-125">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="f70b6-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="f70b6-126">Définissez la valeur de la **Option Explicit** boîte.</span><span class="sxs-lookup"><span data-stu-id="f70b6-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="f70b6-127">Lorsque vous créez un nouveau projet, le **Option Explicit** définition sur le **compiler** onglet est définie sur le **Option Explicit** définition dans le **devaleurspardéfautVB**boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f70b6-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="f70b6-128">Pour accéder à la **valeurs par défaut VB** boîte de dialogue le **outils** menu, cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="f70b6-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="f70b6-129">Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="f70b6-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="f70b6-130">Le paramètre par défaut initial dans **valeurs par défaut VB** est `On`.</span><span class="sxs-lookup"><span data-stu-id="f70b6-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="f70b6-131">Pour définir Option Explicit sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="f70b6-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="f70b6-132">Inclure le [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) option du compilateur dans le **vbc** commande.</span><span class="sxs-lookup"><span data-stu-id="f70b6-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f70b6-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="f70b6-133">Example</span></span>  
 <span data-ttu-id="f70b6-134">L’exemple suivant utilise la `Option Explicit` instruction pour forcer la déclaration explicite de toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="f70b6-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="f70b6-135">Essayez d’utiliser une variable non déclarée de provoque une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f70b6-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f70b6-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f70b6-136">See Also</span></span>  
 [<span data-ttu-id="f70b6-137">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="f70b6-137">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="f70b6-138">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="f70b6-138">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="f70b6-139">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="f70b6-139">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="f70b6-140">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="f70b6-140">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="f70b6-141">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="f70b6-141">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="f70b6-142">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="f70b6-142">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="f70b6-143">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="f70b6-143">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="f70b6-144">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="f70b6-144">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
