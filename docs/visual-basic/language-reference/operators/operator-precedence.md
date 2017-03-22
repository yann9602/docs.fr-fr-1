---
title: "Priorité des opérateurs dans Visual Basic | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6532fc0c26db3b736c863be075571570a3d25eef
ms.lasthandoff: 03/13/2017

---
# <a name="operator-precedence-in-visual-basic"></a>Priorité des opérateurs en Visual Basic
Lorsque plusieurs opérations ont lieu dans une expression, chaque partie est évalué et résolu dans un ordre prédéterminé *la priorité des opérateurs*.  
  
## <a name="precedence-rules"></a>Règles de priorité  
 Expressions contenant des opérateurs à partir de plusieurs catégories, elles sont évaluées selon les règles suivantes :  
  
-   Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante et leur priorité supérieure à la comparaison, logiques et opérateurs au niveau du bit.  
  
-   Tous les opérateurs de comparaison ont la même priorité et leur priorité supérieure à celle des opérateurs logiques et de bits, mais moins élevée que les opérateurs arithmétiques et de concaténation.  
  
-   Les opérateurs logiques et de bits ont l’ordre de priorité décrit dans la section suivante, et leur priorité inférieure à celle de l’arithmétique, concaténation et les opérateurs de comparaison.  
  
-   Les opérateurs ayant la même priorité sont évalués de gauche à droite dans l’ordre dans lequel ils apparaissent dans l’expression.  
  
## <a name="precedence-order"></a>Ordre de priorité  
 Les opérateurs sont évalués dans l’ordre de priorité suivant :  
  
### <a name="await-operator"></a>Await, opérateur  
 Await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Opérations arithmétiques et concaténation  
 Élévation à la puissance (`^`)  
  
 Unaire identité et la négation (`+`, `–`)  
  
 Multiplication et division à virgule flottante (`*`, `/`)  
  
 Division d’entier (`\`)  
  
 Modulo arithmétique (`Mod`)  
  
 Addition et soustraction (`+`, `–`)  
  
 Concaténation de chaînes (`&`)  
  
 Décalage de bits arithmétique (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Opérateurs de comparaison  
 All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Opérateurs logiques et au niveau du bit  
 Négation (`Not`)  
  
 Association (`And`, `AndAlso`)  
  
 Disjonction inclusive (`Or`, `OrElse`)  
  
 Disjonction exclusive (`Xor`)  
  
### <a name="comments"></a>Commentaires  
 Le `=` opérateur n'est que l’opérateur d’égalité, pas l’opérateur d’assignation.  
  
 L’opérateur de concaténation de chaîne (`&`) n’est pas un opérateur arithmétique, mais il est groupé avec les opérateurs arithmétiques priorités.  
  
 Le `Is` et `IsNot` opérateurs sont des opérateurs de comparaison de référence objet. Ils ne comparent pas les valeurs de deux objets ; ils vérifient uniquement pour déterminer si deux variables objets font référence à la même instance d’objet.  
  
## <a name="associativity"></a>Associativité  
 Lorsque les opérateurs de même priorité apparaissent ensemble dans une expression, par exemple multiplication et division, le compilateur évalue chaque opération qu’elle rencontre de gauche à droite. L'exemple suivant illustre ce comportement.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 La première expression évalue la division 96 / 8 (ce qui entraîne à 12), puis la division 12 / 4, ce qui se traduit par trois. Comme le compilateur évalue les opérations de `n1` de gauche à droite, l’évaluation ne change pas lorsque cet ordre est indiqué explicitement pour `n2`. Les deux `n1` et `n2` ont un résultat de trois. En revanche, `n3` a un résultat égal à 48, parce que les parenthèses forcent le compilateur à évaluer 8 / 4 première.  
  
 En raison de ce comportement, les opérateurs sont dits *associatifs sur leur gauche* dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="overriding-precedence-and-associativity"></a>Substitution de priorité et associativité  
 Vous pouvez utiliser des parenthèses pour forcer certaines parties d’une expression doit être évaluée avant d’autres. Cela peut substituer l’ordre de priorité et l’associativité de gauche. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]effectue toujours les opérations entre parenthèses avant celles en dehors. Toutefois, entre parenthèses, il maintient ordinaire priorité et associativité, sauf si vous utilisez des parenthèses dans les parenthèses. L'exemple suivant illustre ce comportement.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [=, Opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Opérateur](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot, opérateur](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [LIKE (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)   
 [TypeOf, opérateur](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
