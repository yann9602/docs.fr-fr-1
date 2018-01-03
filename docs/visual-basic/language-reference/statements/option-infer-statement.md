---
title: Instruction Option Infer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c8bd94bc8dd379edfda8c4350428684a5cda0b1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="a1b3f-102">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="a1b3f-102">Option Infer Statement</span></span>
<span data-ttu-id="a1b3f-103">Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b3f-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="a1b3f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="a1b3f-105">Parts</span></span>  
  
|<span data-ttu-id="a1b3f-106">Terme</span><span class="sxs-lookup"><span data-stu-id="a1b3f-106">Term</span></span>|<span data-ttu-id="a1b3f-107">Définition</span><span class="sxs-lookup"><span data-stu-id="a1b3f-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="a1b3f-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-108">Optional.</span></span> <span data-ttu-id="a1b3f-109">Active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="a1b3f-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-110">Optional.</span></span> <span data-ttu-id="a1b3f-111">Désactive l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1b3f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a1b3f-112">Remarks</span></span>  
 <span data-ttu-id="a1b3f-113">Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="a1b3f-114">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="a1b3f-115">Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="a1b3f-116">Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="a1b3f-117">Dans l'illustration suivante, `Option Infer` est activé.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="a1b3f-118">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="a1b3f-119">![Vue IntelliSense de la déclaration. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="a1b3f-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="a1b3f-120">IntelliSense quand Option Infer est activé</span><span class="sxs-lookup"><span data-stu-id="a1b3f-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="a1b3f-121">Dans l'illustration suivante, `Option Infer` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="a1b3f-122">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="a1b3f-123">Dans cet exemple, le **Option Strict** est défini sur **hors** sur la [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a1b3f-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="a1b3f-124">![Vue IntelliSense de la déclaration. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="a1b3f-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="a1b3f-125">IntelliSense quand Option Infer est désactivé</span><span class="sxs-lookup"><span data-stu-id="a1b3f-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1b3f-126">Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a1b3f-127">exécute des opérations appelées *boxing* et *unboxing* pour effectuer une conversion entre un `Object` et un type valeur, ce qui ralentit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="a1b3f-128">Pour plus d’informations sur les conversions boxing et unboxing, consultez le [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1b3f-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="a1b3f-129">L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="a1b3f-130">Pour plus d’informations, consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a1b3f-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="a1b3f-131">En l'absence d'instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="a1b3f-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="a1b3f-132">Si le code source ne contient pas un `Option Infer` instruction, le **Option Infer** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a1b3f-133">Si le compilateur de ligne de commande est utilisé, le [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="a1b3f-134">Pour définir Option Infer dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="a1b3f-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="a1b3f-135">Dans l’**Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a1b3f-136">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a1b3f-137">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="a1b3f-138">Définissez la valeur de la **Option infer** boîte.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="a1b3f-139">Lorsque vous créez un nouveau projet, le **Option Infer** définition sur le **compiler** onglet est définie sur le **Option Infer** définition dans le **valeurs par défaut VB** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="a1b3f-140">Pour accéder à la **valeurs par défaut VB** boîte de dialogue le **outils** menu, cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a1b3f-141">Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a1b3f-142">Le paramètre par défaut initial dans **valeurs par défaut VB** est `On`.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="a1b3f-143">Pour définir Option Infer sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a1b3f-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="a1b3f-144">Inclure le [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur dans le **vbc** commande.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="a1b3f-145">Types de données et valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a1b3f-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="a1b3f-146">Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="a1b3f-147">Type de données spécifié ?</span><span class="sxs-lookup"><span data-stu-id="a1b3f-147">Data type specified?</span></span>|<span data-ttu-id="a1b3f-148">Initialiseur spécifié ?</span><span class="sxs-lookup"><span data-stu-id="a1b3f-148">Initializer specified?</span></span>|<span data-ttu-id="a1b3f-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1b3f-149">Example</span></span>|<span data-ttu-id="a1b3f-150">Résultat</span><span class="sxs-lookup"><span data-stu-id="a1b3f-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="a1b3f-151">Non</span><span class="sxs-lookup"><span data-stu-id="a1b3f-151">No</span></span>|<span data-ttu-id="a1b3f-152">Non</span><span class="sxs-lookup"><span data-stu-id="a1b3f-152">No</span></span>|`Dim qty`|<span data-ttu-id="a1b3f-153">Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="a1b3f-154">Si `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a1b3f-155">Non</span><span class="sxs-lookup"><span data-stu-id="a1b3f-155">No</span></span>|<span data-ttu-id="a1b3f-156">Oui</span><span class="sxs-lookup"><span data-stu-id="a1b3f-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="a1b3f-157">Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="a1b3f-158">Consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a1b3f-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="a1b3f-159">Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="a1b3f-160">Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a1b3f-161">Oui</span><span class="sxs-lookup"><span data-stu-id="a1b3f-161">Yes</span></span>|<span data-ttu-id="a1b3f-162">Non</span><span class="sxs-lookup"><span data-stu-id="a1b3f-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="a1b3f-163">La variable est initialisée avec la valeur par défaut du type de données.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="a1b3f-164">Pour plus d’informations, consultez [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a1b3f-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="a1b3f-165">Oui</span><span class="sxs-lookup"><span data-stu-id="a1b3f-165">Yes</span></span>|<span data-ttu-id="a1b3f-166">Oui</span><span class="sxs-lookup"><span data-stu-id="a1b3f-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="a1b3f-167">Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1b3f-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1b3f-168">Example</span></span>  
 <span data-ttu-id="a1b3f-169">Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a1b3f-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1b3f-170">Example</span></span>  
 <span data-ttu-id="a1b3f-171">L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.</span><span class="sxs-lookup"><span data-stu-id="a1b3f-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b3f-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1b3f-172">See Also</span></span>  
 [<span data-ttu-id="a1b3f-173">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1b3f-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="a1b3f-174">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="a1b3f-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="a1b3f-175">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1b3f-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="a1b3f-176">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1b3f-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="a1b3f-177">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="a1b3f-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="a1b3f-178">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="a1b3f-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="a1b3f-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="a1b3f-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="a1b3f-180">Conversion boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="a1b3f-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
