---
title: "Xor Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Xor"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exclusive OR operator"
  - "logical exclusion"
  - "operators [Visual Basic], exclusive or"
  - "exclusion operator"
  - "operators [Visual Basic], bitwise"
  - "bitwise operators, XOR operator"
  - "Xor operator [Visual Basic]"
  - "Xor keyword"
  - "bitwise comparison"
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Xor Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue une exclusion logique sur deux expressions `Boolean` ou une exclusion d'opérations de bits sur deux expressions numériques.  
  
## Syntaxe  
  
```  
  
result = expression1 Xor expression2  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute variable `Boolean` ou numérique.  Pour la comparaison Boolean, `result` est l'exclusion logique \(disjonction logique exclusive\) de deux valeurs `Boolean`.  Pour les opérations au niveau du bit, `result` est une valeur numérique représentant l'exclusion d'opérations de bits \(disjonction d'opérations de bits exclusive\) de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
 `expression2`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
## Notes  
 Pour la comparaison Boolean, `result` a la valeur `True` si et seulement si exactement `expression1` ou `expression2` a la valeur `True`.  En d'autres termes, si et uniquement si `expression1` et `expression2` ont les valeurs opposées à la valeur `Boolean`.  Le tableau suivant illustre la manière dont `result` est déterminé.  
  
|Si `expression1` est :|Et `expression2` a la valeur|La valeur de `result` est|  
|----------------------------|----------------------------------|-------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Dans la comparaison Boolean, l'opérateur `Xor` évalue toujours les deux expressions qui pourraient inclure des appels de procédure.  Il n'existe pas d'équivalent court\-circuitant de `Xor`, car le résultat dépend toujours des deux opérandes.  Pour obtenir des informations sur les opérateurs logiques *court\-circuitant*, consultez [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) et [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Pour les opérations au niveau du bit, l'opérateur `Xor` effectue une comparaison de bits de position identique dans deux expressions numériques et définit le bit correspondant dans `result` d'après le tableau suivant :  
  
|Si le bit dans `expression1` a la valeur|Et si le bit dans `expression2` a la valeur|Le bit dans `result` a la valeur|  
|----------------------------------------------|-------------------------------------------------|--------------------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Compte tenu que les opérateurs logiques et de bits ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses afin de garantir une exécution précise.  
  
 Par exemple, 5 `Xor` 3 est 6.  Pour mieux illustrer cette opération, convertissez 5 et 3 en leurs représentations binaire, 101 et 011.  Utilisez ensuite la table précédente pour déterminer que 101 Xor 011 est 110, la représentation binaire du nombre décimal 6.  
  
## Types de données  
 Si les opérandes se composent d'une expression `Boolean` et d'une expression numérique, Visual Basic convertit l'expression `Boolean` en une valeur numérique \(–1 pour `True` et 0 pour `False`\) et exécute une opération au niveau du bit.  
  
 Pour une comparaison `Boolean`, le type de données du résultat est `Boolean`.  Pour une comparaison de bits, le type de données du résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`.  Consultez le tableau « Relational and Bitwise Comparisons » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## Surcharge  
 L'opérateur `Xor` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple utilise l'opérateur `Xor` pour effectuer une exclusion logique \(disjonction logique exclusive\) sur deux expressions.  Le résultat est une valeur `Boolean` qui indique si une seule des expressions a la valeur `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : `False`, `True` et `False`.  
  
## Exemple  
 Cet exemple utilise l'opérateur `Xor` pour effectuer une exclusion logique \(disjonction logique exclusive\) sur les bits de deux expressions numériques.  Le bit du modèle de résultat est défini si un seul des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : 2, 12 et 14.  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)