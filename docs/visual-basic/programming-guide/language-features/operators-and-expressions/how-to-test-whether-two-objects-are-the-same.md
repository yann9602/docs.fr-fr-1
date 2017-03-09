---
title: "How to: Test Whether Two Objects Are the Same (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], reference"
  - "Is operator [Visual Basic], comparing objects"
  - "reference variables"
  - "variables [Visual Basic], referring to same object"
  - "objects [Visual Basic], variables referring to same"
  - "Visual Basic code, operators"
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Test Whether Two Objects Are the Same (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si vous avez deux variables qui font référence à des objets, vous pouvez utiliser l'opérateur `Is` ou `IsNot`, ou les deux, pour déterminer si elles font référence à la même instance.  
  
### Pour tester si deux objets sont identiques  
  
-   Utilisez [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) ou [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-test-whether-two-_1.vb)]  
  
 Vous souhaitez éventuellement entreprendre une certaine action selon que deux objets font référence ou non à la même instance.  L'exemple précédent compare le contrôle `c` au contrôle actif du formulaire `f`.  S'il n'y a aucun contrôle actif, ou s'il y en a et qu'il ne s'agit pas de la même instance de contrôle que `c`, l'instruction `If` échoue et la procédure est retournée sans traitement supplémentaire.  
  
 L'utilisation de `Is` ou de `IsNot` est une question de commodité personnelle.  L'un peut être plus être plus facile à lire que l'autre dans une expression donnée.  
  
## Voir aussi  
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)