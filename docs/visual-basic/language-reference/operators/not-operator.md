---
title: "Not Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Not"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean expressions, negating"
  - "operators [Visual Basic], bitwise"
  - "negation operator"
  - "inverse bit values in variables"
  - "bitwise operators, NOT operator"
  - "bitwise comparison"
  - "Not operator [Visual Basic]"
  - "logical negation"
  - "operators [Visual Basic], negation"
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Not Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Effectue une négation logique sur une expression `Boolean` ou une négation de bits sur une expression numérique.  
  
## Syntaxe  
  
```  
  
result = Not expression  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
 `expression`  
 Obligatoire.  Toute expression `Boolean` ou numérique.  
  
## Notes  
 Pour les expressions `Boolean`, le tableau suivant illustre la manière dont l'argument `result` est déterminé :  
  
|Si `expression` est :|La valeur de `result` est|  
|---------------------------|-------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Pour les expressions numériques, l'opérateur `Not` inverse les valeurs de bits de toute expression numérique et définit le bit correspondant dans `result` d'après le tableau suivant :  
  
|Si le bit dans `expression` a la valeur|Le bit dans `result` a la valeur|  
|---------------------------------------------|--------------------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Compte tenu que les opérateurs logiques et de bits ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses afin de garantir une exécution précise.  
  
## Types de données  
 Pour une négation Boolean, le type de données du résultat est `Boolean`.  Pour une négation au niveau du bit, le type de données de résultat est le même que celui de `expression`.  Toutefois, si l'expression est `Decimal`, le résultat est `Long`.  
  
## Surcharge  
 L'opérateur `Not` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `Not` pour effectuer une négation logique sur une expression `Boolean`.  Le résultat est une valeur `Boolean` qui représente l'inverse de la valeur de l'expression.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/not-operator_1.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : `False` et `True`.  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `Not` pour effectuer une négation logique sur les bits individuels d'une expression numérique.  Le bit dans le modèle de résultat a la valeur de l'inverse du bit correspondant dans le modèle d'opérande, y compris le bit de signe.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/not-operator_2.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : \-11, \-9, et \-7.  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)