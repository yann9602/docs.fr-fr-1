---
title: Select...Case, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="3c750-102">Select...Case, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c750-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="3c750-103">Exécute l’une des multiples groupes d’instructions, en fonction de la valeur d’une expression.</span><span class="sxs-lookup"><span data-stu-id="3c750-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c750-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c750-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="3c750-105">Composants</span><span class="sxs-lookup"><span data-stu-id="3c750-105">Parts</span></span>  
  
|<span data-ttu-id="3c750-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3c750-106">Term</span></span>|<span data-ttu-id="3c750-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3c750-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="3c750-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c750-108">Required.</span></span> <span data-ttu-id="3c750-109">Expression.</span><span class="sxs-lookup"><span data-stu-id="3c750-109">Expression.</span></span> <span data-ttu-id="3c750-110">Doit correspondre à un des types de données élémentaires (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, et `UShort`).</span><span class="sxs-lookup"><span data-stu-id="3c750-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="3c750-111">Requis dans un `Case` instruction.</span><span class="sxs-lookup"><span data-stu-id="3c750-111">Required in a `Case` statement.</span></span> <span data-ttu-id="3c750-112">Liste des clauses d’expression représentant les valeurs correspondantes pour `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3c750-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="3c750-113">Plusieurs clauses d’expression sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="3c750-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="3c750-114">Chaque clause peut prendre une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c750-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="3c750-115">-   *expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="3c750-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="3c750-116">-[ `Is` ] *comparisonoperator* *expression*</span><span class="sxs-lookup"><span data-stu-id="3c750-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="3c750-117">-   *expression*</span><span class="sxs-lookup"><span data-stu-id="3c750-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="3c750-118">Utilisez le `To` les valeurs de mot clé pour spécifier les limites d’une plage de correspondance pour `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3c750-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="3c750-119">La valeur de `expression1` doit être inférieur ou égal à la valeur de `expression2`.</span><span class="sxs-lookup"><span data-stu-id="3c750-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="3c750-120">Utilisez le `Is` mot clé avec un opérateur de comparaison (`=`, `<>`, `<`, `<=`, `>`, ou `>=`) pour spécifier une restriction sur les valeurs correspondantes pour `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3c750-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="3c750-121">Si le `Is` mot clé n’est pas fourni, il est automatiquement insérée avant *comparisonoperator*.</span><span class="sxs-lookup"><span data-stu-id="3c750-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="3c750-122">Le formulaire en spécifiant uniquement `expression` est traité comme un cas spécial de la `Is` écran where *comparisonoperator* est le signe égal (`=`).</span><span class="sxs-lookup"><span data-stu-id="3c750-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="3c750-123">Ce formulaire est évalué comme `testexpression`  =  `expression`.</span><span class="sxs-lookup"><span data-stu-id="3c750-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="3c750-124">Les expressions dans `expressionlist` peut être de n’importe quel type de données, à condition qu’ils soient implicitement convertibles au type de `testexpression` et approprié `comparisonoperator` n’est valide pour les deux types avec lesquels il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3c750-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="3c750-125">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c750-125">Optional.</span></span> <span data-ttu-id="3c750-126">Une ou plusieurs instructions qui suivent `Case` s’exécutent si `testexpression` correspond à une clause dans `expressionlist`.</span><span class="sxs-lookup"><span data-stu-id="3c750-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="3c750-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c750-127">Optional.</span></span> <span data-ttu-id="3c750-128">Une ou plusieurs instructions qui suivent `Case Else` s’exécutent si `testexpression` ne correspond pas à une clause dans la `expressionlist` de toutes les `Case` instructions.</span><span class="sxs-lookup"><span data-stu-id="3c750-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="3c750-129">Termine la définition de la `Select`... `Case` construction.</span><span class="sxs-lookup"><span data-stu-id="3c750-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c750-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="3c750-130">Remarks</span></span>  
 <span data-ttu-id="3c750-131">Si `testexpression` correspond à un `Case` `expressionlist` clause, les instructions qui suivent `Case` instruction s’exécutent dans la prochaine `Case`, `Case Else`, ou `End Select` instruction.</span><span class="sxs-lookup"><span data-stu-id="3c750-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="3c750-132">Contrôle passe alors à l’instruction qui suit `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3c750-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="3c750-133">Si `testexpression` correspond à un `expressionlist` clause dans plusieurs `Case` clause, seules les instructions qui suivent la première correspondance exécutent.</span><span class="sxs-lookup"><span data-stu-id="3c750-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="3c750-134">Le `Case Else` instruction permet de présenter le `elsestatements` à exécuter si aucune correspondance n’est trouvée entre la `testexpression` et un `expressionlist` clause dans toute autre `Case` instructions.</span><span class="sxs-lookup"><span data-stu-id="3c750-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="3c750-135">Mais non obligatoire, il est judicieux d’avoir un `Case Else` instruction dans votre `Select Case` construction gérer imprévus `testexpression` valeurs.</span><span class="sxs-lookup"><span data-stu-id="3c750-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="3c750-136">Si aucun `Case` `expressionlist` clause correspond à `testexpression` et il n’est pas `Case Else` instruction, le contrôle passe à l’instruction qui suit `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3c750-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="3c750-137">Vous pouvez utiliser plusieurs expressions ou plages dans chaque `Case` clause.</span><span class="sxs-lookup"><span data-stu-id="3c750-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="3c750-138">Par exemple, la ligne suivante est valide.</span><span class="sxs-lookup"><span data-stu-id="3c750-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="3c750-139">Le `Is` mot-clé dans le `Case` et `Case Else` instructions n’est pas le même que le [est un opérateur](../../../visual-basic/language-reference/operators/is-operator.md), qui est utilisé pour la comparaison de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="3c750-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="3c750-140">Vous pouvez spécifier des plages et des expressions multiples pour des chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="3c750-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="3c750-141">Dans l’exemple suivant, `Case` correspond à n’importe quelle chaîne qui est exactement égal à « pommes », a une valeur comprise entre « fruits à coques » et « a » dans l’ordre alphabétique ou contient la même valeur exacte que la valeur actuelle de `testItem`.</span><span class="sxs-lookup"><span data-stu-id="3c750-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="3c750-142">Le paramètre de `Option Compare` peut affecter les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="3c750-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="3c750-143">Sous `Option Compare Text`, les chaînes « Apples » et « apples » considérées comme égales, mais sous `Option Compare Binary`, ils ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="3c750-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c750-144">A `Case` instruction avec plusieurs clauses peut exposer un comportement appelé *de court-circuit*.</span><span class="sxs-lookup"><span data-stu-id="3c750-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="3c750-145">Visual Basic évalue les clauses de gauche à droite et si un produit une correspondance avec `testexpression`, les autres clauses ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="3c750-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="3c750-146">Court-circuit peut améliorer les performances, mais elle peut produire des résultats inattendus si vous attendez chaque expression dans `expressionlist` à évaluer.</span><span class="sxs-lookup"><span data-stu-id="3c750-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="3c750-147">Pour plus d’informations sur le court-circuit, consultez [Expressions booléennes](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3c750-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="3c750-148">Si le code dans un `Case` ou `Case Else` bloc d’instructions ne doit-elle pas exécuter d’autres instructions dans le bloc, il peut quitter le bloc à l’aide de la `Exit Select` instruction.</span><span class="sxs-lookup"><span data-stu-id="3c750-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="3c750-149">Il transfère le contrôle immédiatement à l’instruction qui suit `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3c750-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="3c750-150">`Select Case`constructions peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="3c750-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="3c750-151">Chaque imbriqués `Select Case` construction doit avoir une correspondance `End Select` instruction et doit être entièrement contenue dans un seul `Case` ou `Case Else` bloc d’instructions d’externe `Select Case` construction dans laquelle elle est imbriquée.</span><span class="sxs-lookup"><span data-stu-id="3c750-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c750-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c750-152">Example</span></span>  
 <span data-ttu-id="3c750-153">L’exemple suivant utilise un `Select Case` construction pour écrire une ligne correspondant à la valeur de la variable `number`.</span><span class="sxs-lookup"><span data-stu-id="3c750-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="3c750-154">La seconde `Case` instruction contient la valeur qui correspond à la valeur actuelle de `number`, de sorte que l’instruction qui écrit « entre 6 et 8, inclusif » s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3c750-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3c750-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c750-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [<span data-ttu-id="3c750-156">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c750-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="3c750-157">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c750-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="3c750-158">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c750-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="3c750-159">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="3c750-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
