---
title: Instruction Option Infer | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement
- Infer keyword
- declaring variables, inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
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
ms.openlocfilehash: 56c2813f0fcfc23c4eb4039ffbbb1d9deeccb72c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="option-infer-statement"></a><span data-ttu-id="34007-102">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="34007-102">Option Infer Statement</span></span>
<span data-ttu-id="34007-103">Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.</span><span class="sxs-lookup"><span data-stu-id="34007-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34007-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34007-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="34007-105">Composants</span><span class="sxs-lookup"><span data-stu-id="34007-105">Parts</span></span>  
  
|<span data-ttu-id="34007-106">Terme</span><span class="sxs-lookup"><span data-stu-id="34007-106">Term</span></span>|<span data-ttu-id="34007-107">Définition</span><span class="sxs-lookup"><span data-stu-id="34007-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="34007-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="34007-108">Optional.</span></span> <span data-ttu-id="34007-109">Active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="34007-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="34007-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="34007-110">Optional.</span></span> <span data-ttu-id="34007-111">Désactive l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="34007-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34007-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="34007-112">Remarks</span></span>  
 <span data-ttu-id="34007-113">Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source.</span><span class="sxs-lookup"><span data-stu-id="34007-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="34007-114">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="34007-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="34007-115">Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données.</span><span class="sxs-lookup"><span data-stu-id="34007-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="34007-116">Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="34007-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="34007-117">Dans l'illustration suivante, `Option Infer` est activé.</span><span class="sxs-lookup"><span data-stu-id="34007-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="34007-118">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="34007-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="34007-119">![Vue IntelliSense de la déclaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="34007-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="34007-120">IntelliSense quand Option Infer est activé</span><span class="sxs-lookup"><span data-stu-id="34007-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="34007-121">Dans l'illustration suivante, `Option Infer` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="34007-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="34007-122">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="34007-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="34007-123">Dans cet exemple, le **Option Strict** est défini sur **hors** sur la [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="34007-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="34007-124">![Vue IntelliSense de la déclaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="34007-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="34007-125">IntelliSense quand Option Infer est désactivé</span><span class="sxs-lookup"><span data-stu-id="34007-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34007-126">Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute.</span><span class="sxs-lookup"><span data-stu-id="34007-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="34007-127">exécute des opérations appelées *boxing* et *unboxing* pour effectuer une conversion entre un `Object` et un type valeur, ce qui ralentit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="34007-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="34007-128">Pour plus d’informations sur les conversions boxing et unboxing, consultez le [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification.md).</span><span class="sxs-lookup"><span data-stu-id="34007-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
 <span data-ttu-id="34007-129">L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.</span><span class="sxs-lookup"><span data-stu-id="34007-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="34007-130">Pour plus d’informations, consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="34007-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="34007-131">En l'absence d'instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="34007-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="34007-132">Si le code source ne contient pas une `Option Infer` instruction, le **Option Infer** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="34007-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="34007-133">Si le compilateur de ligne de commande est utilisé, le [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="34007-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="34007-134">Pour définir Option Infer dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="34007-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="34007-135">Dans **l’Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="34007-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="34007-136">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="34007-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="34007-137">Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="34007-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="34007-138">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="34007-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="34007-139">Définissez la valeur de la **Option infer** boîte.</span><span class="sxs-lookup"><span data-stu-id="34007-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="34007-140">Lorsque vous créez un nouveau projet, le **Option Infer** définition sur le **compiler** onglet est définie sur le **Option Infer** dans les **valeurs par défaut VB** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="34007-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="34007-141">Pour accéder à la **valeurs par défaut VB** boîte de dialogue le **outils** menu, cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="34007-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="34007-142">Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="34007-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="34007-143">Le paramètre par défaut initial dans **valeurs par défaut VB** est `On`.</span><span class="sxs-lookup"><span data-stu-id="34007-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="34007-144">Pour définir Option Infer sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="34007-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="34007-145">Inclure les [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur dans le **vbc** commande.</span><span class="sxs-lookup"><span data-stu-id="34007-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="34007-146">Types de données et valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="34007-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="34007-147">Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="34007-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="34007-148">Type de données spécifié ?</span><span class="sxs-lookup"><span data-stu-id="34007-148">Data type specified?</span></span>|<span data-ttu-id="34007-149">Initialiseur spécifié ?</span><span class="sxs-lookup"><span data-stu-id="34007-149">Initializer specified?</span></span>|<span data-ttu-id="34007-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="34007-150">Example</span></span>|<span data-ttu-id="34007-151">Résultat</span><span class="sxs-lookup"><span data-stu-id="34007-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="34007-152">Non</span><span class="sxs-lookup"><span data-stu-id="34007-152">No</span></span>|<span data-ttu-id="34007-153">Non</span><span class="sxs-lookup"><span data-stu-id="34007-153">No</span></span>|`Dim qty`|<span data-ttu-id="34007-154">Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="34007-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="34007-155">Si `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="34007-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="34007-156">Non</span><span class="sxs-lookup"><span data-stu-id="34007-156">No</span></span>|<span data-ttu-id="34007-157">Oui</span><span class="sxs-lookup"><span data-stu-id="34007-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="34007-158">Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur.</span><span class="sxs-lookup"><span data-stu-id="34007-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="34007-159">Consultez la page [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="34007-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="34007-160">Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.</span><span class="sxs-lookup"><span data-stu-id="34007-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="34007-161">Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="34007-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="34007-162">Oui</span><span class="sxs-lookup"><span data-stu-id="34007-162">Yes</span></span>|<span data-ttu-id="34007-163">Non</span><span class="sxs-lookup"><span data-stu-id="34007-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="34007-164">La variable est initialisée avec la valeur par défaut du type de données.</span><span class="sxs-lookup"><span data-stu-id="34007-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="34007-165">Pour plus d’informations, consultez [une instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34007-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="34007-166">Oui</span><span class="sxs-lookup"><span data-stu-id="34007-166">Yes</span></span>|<span data-ttu-id="34007-167">Oui</span><span class="sxs-lookup"><span data-stu-id="34007-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="34007-168">Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="34007-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="34007-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="34007-169">Example</span></span>  
 <span data-ttu-id="34007-170">Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="34007-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 <span data-ttu-id="34007-171">[!code-vb[VbVbalrTypeInference n °&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="34007-171">[!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="34007-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="34007-172">Example</span></span>  
 <span data-ttu-id="34007-173">L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.</span><span class="sxs-lookup"><span data-stu-id="34007-173">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 <span data-ttu-id="34007-174">[!code-vb[VbVbalrTypeInference&#11;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="34007-174">[!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34007-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34007-175">See Also</span></span>  
 <span data-ttu-id="34007-176">[Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34007-176">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="34007-177"> [Inférence de Type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="34007-177"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="34007-178"> [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34007-178"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="34007-179"> [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34007-179"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="34007-180"> [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34007-180"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="34007-181"> [Boîte de dialogue Options par défaut, les projets, Visual Basic](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="34007-181"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="34007-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="34007-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="34007-183"> [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span><span class="sxs-lookup"><span data-stu-id="34007-183"> [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span></span>
