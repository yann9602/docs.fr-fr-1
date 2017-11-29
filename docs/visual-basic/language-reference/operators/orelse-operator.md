---
title: "Opérateur OrElse (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47239a1d2b5b20f2b8cacc9b9185a0f95f63dc84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="e1853-102">Opérateur OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1853-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="e1853-103">Effectue une disjonction logique inclusive sur deux expressions de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="e1853-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1853-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1853-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e1853-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e1853-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e1853-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e1853-106">Required.</span></span> <span data-ttu-id="e1853-107">Toute expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e1853-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="e1853-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e1853-108">Required.</span></span> <span data-ttu-id="e1853-109">Toute expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e1853-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e1853-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e1853-110">Required.</span></span> <span data-ttu-id="e1853-111">Toute expression `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e1853-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1853-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="e1853-112">Remarks</span></span>  
 <span data-ttu-id="e1853-113">Une opération logique est dite *de court-circuit* si le code compilé peut ignorer l’évaluation d’une expression en fonction du résultat d’une autre expression.</span><span class="sxs-lookup"><span data-stu-id="e1853-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="e1853-114">Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas besoin d’évaluer la seconde expression, car elle ne peut pas changer le résultat final.</span><span class="sxs-lookup"><span data-stu-id="e1853-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="e1853-115">Court-circuit peut améliorer les performances si l’expression ignorée est complexe, ou si elle implique des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="e1853-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="e1853-116">Si un ou les deux expressions ont `True`, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="e1853-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="e1853-117">Le tableau suivant illustre comment `result` est déterminée.</span><span class="sxs-lookup"><span data-stu-id="e1853-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="e1853-118">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="e1853-118">If `expression1` is</span></span>|<span data-ttu-id="e1853-119">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="e1853-119">And `expression2` is</span></span>|<span data-ttu-id="e1853-120">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="e1853-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="e1853-121">(non évaluée)</span><span class="sxs-lookup"><span data-stu-id="e1853-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="e1853-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="e1853-122">Data Types</span></span>  
 <span data-ttu-id="e1853-123">Le `OrElse` opérateur est défini uniquement pour le [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e1853-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="e1853-124">Visual Basic convertit chaque opérande si nécessaire en `Boolean` et effectue l’opération entière en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e1853-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="e1853-125">Si vous assignez le résultat à un type numérique, Visual Basic convertit de `Boolean` à ce type.</span><span class="sxs-lookup"><span data-stu-id="e1853-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="e1853-126">Cela peut entraîner un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="e1853-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="e1853-127">Par exemple, `5 OrElse 12` entraîne `–1` lorsque converti en `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e1853-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e1853-128">Surcharge</span><span class="sxs-lookup"><span data-stu-id="e1853-128">Overloading</span></span>  
 <span data-ttu-id="e1853-129">Le [ou opérateur](../../../visual-basic/language-reference/operators/or-operator.md) et [opérateur IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de cette classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="e1853-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e1853-130">La surcharge la `Or` et `IsTrue` opérateurs affecte le comportement de la `OrElse` opérateur.</span><span class="sxs-lookup"><span data-stu-id="e1853-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="e1853-131">Si votre code utilise `OrElse` sur une classe ou structure qui surcharge `Or` et `IsTrue`, assurez-vous de bien comprendre leur comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="e1853-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="e1853-132">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e1853-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1853-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1853-133">Example</span></span>  
 <span data-ttu-id="e1853-134">L’exemple suivant utilise le `OrElse` opérateur pour effectuer une disjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="e1853-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="e1853-135">Le résultat est un `Boolean` valeur indiquant si une des deux expressions est vraie.</span><span class="sxs-lookup"><span data-stu-id="e1853-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="e1853-136">Si la première expression est `True`, la seconde n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="e1853-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 <span data-ttu-id="e1853-137">L’exemple précédent produit des résultats de `True`, `True`, et `False` respectivement.</span><span class="sxs-lookup"><span data-stu-id="e1853-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="e1853-138">Dans le calcul de `firstCheck`, la seconde expression n’est pas évaluée, car le premier est déjà `True`.</span><span class="sxs-lookup"><span data-stu-id="e1853-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="e1853-139">Toutefois, la seconde expression est évaluée dans le calcul de `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="e1853-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1853-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1853-140">Example</span></span>  
 <span data-ttu-id="e1853-141">L’exemple suivant montre un `If`... `Then` instruction contenant deux appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="e1853-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="e1853-142">Si le premier appel retourne `True`, la seconde procédure n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="e1853-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="e1853-143">Cela peut produire des résultats inattendus si la deuxième procédure effectue des tâches importantes qui doivent toujours être effectuées lors de l’exécution de cette section de code.</span><span class="sxs-lookup"><span data-stu-id="e1853-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e1853-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1853-144">See Also</span></span>  
 [<span data-ttu-id="e1853-145">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1853-145">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="e1853-146">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1853-146">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e1853-147">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="e1853-147">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e1853-148">Or (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e1853-148">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)  
 [<span data-ttu-id="e1853-149">IsTrue (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e1853-149">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="e1853-150">Opérateurs logiques et au niveau du bit en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1853-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
