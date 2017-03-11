---
title: "Operator Precedence in Visual Basic | Microsoft Docs"
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
  - "arithmetic operators, precedence"
  - "operator precedence"
  - "logical operators, precedence"
  - "operators [Visual Basic], associativity"
  - "operators [Visual Basic], resolution"
  - "associativity of operators"
  - "operators [Visual Basic], precedence"
  - "precedence, of operators"
  - "comparison operators, precedence"
  - "math operators"
  - "order of precedence"
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Operator Precedence in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Lorsque plusieurs opérations ont lieu dans une même expression, chaque partie est évaluée et résolue dans un ordre prédéterminé. Cet ordre est connu sous le nom de *priorité des opérateurs*.  
  
## Règles de priorité  
 Lorsque les expressions contiennent des opérateurs issus de plusieurs catégories, elles sont évaluées conformément aux règles suivantes :  
  
-   Les opérateurs de concaténation et arithmétiques ont l'ordre de priorité décrit dans la section suivante et leur priorité est supérieure à celle des opérateurs logiques, de comparaison et de bits.  
  
-   Tous les opérateurs de comparaison ont la même priorité, et leur priorité est plus élevée que les opérateurs logiques et de bits, mais moins élevée que les opérateurs arithmétiques et de concaténation.  
  
-   Les opérateurs de concaténation et arithmétiques ont l'ordre de priorité décrit dans la section suivante et leur priorité est inférieure à celle des opérateurs logiques, de comparaison et de bits.  
  
-   Les opérateurs ayant la même priorité sont évalués de gauche à droite dans l'ordre où ils apparaissent dans l'expression.  
  
## Ordre de priorité  
 Les opérateurs sont évalués dans l'ordre de priorité suivant :  
  
### Attendez que l'opérateur  
 Await  
  
### Opérateurs arithmétiques et de concaténation  
 Élévation à une puissance \(`^`\)  
  
 Identité et négation unaires \(`+`, `–`\)  
  
 Multiplication et division à virgule flottante \(`*`, `/`\)  
  
 Division entière \(`\`\)  
  
 Modulo arithmétique \(`Mod`\)  
  
 Ajout et soustraction \(`+`, `–`\)  
  
 Concaténation de chaînes \(`&`\)  
  
 Décalage de bits arithmétique \(`<<`, `>>`\)  
  
### Opérateurs de comparaison  
 Tous les opérateurs de comparaison \(`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`\)  
  
### Opérateurs logiques et au niveau du bit  
 Négation \(`Not`\)  
  
 Conjonction \(`And`, `AndAlso`\)  
  
 Disjonction inclusive \(`Or`, `OrElse`\)  
  
 Disjonction exclusive \(`Xor`\)  
  
### Commentaires  
 L'opérateur `=` est uniquement l'opérateur de comparaison d'égalité, pas l'opérateur d'assignation.  
  
 L'opérateur de concaténation de chaînes \(`&`\) n'est pas un opérateur arithmétique, mais il est groupé avec les opérateurs arithmétiques pour établir les priorités.  
  
 Les opérateurs `Is` et `IsNot` sont des opérateurs de comparaison de référence d'objet.  Ils ne comparent pas les valeurs de deux objets, mais effectuent une vérification pour déterminer si deux variables d'objet désignent la même instance d'objet.  
  
## Associativité  
 Lorsque des opérateurs de même priorité apparaissent dans la même expression, par exemple multiplication et division, le compilateur évalue chaque opération dans l'ordre d'apparition de gauche à droite.  L'exemple suivant illustre ce comportement.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 La première expression évalue la division 96 \/ 8 \(le résultats est 12\), puis la division 12 \/ 4 \(le résultat est 3\).  Comme le compilateur évalue de gauche à droite les opérations pour `n1`, l'évaluation ne change pas lorsque cet ordre est indiqué explicitement pour `n2`.  Pour `n1` comme pour `n2`, le résultat est trois.  En revanche, `n3` a un résultat égal à 48, parce que les parenthèses forcent le compilateur à évaluer 8 \/ 4 en premier.  
  
 C'est pourquoi, les opérateurs sont dits *associatif à gauche* dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
## Substitution de la priorité et de l'associativité  
 Vous pouvez utiliser des parenthèses pour forcer certaines parties d'une expression à être évaluée avant d'autres.  Cela peut substituer à la fois l'ordre de priorité et l'associativité gauche.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] exécute toujours les opérations qui sont entre parenthèses avant ceux en dehors de. Toutefois, entre parenthèses, il met à jour la priorité ordinaire et l'associativité, sauf si vous utilisez des parenthèses entre parenthèses.  L'exemple suivant illustre ce comportement.  
  
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
  
## Voir aussi  
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)