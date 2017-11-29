---
title: "Comment : déterminer si deux objets sont identiques (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="c0879-102">Comment : déterminer si deux objets sont identiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0879-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="c0879-103">Si vous avez deux variables qui font référence aux objets, vous pouvez utiliser la `Is` ou `IsNot` (opérateur), ou les deux, pour déterminer si elles font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="c0879-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="c0879-104">Pour tester si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="c0879-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="c0879-105">Utilisez le [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) ou [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="c0879-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="c0879-106">Vous pouvez souhaiter prendre une certaine action selon si les deux objets font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="c0879-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="c0879-107">L’exemple précédent compare le contrôle `c` le contrôle actif du formulaire `f`.</span><span class="sxs-lookup"><span data-stu-id="c0879-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="c0879-108">S’il n’existe aucun contrôle actif, ou s’il existe et qu’il n’est pas la même instance de contrôle que `c`, puis la `If` instruction échoue et la procédure est retournée sans traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="c0879-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="c0879-109">Si vous utilisez `Is` ou `IsNot` est une question de commodité personnelle.</span><span class="sxs-lookup"><span data-stu-id="c0879-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="c0879-110">Un peut être plus facile à lire à l’autre dans une expression donnée.</span><span class="sxs-lookup"><span data-stu-id="c0879-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0879-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0879-111">See Also</span></span>  
 [<span data-ttu-id="c0879-112">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0879-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
