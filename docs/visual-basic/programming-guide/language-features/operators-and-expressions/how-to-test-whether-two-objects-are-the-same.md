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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Comment : déterminer si deux objets sont identiques (Visual Basic)
Si vous avez deux variables qui font référence aux objets, vous pouvez utiliser la `Is` ou `IsNot` (opérateur), ou les deux, pour déterminer si elles font référence à la même instance.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Pour tester si deux objets sont identiques  
  
-   Utilisez le [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) ou [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Vous pouvez souhaiter prendre une certaine action selon si les deux objets font référence à la même instance. L’exemple précédent compare le contrôle `c` le contrôle actif du formulaire `f`. S’il n’existe aucun contrôle actif, ou s’il existe et qu’il n’est pas la même instance de contrôle que `c`, puis la `If` instruction échoue et la procédure est retournée sans traitement supplémentaire.  
  
 Si vous utilisez `Is` ou `IsNot` est une question de commodité personnelle. Un peut être plus facile à lire à l’autre dans une expression donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
