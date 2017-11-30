---
title: "Association efficace d'opérateurs (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="29e98-102">Association efficace d'opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29e98-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="29e98-103">Expressions complexes peuvent contenir plusieurs opérateurs distincts.</span><span class="sxs-lookup"><span data-stu-id="29e98-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="29e98-104">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="29e98-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="29e98-105">Création d’expressions complexes, tel que celui de l’exemple précédent requiert une connaissance approfondie des règles de priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="29e98-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="29e98-106">Pour plus d’informations, consultez [priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="29e98-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="29e98-107">Expressions entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="29e98-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="29e98-108">Fréquence à laquelle vous souhaitez opérations dans un ordre différent de celui déterminé par la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="29e98-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="29e98-109">Prenons l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="29e98-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="29e98-110">L’exemple précédent multiplie `z` par `y`, puis ajoute le résultat à `4`.</span><span class="sxs-lookup"><span data-stu-id="29e98-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="29e98-111">Mais si vous souhaitez ajouter `y` et `4` avant de multiplier le résultat par `z`, vous pouvez substituer la priorité des opérateurs normale en utilisant des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="29e98-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="29e98-112">En plaçant une expression entre parenthèses, vous forcez cette expression soit évaluée en premier, quelle que soit la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="29e98-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="29e98-113">Pour forcer l’exemple précédent pour effectuer l’ajout de tout d’abord, vous pouvez la réécrire comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="29e98-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="29e98-114">L’exemple précédent ajoute `y` et `4`, puis multiplie cette somme par `z`.</span><span class="sxs-lookup"><span data-stu-id="29e98-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="29e98-115">Expressions entre parenthèses imbriquées</span><span class="sxs-lookup"><span data-stu-id="29e98-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="29e98-116">Vous pouvez imbriquer des expressions dans plusieurs niveaux de parenthèses pour substituer davantage la priorité.</span><span class="sxs-lookup"><span data-stu-id="29e98-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="29e98-117">Les expressions plus profondément imbriquées entre parenthèses sont évaluées en premier, suivie de la prochaine plus profondément imbriquée, et ainsi de suite à la moins profondément imbriquée et enfin les expressions en dehors des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="29e98-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="29e98-118">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="29e98-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="29e98-119">Dans l’exemple précédent, `z + 2` est évaluée en premier, puis les autres expressions entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="29e98-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="29e98-120">Élévation à la puissance, qui a généralement la priorité plus élevée que l’addition ou la multiplication, est évaluée en dernier dans cet exemple, car les autres expressions entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="29e98-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e98-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29e98-121">See Also</span></span>  
 [<span data-ttu-id="29e98-122">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29e98-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="29e98-123">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29e98-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="29e98-124">Opérateurs logiques et au niveau du bit en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29e98-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="29e98-125">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29e98-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="29e98-126">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="29e98-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="29e98-127">Comparaisons de valeurs</span><span class="sxs-lookup"><span data-stu-id="29e98-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="29e98-128">Guide pratique : calculer des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="29e98-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="29e98-129">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29e98-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
