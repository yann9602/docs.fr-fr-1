---
title: "Comparison Operators in Visual Basic | Microsoft Docs"
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
  - "comparison operators, comparing strings"
  - "comparison operators, comparing objects"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "string comparison [Visual Basic], operators"
  - "objects [Visual Basic], comparing"
  - "numbers, comparing"
  - "Visual Basic code, operators"
  - "string comparison [Visual Basic]"
  - "numeric values, comparing"
  - "comparison operators, comparing numeric values"
  - "operators [Visual Basic], comparison"
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Comparison Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les opérateurs de comparaison comparent deux expressions et retournent une valeur `Boolean` qui représente la relation de leurs valeurs.  Il existe des opérateurs pour comparer des valeurs numériques, des opérateurs pour comparer des chaînes et des opérateurs pour comparer des objets.  Les trois types d'opérateurs sont détaillés ci\-dessous.  
  
## Comparaison de valeurs numériques  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] compare des valeurs numériques à l'aide de six opérateurs de comparaison numériques.  Chaque opérateur accepte comme opérandes deux expressions qui prennent des valeurs numériques.  Le tableau suivant répertorie les opérateurs et affiche des exemples de chacun d'entre eux.  
  
|Opérateur|Condition testée|Exemples|  
|---------------|----------------------|--------------|  
|`=` \(égalité\)|La valeur de la première expression est\-elle égale à la valeur de la seconde ?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` \(inégalité\)|La valeur de la première expression est\-elle inégale à la valeur de la seconde ?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` \(inférieur à\)|La valeur de la première expression est\-elle inférieure à la valeur de la seconde ?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` \(supérieur à\)|La valeur de la première expression est\-elle supérieure à la valeur de la seconde ?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` \(inférieur ou égal à\)|La valeur de la première expression est\-elle inférieure ou égale à la valeur de la seconde ?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` \(supérieur ou égal à\)|La valeur de la première expression est\-elle supérieure ou égale à la valeur de la seconde ?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## Comparaison de chaînes  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] compare des chaînes à l'aide du [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) ainsi que les opérateurs de comparaison numériques.  L'opérateur `Like` vous permet de spécifier un modèle.  La chaîne est ensuite comparée au modèle, et en cas de correspondance, le résultat est `True`.  Sinon, le résultat est `False`.  Les opérateurs numériques vous permettent de comparer des valeurs `String` en fonction de leur ordre de tri, comme illustré dans l'exemple ci\-dessous :  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Le résultat de l'exemple précédent est `True` car le premier caractère de la première chaîne est trié avant le premier caractère de la deuxième chaîne.  Si les premiers caractères sont identiques, la comparaison se poursuit jusqu'au prochain caractère des deux chaînes, etc.  Vous pouvez également tester l'égalité des chaînes à l'aide de l'opérateur d'égalité, comme illustré dans l'exemple ci\-dessous.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Si une chaîne est un préfixe d'une autre chaîne \(« aa » et « aaa », par exemple\), la plus longue chaîne est considérée comme supérieure à la plus courte chaîne.  L'exemple suivant illustre ce comportement.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 L'ordre de tri dépend soit d'une comparaison binaire, soit d'une comparaison textuelle en fonction du paramètre `Option Compare`.  Pour plus d'informations, consultez [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## Comparaison d'objets  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] compare deux variables de référence d'objet avec [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) et [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).  Vous pouvez utiliser l'un ou l'autre de ces opérateurs pour déterminer si deux variables de référence font référence à la même instance d'objet.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_1.vb)]  
  
 Dans l'exemple précédent, `x Is y` a la valeur `True`, parce que les deux variables font référence à la même instance.  Comparez ce résultat à ce qui suit :  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_2.vb)]  
  
 Dans l'exemple précédent, `x Is y` a la valeur `False`, dans la mesure où, même si les variables font référence à des objets du même type, elles se rapportent à des instances distinctes de ce type.  
  
 Lorsque vous souhaitez tester deux objets qui ne pointent pas vers la même instance, l'opérateur `IsNot` vous permet d'éviter une combinaison grammaticalement maladroite de `Not` et `Is`.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_3.vb)]  
  
 Dans l'exemple précédent, `If a IsNot b` est équivalent à `If Not a Is b`.  
  
### Comparaison du type d'objet  
 L'expression `TypeOf`...`Is` permet de tester si un objet est d'un type particulier.  La syntaxe est la suivante :  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Lorsque `typename` spécifie un type interface, l'expression `TypeOf`...`Is` retourne `True` si l'objet implémente le type interface.  Lorsque `typename` est un type classe, l'expression retourne `True` si l'objet est une instance de la classe spécifiée ou d'une classe qui dérive de la classe spécifiée.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_4.vb)]  
  
 Dans l'exemple précédent, l'expression `TypeOf x Is Control` a la valeur `True` car le type de `x` est `Button`, qui hérite de `Control`.  
  
 Pour plus d'informations, consultez [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## Voir aussi  
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operators](../../../../visual-basic/language-reference/operators/index.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)