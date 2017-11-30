---
title: "Comment : calculer des valeurs numériques (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Comment : calculer des valeurs numériques (Visual Basic)
Vous pouvez calculer des valeurs numériques via l’utilisation d’expressions numériques. A *expression numérique* est une expression qui contient des littéraux, des constantes et des variables représentant des valeurs numériques et les opérateurs qui agissent sur ces valeurs.  
  
## <a name="calculating-numeric-values"></a>Calcul de valeurs numériques  
  
#### <a name="to-calculate-a-numeric-value"></a>Pour calculer une valeur numérique  
  
-   Combiner un ou plusieurs des littéraux numériques, de constantes et variables dans une expression numérique. L’exemple suivant illustre certaines expressions numériques valides.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Les trois premières lignes affichent un littéral, une constante et une variable. Chacune d’elle forme une expression numérique valide par lui-même. La dernière ligne affiche une combinaison d’une variable avec deux littéraux.  
  
     Notez qu’une expression numérique ne constitue pas un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] en elle-même. Vous devez utiliser l’expression dans le cadre d’une instruction complète.  
  
#### <a name="to-store-a-numeric-value"></a>Pour stocker une valeur numérique  
  
-   Vous pouvez utiliser une instruction d’assignation pour assigner la valeur représentée par une expression numérique à une variable, comme illustré dans l’exemple suivant.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     Dans l’exemple précédent, la valeur de l’expression située à droite de l’opérateur égal (`=`) est affectée à la variable `j` sur le côté gauche de l’opérateur, donc `j` correspond à 276.  
  
     Pour plus d’informations, consultez [Instructions](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Plusieurs opérateurs  
 Si l’expression numérique contient plusieurs opérateurs, l’ordre dans lequel ils sont évalués est déterminé par les règles de priorité des opérateurs. Pour remplacer les règles de priorité des opérateurs, vous placez les expressions entre parenthèses, comme dans l’exemple ci-dessus ; les expressions entre parenthèses sont évaluées en premier.  
  
#### <a name="to-override-normal-operator-precedence"></a>Pour substituer la priorité des opérateurs normale  
  
-   Utilisez des parenthèses pour encadrer les opérations que vous souhaitez être exécutées en premier. L’exemple suivant montre deux résultats différents avec les mêmes opérandes et opérateurs.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     Dans l’exemple précédent, le calcul de `j` effectue l’opérateur d’addition (`+`) premier, car les parenthèses autour de `(67 + i)` substituer la priorité normale et la valeur affectée à `j` est 276 (4 fois 69). Le calcul de `k` exécute les opérateurs dans leur priorité normale (`*` avant `+`) et la valeur affectée à `k` est de 270 (268 plus 2).  
  
     Pour plus d’informations, consultez [priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instructions](../../../../visual-basic/language-reference/statements/index.md)  
 [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
