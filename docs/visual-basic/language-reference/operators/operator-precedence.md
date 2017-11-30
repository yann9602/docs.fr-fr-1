---
title: "Priorité des opérateurs en Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c0fb466b404cafdd4b91d061971fd683375c715
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-precedence-in-visual-basic"></a>Priorité des opérateurs en Visual Basic
Lorsque plusieurs opérations ont lieu dans une expression, chaque partie est évaluée et résolue dans un ordre prédéterminé *la priorité des opérateurs*.  
  
## <a name="precedence-rules"></a>Règles de priorité  
 Les expressions contenant des opérateurs à partir de plusieurs catégories, elles sont évaluées selon les règles suivantes :  
  
-   Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante, et que tous ont une priorité supérieure à celle de la comparaison, logiques et les opérateurs au niveau du bit.  
  
-   Tous les opérateurs de comparaison ont la même priorité et ont la précédence la plus élevée que les opérateurs logiques et au niveau du bit, mais moins élevée que les opérateurs arithmétiques et de concaténation.  
  
-   Les opérateurs logiques et au niveau du bit ont l’ordre de priorité décrite dans la section suivante, et leur priorité inférieure à celle de l’arithmétique, concaténation et les opérateurs de comparaison.  
  
-   Opérateurs ayant la même priorité sont évalués de gauche à droite dans l’ordre dans lequel elles apparaissent dans l’expression.  
  
## <a name="precedence-order"></a>Ordre de priorité  
 Les opérateurs sont évalués dans l’ordre de priorité suivant :  
  
### <a name="await-operator"></a>Await, opérateur  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Opérations arithmétiques et les opérateurs de concaténation  
 Exponentiation (`^`)  
  
 Unaire identité et la négation (`+`, `–`)  
  
 Multiplication et division à virgule flottante (`*`, `/`)  
  
 Division d’entier (`\`)  
  
 Modulo arithmétique (`Mod`)  
  
 Addition et soustraction (`+`, `–`)  
  
 Concaténation de chaînes (`&`)  
  
 Décalage de bits arithmétique (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Opérateurs de comparaison  
 Tous les opérateurs de comparaison (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Opérateurs logiques et au niveau du bit  
 Négation (`Not`)  
  
 Association (`And`, `AndAlso`)  
  
 Disjonction inclusive (`Or`, `OrElse`)  
  
 Disjonction exclusive (`Xor`)  
  
### <a name="comments"></a>Commentaires  
 Le `=` opérateur est uniquement l’opérateur d’égalité, pas l’opérateur d’assignation.  
  
 L’opérateur de concaténation de chaîne (`&`) n’est pas un opérateur arithmétique, mais il est groupé avec les opérateurs arithmétiques priorité.  
  
 Le `Is` et `IsNot` opérateurs sont des opérateurs de comparaison de référence objet. Ils ne comparent pas les valeurs de deux objets ; ils vérifient uniquement pour déterminer si deux variables objets font référence à la même instance d’objet.  
  
## <a name="associativity"></a>Associativité  
 Lorsque les opérateurs de même priorité apparaissent ensemble dans une expression, par exemple multiplication et division, le compilateur évalue chaque opération qu’elle rencontre de gauche à droite. L'exemple suivant illustre ce comportement.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 La première expression évalue la division 96 / 8 (ce qui se traduit à 12), puis la division 12 / 4, ce qui entraîne trois. Étant donné que le compilateur évalue les opérations de `n1` de gauche à droite, l’évaluation est le même lorsque cet ordre est indiqué explicitement pour `n2`. Les deux `n1` et `n2` avoir un résultat de trois. En revanche, `n3` a un résultat égal à 48, parce que les parenthèses forcent le compilateur à évaluer 8 / 4 premier.  
  
 En raison de ce comportement, les opérateurs sont dits *associatifs sur leur gauche* dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="overriding-precedence-and-associativity"></a>Substitution de priorité et associativité  
 Vous pouvez utiliser des parenthèses pour forcer certaines parties d’une expression à évaluer avant les autres. Cela peut remplacer l’ordre de priorité et l’associativité de gauche. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]exécute toujours les opérations qui sont placés entre parenthèses avant celles en dehors. Toutefois, dans les parenthèses, il maintient ordinaire priorité et associativité, sauf si vous utilisez des parenthèses dans les parenthèses. L'exemple suivant illustre ce comportement.  
  
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
 [= (opérateur)](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Like (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)  
 [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
