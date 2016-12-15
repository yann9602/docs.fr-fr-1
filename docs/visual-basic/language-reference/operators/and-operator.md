---
title: "And Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.And"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic], bitwise"
  - "logical conjunction"
  - "bitwise AND operator [Visual Basic]"
  - "conjunction operator"
  - "And operator [Visual Basic]"
  - "bitwise operators, AND operator"
  - "operators [Visual Basic], conjunction"
  - "bitwise comparison"
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# And Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue une conjonction logique sur deux expressions `Boolean` ou une conjonction d'opérations de bits sur deux expressions numériques.  
  
## Syntaxe  
  
```  
  
result = expression1 And expression2  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  Pour une comparaison Boolean, `result` est la conjonction logique de deux valeurs `Boolean`.  Pour les opérations de bits, `result` est une valeur numérique représentant la conjonction d'opérations de bits de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
 `expression2`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
## Notes  
 Pour la comparaison Boolean, `result` a la valeur `True` si et seulement si `expression1` et `expression2` ont la valeur `True`.  Le tableau suivant illustre la manière dont `result` est déterminé.  
  
|Si `expression1` est :|Et `expression2` a la valeur|La valeur de `result` est|  
|----------------------------|----------------------------------|-------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Dans la comparaison Boolean, l'opérateur `And` évalue toujours les deux expressions qui pourraient inclure des appels de procédure.  [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) exécute le *court\-circuit*, ce qui signifie que si `expression1` a la valeur `False`, `expression2` n'est pas évalué.  
  
 Lorsqu'il est appliqué à des valeurs numériques, l'opérateur `And` effectue une comparaison d'opérations des bits de position identique dans deux expressions numériques et définit le bit correspondant dans `result` d'après le tableau suivant :  
  
|Si le bit dans `expression1` a la valeur|Et si le bit dans `expression2` a la valeur|Le bit dans `result` a la valeur|  
|----------------------------------------------|-------------------------------------------------|--------------------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Compte tenu que les opérateurs logiques et de bits ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses afin de garantir des résultats précis.  
  
## Types de données  
 Si les opérandes se composent d'une expression `Boolean` et d'une expression numérique, Visual Basic convertit l'expression `Boolean` en une valeur numérique \(–1 pour `True` et 0 pour `False`\) et exécute une opération au niveau du bit.  
  
 Pour une comparaison Boolean, le type de données du résultat est `Boolean`.  Pour une comparaison de bits, le type de données du résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`.  Consultez le tableau « Relational and Bitwise Comparisons » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  L'opérateur `And` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `And` pour effectuer une conjonction logique sur deux expressions.  Le résultat est une valeur `Boolean` qui indique si les deux expressions ont la valeur `True`.  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : `True` et `False`.  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `And` pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques.  Le bit du modèle de résultat est défini si les bits correspondants dans les opérandes ont la valeur 1.  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : 8, 2 et 0.  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)