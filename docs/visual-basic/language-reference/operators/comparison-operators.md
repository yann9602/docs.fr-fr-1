---
title: "Opérateurs de comparaison (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa450f7978f46196663c7534b31597b04d80482a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-visual-basic"></a>Opérateurs de comparaison (Visual Basic)
Voici les opérateurs de comparaison définis dans Visual Basic.  
  
 `<`(opérateur)  
  
 `<=`(opérateur)  
  
 `>`(opérateur)  
  
 `>=`(opérateur)  
  
 `=`(opérateur)  
  
 `<>`(opérateur)  
  
 [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Ces opérateurs comparent deux expressions pour déterminer si elles sont égales, et dans le cas contraire, leurs différences. `Is`, `IsNot`, et `Like` sont présentées en détail dans les pages d’aide distinctes. Opérateurs de comparaison relationnels sont présentées en détail dans cette page.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. A `Boolean` valeur représentant le résultat de la comparaison.  
  
 `expression`  
 Obligatoire. Toute expression.  
  
 `comparisonoperator`  
 Obligatoire. N’importe quel opérateur de comparaison relationnel.  
  
 `object1`, `object2`  
 Requis. Tous les noms d’objet de référence.  
  
 `string`  
 Obligatoire. Toute expression `String`.  
  
 `pattern`  
 Obligatoire. N’importe quel `String` expression ou une plage de caractères.  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant contient une liste des opérateurs de comparaison relationnels et les conditions qui déterminent si `result` est `True` ou `False`.  
  
|Opérateur|`True`If|`False`If|  
|--------------|---------------|----------------|  
|`<`(Inférieur à)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=`(Inférieur ou égal à)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>`(Supérieur à)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=`(Supérieur ou égal à)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=`(Égal à)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>`(Différent de)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  Le [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md) est également utilisé comme un opérateur d’assignation.  
  
 Le `Is` (opérateur), le `IsNot` (opérateur) et le `Like` opérateur ont des fonctionnalités de comparaison spécifiques qui diffèrent des opérateurs dans le tableau précédent.  
  
## <a name="comparing-numbers"></a>Comparaison de nombres  
 Lorsque vous comparez une expression de type `Single` à un de type `Double`, le `Single` expression est convertie en `Double`. Ce comportement est l’inverse de celui trouvé dans Visual Basic 6.  
  
 De même, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double`, le `Decimal` expression est convertie en `Single` ou `Double`. Pour `Decimal` expressions, toute valeur fractionnaire inférieure à 1E-28 peut-être être perdue. Cette perte de valeur fractionnaire risque de deux valeurs considérées comme égales lorsqu’ils ne sont pas. Pour cette raison, vous devez prendre soin lors de l’utilisation de l’égalité (`=`) pour comparer deux variables à virgule flottante. Il est plus sûr tester si la valeur absolue de la différence entre les deux nombres est inférieure à une petite tolérance acceptable.  
  
### <a name="floating-point-imprecision"></a>À virgule flottante imprécision  
 Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours de représentation précise dans la mémoire. Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les [MOD, opérateur](../../../visual-basic/language-reference/operators/mod-operator.md). Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  
 Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées selon leur ordre de tri par ordre alphabétique, qui varie selon le `Option Compare` paramètre.  
  
 `Option Compare Binary`bases de comparaisons sur un ordre de tri dérivé des représentations binaires internes des caractères de chaînes. L’ordre de tri est déterminé par la page de codes. L’exemple suivant montre un ordre de tri binaire standard.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text`bases de chaîne des comparaisons sur un ordre de tri de texte sans respecter la casse déterminé par les paramètres régionaux de votre application. Lorsque vous définissez `Option Compare Text` et triez les caractères dans l’exemple précédent, l’ordre de tri de texte suivant s’applique :  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Dépendance des paramètres régionaux  
 Lorsque vous définissez `Option Compare Text`, le résultat d’une comparaison de chaînes peut dépendre des paramètres régionaux dans lequel l’application est en cours d’exécution. Deux caractères peuvent considérés comme égaux dans des paramètres régionaux, mais pas dans un autre. Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, telles que s’il faut accepter une tentative de connexion, vous devez être alerte sensibilité de paramètres régionaux. Un paramètre `Option Compare Binary` ou appel le <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, qui prend les paramètres régionaux en compte.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programmation sans type avec des opérateurs de comparaison relationnels  
 L’utilisation d’opérateurs de comparaison relationnels avec `Object` expressions n’est pas autorisée sous `Option Strict On`. Lorsque `Option Strict` est `Off`et la valeur `expression1` ou `expression2` est un `Object` expression, les types d’exécution déterminent la façon dont ils sont comparés. Le tableau suivant montre comment les expressions sont comparées et le résultat de la comparaison, en fonction du type d’exécution des opérandes.  
  
|Si les opérandes sont|La comparaison est|  
|---------------------|-------------------|  
|Les deux`String`|Comparaison basée sur les caractéristiques de tri de chaîne de tri.|  
|Les deux numériques|Les objets convertis en `Double`, comparaison numérique.|  
|Une valeur numérique et l’autre`String`|Le `String` est converti en un `Double` et une comparaison numérique est effectuée. Si le `String` ne peut pas être converti en `Double`, un <xref:System.InvalidCastException> est levée.|  
|Les deux sont des types de référence autres que`String`|Un objet <xref:System.InvalidCastException> est levé.|  
  
 Les comparaisons numériques traitent `Nothing` en tant que 0. Comparaisons de chaînes traitent `Nothing` en tant que `""` (une chaîne vide).  
  
## <a name="overloading"></a>Surcharge  
 Opérateurs de comparaison relationnels (`<`. `<=``>`, `>=`, `=`, `<>`) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise un de ces opérateurs sur une telle classe ou structure, assurez-vous que vous comprenez le comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Notez que la [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md) peuvent être surchargées uniquement en tant qu’un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les différentes utilisations des opérateurs de comparaison relationnels, ce qui vous permet de comparer des expressions. Opérateurs de comparaison relationnels retournent un `Boolean` résultat qui indique si l’expression spécifiée a la valeur `True`. Lorsque vous appliquez le `>` et `<` opérateurs en chaînes, la comparaison est effectuée à l’aide de l’ordre de tri alphabétique normal des chaînes. Cet ordre peut dépendre de vos paramètres régionaux. Si le tri respecte la casse ou non dépend de la [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) paramètre.  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 Dans l’exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.InvalidCastException>  
 [= (opérateur)](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
