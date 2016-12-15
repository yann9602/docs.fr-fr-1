---
title: "Logical and Bitwise Operators in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "operators [Visual Basic], logical"
  - "AndAlso operator"
  - "Not operator [Visual Basic], Boolean expressions"
  - "Xor operator [Visual Basic], Boolean expressions"
  - "And operator [Visual Basic], logical operators"
  - "logical operators"
  - "expressions [Visual Basic], Boolean"
  - "Or operator, logical operators"
  - "Visual Basic code, operators"
  - "short-circuiting, logical operators"
  - "logical operators, short-circuiting"
  - "Visual Basic code, expressions"
  - "logical operators, binary"
  - "OrElse operator [Visual Basic]"
  - "logical operators, unary"
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Logical and Bitwise Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les opérateurs logiques comparent des expressions `Boolean` et retournent un résultat `Boolean`.  Les opérateurs `And`, `Or`, `AndAlso`, `OrElse` et `Xor` sont *binaires* parce qu'ils prennent deux opérandes, tandis que l'opérateur `Not` est *unaire* parce qu'il prend un seul opérande.  Certains de ces opérateurs peuvent également exécuter des opérations logiques de bits sur des valeurs intégrales.  
  
## Opérateur logique unaire  
 L'[Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) effectue une *négation* logique sur une expression `Boolean`.  Il retourne l'opposé logique de son opérande.  Si l'expression a la valeur `True`, `Not` retourne `False` ; si elle a la valeur `False`, `Not` retourne `True`.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## Opérateurs logiques binaires  
 L'[And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) effectue une *conjonction* logique sur deux expressions `Boolean`.  Si les deux expressions ont la valeur `True`, `And` retourne `True`.  Si au moins l'une des expressions a la valeur `False`, `And` retourne `False`.  
  
 L'[Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) effectue une *disjonction* ou une *inclusion* logique sur deux expressions `Boolean`.  Si l'une des deux expressions a la valeur `True`, ou encore si elles ont toutes les deux la valeur `True`, `Or` retourne `True`.  Si aucune expression n'a la valeur `True`, `Or` retourne `False`.  
  
 L'[Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) effectue une *exclusion* logique sur deux expressions `Boolean`.  Si une seule expression a la valeur `True`, `Xor` retourne `True`.  Si les deux expressions ont la valeur `True` ou la valeur `False`, `Xor` retourne `False`.  
  
 L'exemple suivant illustre les opérateurs `And`, `Or` et `Xor`.  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## Opérations logiques de court\-circuit  
 L'[AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) est très similaire à l'opérateur `And`, car il effectue également une conjonction logique sur deux expressions `Boolean`.  La différence principale entre les deux est que `AndAlso` se comporte comme un *court\-circuit*.  Si la première expression d'une expression `AndAlso` a la valeur `False`, la deuxième expression n'est pas évaluée, car elle ne peut pas modifier le résultat final et `AndAlso` retourne `False`.  
  
 De même, l'[OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) effectue une disjonction logique de court\-circuit sur deux expressions `Boolean`.  Si la première expression d'une expression `OrElse` a la valeur `True`, la deuxième expression n'est pas évaluée, car elle ne peut pas modifier le résultat final et `OrElse` retourne `True`.  
  
### Compromis de court\-circuit  
 Un court\-circuit peut améliorer les performances en n'évaluant pas une expression qui ne peut pas modifier le résultat de l'opération logique.  Toutefois, si cette expression exécute des actions supplémentaires, le court\-circuit les ignore.  Par exemple, si l'expression inclut un appel à une procédure `Function`, cette procédure n'est pas appelée si l'expression est court\-circuitée, et le code supplémentaire contenu dans la `Function` ne s'exécute pas.  Par conséquent, la fonction peut ne s'exécuter qu'occasionnellement et ne pas être testée correctement.  Il est également possible que la logique de programme dépende du code dans la `Function`.  
  
 L'exemple suivant illustre la différence entre `And`, `Or` et leurs équivalents de court\-circuit.  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 Dans l'exemple précédent, notez que du code important dans `checkIfValid()` ne s'exécute pas lorsque l'appel est court\-circuité.  La première instruction `If` appelle `checkIfValid()` bien que `12 > 45` retourne `False`, parce que `And` n'effectue pas de court\-circuit.  La deuxième instruction `If` n'appelle pas `checkIfValid()` parce que si `12 > 45` retourne `False`, `AndAlso` court\-circuite la deuxième expression.  La troisième instruction `If` appelle `checkIfValid()` bien que `12 < 45` retourne `True`, parce que `Or` n'effectue pas de court\-circuit.  La quatrième instruction `If` n'appelle pas `checkIfValid()` parce que si `12 < 45` retourne `True`, `OrElse` court\-circuite la deuxième expression.  
  
## Opérateurs de bits  
 Les opérations de bits évaluent deux valeurs intégrales sous forme binaire \(base 2\).  Elles comparent les bits à des positions correspondantes, puis assignent des valeurs en fonction de la comparaison.  L'exemple suivant illustre l'opérateur `And`.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 L'exemple précédent affecte à `x` la valeur de 1.  Cette opération se produit pour les raisons suivantes :  
  
-   Les valeurs sont traitées comme des valeurs binaires :  
  
     3 sous forme binaire \= 011  
  
     5 sous forme binaire \= 101  
  
-   L'opérateur `And` compare les représentations binaires par position binaire \(bit\).  Si les deux bits d'une position donnée correspondent à 1, une valeur égale à 1 est placée à cette position dans le résultat.  Si l'un des deux bits est 0, une valeur égale à 0 est placée à cette position dans le résultat.  Dans l'exemple précédent, cette procédure fonctionne comme suit :  
  
     011 \(3 sous forme binaire\)  
  
     101 \(5 sous forme binaire\)  
  
     001 \(le résultat sous forme binaire\)  
  
-   Le résultat est traité comme une valeur décimale.  La valeur 001 est la représentation binaire de 1, donc `x` \= 1.  
  
 L'opération `Or` de bits est semblable, mais un 1 est assigné au bit de résultat si un ou les deux bits comparés ont la valeur 1.  `Xor` assigne un 1 au bit de résultat si exactement l'un des bits comparés \(pas les deux\) a la valeur 1.  `Not` prend un opérande unique et inverse tous les bits, notamment le bit de signe, et assigne cette valeur au résultat.  Ainsi, pour les nombres positifs signés, `Not` retourne toujours une valeur négative, et pour les nombres négatifs, `Not` retourne toujours une valeur positive ou nulle.  
  
 Les opérateurs `AndAlso` et `OrElse` ne prennent pas en charge les opérations de bits.  
  
> [!NOTE]
>  Les opérations de bits ne peuvent être effectuées que sur des types intégraux.  Les valeurs de virgule flottante doivent être converties en types intégraux avant de poursuivre une opération de bits.  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)