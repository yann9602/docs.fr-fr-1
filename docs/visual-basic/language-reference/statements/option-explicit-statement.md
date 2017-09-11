---
title: Option Explicit, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
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
ms.openlocfilehash: 4283599d9ed2ad9075ab0b2f404f1a12a31437ec
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="08822-102">Option Explicit, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08822-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="08822-103">Force la déclaration explicite de toutes les variables dans un fichier, ou permet les déclarations implicites de variables.</span><span class="sxs-lookup"><span data-stu-id="08822-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08822-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08822-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="08822-105">Composants</span><span class="sxs-lookup"><span data-stu-id="08822-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="08822-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="08822-106">Optional.</span></span> <span data-ttu-id="08822-107">Permet de `Option Explicit` la vérification.</span><span class="sxs-lookup"><span data-stu-id="08822-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="08822-108">Si `On` ou `Off` n’est pas spécifié, la valeur par défaut est `On`.</span><span class="sxs-lookup"><span data-stu-id="08822-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="08822-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="08822-109">Optional.</span></span> <span data-ttu-id="08822-110">Désactive `Option Explicit` la vérification.</span><span class="sxs-lookup"><span data-stu-id="08822-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08822-111">Notes</span><span class="sxs-lookup"><span data-stu-id="08822-111">Remarks</span></span>  
 <span data-ttu-id="08822-112">Lors de la `Option Explicit On` ou `Option Explicit` apparaît dans un fichier, vous devez déclarer explicitement toutes les variables à l’aide de la `Dim` ou `ReDim` instructions.</span><span class="sxs-lookup"><span data-stu-id="08822-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="08822-113">Si vous essayez d’utiliser un nom de variable non déclarée, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="08822-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="08822-114">La `Option Explicit Off` instruction permet une déclaration implicite des variables.</span><span class="sxs-lookup"><span data-stu-id="08822-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="08822-115">Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="08822-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08822-116">Paramètre `Option Explicit` à `Off` n’est généralement pas une bonne pratique.</span><span class="sxs-lookup"><span data-stu-id="08822-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="08822-117">Si vous orthographiez un nom de variable dans un ou plusieurs emplacements, ce qui entraînerait des résultats inattendus lorsque le programme est exécuté.</span><span class="sxs-lookup"><span data-stu-id="08822-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="08822-118">Lorsqu’une instruction Option Explicit n’est pas présente</span><span class="sxs-lookup"><span data-stu-id="08822-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="08822-119">Si le code source ne contient pas une `Option Explicit` instruction, le **Option Explicit** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="08822-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="08822-120">Si le compilateur de ligne de commande est utilisé, le [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) option du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="08822-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="08822-121">Pour définir Option Explicit dans l’IDE</span><span class="sxs-lookup"><span data-stu-id="08822-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="08822-122">Dans **l’Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="08822-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="08822-123">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="08822-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="08822-124">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="08822-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="08822-125">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="08822-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="08822-126">Définissez la valeur de la **Option Explicit** boîte.</span><span class="sxs-lookup"><span data-stu-id="08822-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="08822-127">Lorsque vous créez un nouveau projet, le **Option Explicit** définition sur le **compiler** onglet est définie sur le **Option Explicit** dans les **valeurs par défaut VB** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="08822-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="08822-128">Pour accéder à la **valeurs par défaut VB** boîte de dialogue le **outils** menu, cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="08822-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="08822-129">Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="08822-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="08822-130">Le paramètre par défaut initial dans **valeurs par défaut VB** est `On`.</span><span class="sxs-lookup"><span data-stu-id="08822-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="08822-131">Pour définir Option Explicit dans la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="08822-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="08822-132">Inclure les [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) option du compilateur dans le **vbc** commande.</span><span class="sxs-lookup"><span data-stu-id="08822-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08822-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="08822-133">Example</span></span>  
 <span data-ttu-id="08822-134">L’exemple suivant utilise la `Option Explicit` instruction pour forcer la déclaration explicite de toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="08822-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="08822-135">Essayez d’utiliser une variable non déclarée provoque une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="08822-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 <span data-ttu-id="08822-136">[!code-vb[VbVbalrStatements&#47;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="08822-136">[!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="08822-137">[!code-vb[VbVbalrStatements&#48;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="08822-137">[!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08822-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08822-138">See Also</span></span>  
 <span data-ttu-id="08822-139">[Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="08822-139">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="08822-140"> [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="08822-140"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="08822-141"> [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="08822-141"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="08822-142"> [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="08822-142"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="08822-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="08822-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="08822-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="08822-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="08822-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="08822-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="08822-146"> [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="08822-146"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
