---
title: "Opérateurs de comparaison en Visual Basic | Documents Microsoft"
ms.custom: 
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
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 6185d1676f2cd160c9c3e855cce4a6d2bbe2ffb4
ms.lasthandoff: 03/13/2017

---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic
Opérateurs de comparaison comparent deux expressions et retournent un `Boolean` valeur qui représente la relation de leurs valeurs. Il existe des opérateurs pour comparer des valeurs numériques, des opérateurs de comparaison de chaînes et des opérateurs pour comparer des objets. Les trois types d’opérateurs sont détaillés ci-dessous.  
  
## <a name="comparing-numeric-values"></a>Comparer des valeurs numériques  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Compare des valeurs numériques à l’aide de six opérateurs de comparaison numériques. Chaque opérateur accepte comme opérandes deux expressions qui correspondent à des valeurs numériques. Le tableau suivant répertorie les opérateurs et présente des exemples de chacun.  
  
|Opérateur|Condition testée|Exemples|  
|--------------|----------------------|--------------|  
|`=`(Égalité)|Est la valeur de la première expression égale à la valeur de la seconde ?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`(Inégalité)|La valeur de la première expression n’est pas égale à la valeur de la seconde ?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`(Inférieur à)|Est la valeur de la première expression inférieure à la valeur de la seconde ?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`(Supérieur à)|La valeur de la première expression est supérieure à la valeur de la seconde ?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`(Inférieur ou égal à)|Est la valeur de la première expression inférieure ou égale à la valeur de la seconde ?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`(Supérieur ou égal à)|Est la valeur de la première expression supérieure ou égale à la valeur de la seconde ?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Compare des chaînes à l’aide de la [opérateur Like](../../../../visual-basic/language-reference/operators/like-operator.md) , ainsi que les opérateurs de comparaison numériques. Le `Like` opérateur vous permet de spécifier un modèle. La chaîne est ensuite comparée par rapport au modèle, et si elle correspond, le résultat est `True`. Dans le cas contraire, le résultat est `False`. Les opérateurs numériques permettent de comparer `String` valeurs selon leur ordre de tri, comme le montre l’exemple suivant.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Le résultat de l’exemple précédent est `True` car le premier caractère dans la première chaîne est trié avant le premier caractère dans la deuxième chaîne. Si les premiers caractères sont identiques, la comparaison de continuer au caractère suivant dans les deux chaînes et ainsi de suite. Vous pouvez également tester l’égalité de chaînes à l’aide de l’opérateur d’égalité, comme le montre l’exemple suivant.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Si une chaîne est un préfixe de l’autre, tels que « aa » et « aaa », la plus longue chaîne est considéré comme supérieur à la chaîne la plus courte. L'exemple suivant illustre ce comportement.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 L’ordre de tri est basé sur une comparaison binaire ou une comparaison de texte selon le paramètre de `Option Compare`. Pour plus d’informations, consultez [instruction Option Compare](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Comparaison des objets  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Compare deux variables de référence avec l’objet le [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) et [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md). Vous pouvez utiliser un de ces opérateurs pour déterminer si deux variables de référence font référence à la même instance d’objet. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators&#65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 Dans l’exemple précédent, `x Is y` a la valeur `True`, car les deux variables font référence à la même instance. Comparez ce résultat à l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators&#66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 Dans l’exemple précédent, `x Is y` a la valeur `False`, car même si les variables font référence à des objets du même type, ils font référence à des instances distinctes de ce type.  
  
 Lorsque vous souhaitez tester deux objets ne pointe ne pas vers la même instance, le `IsNot` opérateur vous permet d’éviter une combinaison grammaticalement maladroite de `Not` et `Is`. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators&#67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 Dans l’exemple précédent, `If a IsNot b` équivaut à `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Comparaison de Type d’objet  
 Vous pouvez vérifier si un objet est d’un type particulier avec les `TypeOf`... `Is` expression. La syntaxe est la suivante :  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Lors de la `typename` spécifie un type d’interface, puis le `TypeOf`... `Is` retourne `True` si l’objet implémente le type interface. Lors de la `typename` est un type classe, l’expression retourne `True` si l’objet est une instance de la classe spécifiée ou d’une classe qui dérive de la classe spécifiée. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators&#68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 Dans l’exemple précédent, le `TypeOf x Is Control` l’expression `True` , car le type de `x` est `Button`, qui hérite de `Control`.  
  
 Pour plus d’informations, consultez [TypeOf, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Opérateurs de comparaison](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Opérateurs](../../../../visual-basic/language-reference/operators/index.md)   
 [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
