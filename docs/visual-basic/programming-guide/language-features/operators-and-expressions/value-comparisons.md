---
title: Comparaisons de valeurs (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c11f12bbaf261c0853e96802f03322c5e7fdc706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="bb79b-102">Comparaisons de valeurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb79b-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="bb79b-103">Opérateurs de comparaison peuvent être utilisés pour construire des expressions qui comparent les valeurs des variables numériques.</span><span class="sxs-lookup"><span data-stu-id="bb79b-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="bb79b-104">Ces expressions retournent un `Boolean` valeur selon que la comparaison est true ou false.</span><span class="sxs-lookup"><span data-stu-id="bb79b-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="bb79b-105">Voici quelques exemples d’une telle expression.</span><span class="sxs-lookup"><span data-stu-id="bb79b-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="bb79b-106">La première expression prend la valeur `True`, car 45 est supérieur à 26.</span><span class="sxs-lookup"><span data-stu-id="bb79b-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="bb79b-107">Le deuxième exemple prend la valeur `False`, car 26 n’est pas supérieur à 45.</span><span class="sxs-lookup"><span data-stu-id="bb79b-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="bb79b-108">Vous pouvez également comparer des expressions numériques de cette façon.</span><span class="sxs-lookup"><span data-stu-id="bb79b-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="bb79b-109">Vous comparez des expressions peuvent être des expressions complexes, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bb79b-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="bb79b-110">La précédente expression complexe inclut des littéraux, des variables et des appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="bb79b-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="bb79b-111">Les expressions des deux côtés de l’opérateur de comparaison sont évaluées et les valeurs résultantes sont ensuite comparés à l’aide de la `>=` opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="bb79b-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="bb79b-112">Si la valeur de l’expression de gauche est supérieure ou égale à la valeur de l’expression de droite, toute l’expression prend la valeur de `True`; sinon, elle prend la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="bb79b-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="bb79b-113">Les expressions qui comparent des valeurs sont couramment utilisées dans `If...Then` constructions, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bb79b-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="bb79b-114">Le `=` signe est un opérateur de comparaison et un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="bb79b-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="bb79b-115">Lorsqu’il est utilisé comme opérateur de comparaison, il évalue si la valeur de gauche est égale à la valeur à droite, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bb79b-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="bb79b-116">Vous pouvez également utiliser une expression de comparaison n’importe où un `Boolean` valeur est nécessaire, comme dans un `If`, `While`, `Loop`, ou `ElseIf` instruction, ou lors de l’assignation ou du passage d’une valeur à une `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="bb79b-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="bb79b-117">Dans l’exemple suivant, la valeur retournée par l’expression de comparaison est affectée à un `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="bb79b-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bb79b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb79b-118">See Also</span></span>  
 [<span data-ttu-id="bb79b-119">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="bb79b-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="bb79b-120">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="bb79b-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="bb79b-121">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb79b-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="bb79b-122">Guide pratique : calculer des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="bb79b-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="bb79b-123">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb79b-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
