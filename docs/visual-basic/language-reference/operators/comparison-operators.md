---
title: "Comparison Operators (Visual Basic) | Microsoft Docs"
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
  - "vb.<>"
  - "vb.>="
  - "vb.<="
  - "vb.>"
  - "vb.<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "greater than or equal to operator [Visual Basic]"
  - ">= operator [Visual Basic]"
  - "= operator [Visual Basic]"
  - "< operator [Visual Basic]"
  - "less than operator [Visual Basic]"
  - "relational operators, syntax"
  - "Like operator [Visual Basic]"
  - "<> operator [Visual Basic]"
  - "> operator [Visual Basic]"
  - "equal operator [Visual Basic]"
  - "less than or equal to operator [Visual Basic]"
  - "symbols, operators"
  - "greater than operator [Visual Basic]"
  - "comparing values [Visual Basic]"
  - "operators [Visual Basic], relational"
  - "string comparison [Visual Basic]"
  - "not equal to comparison operator [Visual Basic]"
  - "<= operator [Visual Basic]"
  - "operators [Visual Basic], comparison"
  - "Is operator [Visual Basic]"
  - "comparison operators, Visual Basicl"
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comparison Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les opérateurs de comparaison définis dans Visual Basic sont les suivants.  
  
 Opérateur `<`  
  
 Opérateur `<=`  
  
 Opérateur `>`  
  
 Opérateur `>=`  
  
 Opérateur `=`  
  
 Opérateur `<>`  
  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Ces opérateurs comparent deux expressions pour déterminer si elles sont égales et, dans le cas contraire, identifier leurs différences.  `Is`, `IsNot` et `Like` sont abordés en détail à différentes pages de l'aide.  Cette page aborde en détail les opérateurs de comparaison relationnels.  
  
## Syntaxe  
  
```  
  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## Composants  
 `result`  
 Obligatoire.  Valeur `Boolean` représentant le résultat de la comparaison.  
  
 `expression`  
 Obligatoire.  Toute expression.  
  
 `comparisonoperator`  
 Obligatoire.  Tout opérateur de comparaison relationnel.  
  
 `object1`, `object2`  
 Obligatoire.  Tout nom d'objet de référence.  
  
 `string`  
 Obligatoire.  Toute expression `String`.  
  
 `pattern`  
 Obligatoire.  Toute expression `String` ou plage de caractères.  
  
## Notes  
 Le tableau suivant contient une liste des opérateurs de comparaison relationnels et des conditions qui déterminent si `result` a la valeur `True` ou `False`.  
  
|Opérateur|`True` si|`False` si|  
|---------------|---------------|----------------|  
|`<` \(inférieur à\)|`expression1` \< `expression2`|`expression1` \>\= `expression2`|  
|`<=` \(inférieur ou égal à\)|`expression1` \<\= `expression2`|`expression1` \> `expression2`|  
|`>` \(supérieur à\)|`expression1` \> `expression2`|`expression1` \<\= `expression2`|  
|`>=` \(supérieur ou égal à\)|`expression1` \>\= `expression2`|`expression1` \< `expression2`|  
|`=` \(égal à\)|`expression1` \= `expression2`|`expression1` \<\> `expression2`|  
|`<>` \(différent de\)|`expression1` \<\> `expression2`|`expression1` \= `expression2`|  
  
> [!NOTE]
>  Le [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) est également utilisé comme opérateur d'assignation.  
  
 L'opérateur `Is`, l'opérateur `IsNot` et l'opérateur `Like` ont des fonctionnalités de comparaison spécifiques qui sont en désaccord avec les opérateurs dans le tableau précédent.  
  
## Comparaison de nombres  
 Lorsqu'une expression de type `Single` est comparée à une expression de type `Double`, l'expression `Single` est convertie en `Double`.  Ce comportement est l'inverse de celui trouvé dans Visual Basic 6.  
  
 De la même façon, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double`, l'expression `Decimal` est convertie en `Single` ou `Double`.  Pour les expressions `Decimal`, toute valeur fractionnaire inférieure à 1E\-28 risque d'être perdue.  Du fait de cette perte de valeur fractionnaire, deux valeurs peuvent être considérées comme égales alors qu'elles ne le sont pas.  C'est pourquoi le plus grand soin est nécessaire lors de l'utilisation de l'égalité \(`=`\) pour comparer deux variables à virgule flottante.  Il vaut mieux s'assurer que la valeur absolue de la différence entre les deux nombres est tout au plus une petite tolérance acceptable.  
  
### Imprécision des nombres à virgule flottante  
 Lorsque vous utilisez des nombres à virgule flottante, pensez qu'ils n'ont pas toujours de représentation précise dans la mémoire.  Certaines opérations pourraient avoir des résultats inattendus, comme la comparaison de valeur et l'opérateur [Mod, opérateur](../../../visual-basic/language-reference/operators/mod-operator.md).  Pour plus d'informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Comparaison de chaînes  
 Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées selon leur ordre de tri alphabétique qui dépend du paramètre `Option Compare`.  
  
 `Option Compare Binary` donne lieu à des comparaisons de chaînes basées sur un ordre de tri dérivé de la représentation binaire interne des caractères.  L'ordre de tri est déterminé par la page de codes.  L'exemple suivant montre un ordre de tri binaire typique.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` fournit des comparaisons de chaînes basées sur un ordre de tri de texte qui ne tient pas compte de la casse et qui est déterminé par les paramètres régionaux de votre application.  Lorsque vous définissez `Option Compare Text` et triez les caractères dans l'exemple précédent, l'ordre de tri de texte suivant s'applique :  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### Dépendance des paramètres régionaux  
 Lorsque vous définissez `Option Compare Text`, le résultat d'une comparaison de chaînes peut dépendre des paramètres régionaux définis pour l'application.  Deux caractères peuvent être équivalents selon certains paramètres régionaux, mais pas selon d'autres.  Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, par exemple pour décider si vous pouvez accepter ou non une tentative de connexion, vous devez être conscient du critère de diffusion des paramètres régionaux.  Pensez à définir `Option Compare Binary` ou appeler le <xref:Microsoft.VisualBasic.Strings.StrComp%2A> qui prend les paramètres régionaux en considération.  
  
## Programmation sans type avec les opérateurs de comparaison relationnels  
 L'utilisation d'opérateurs de comparaison relationnels avec des expressions `Object` est interdite sous `Option Strict On`.  Lorsque `Option Strict` est `Off` et `expression1` ou `expression2` est une expression `Object`, les types d'exécution déterminent la façon dont ils sont comparés.  Le tableau suivant montre la façon dont les expressions sont comparées et ce qui résulte de la comparaison, en fonction du type d'exécution des opérandes :  
  
|Si les opérandes sont :|La comparaison est|  
|-----------------------------|------------------------|  
|Les deux `String`|Comparaison de tri à partir des caractéristiques de tri des chaînes.|  
|Les deux numériques|Objets convertis en `Double`, comparaison numérique.|  
|Une valeur numérique et une valeur `String`|La valeur `String` est convertie en `Double` et la comparaison numérique est effectuée.  Si `String` ne peut être converti en `Double`, une exception <xref:System.InvalidCastException> est levée.|  
|L'une ou les deux sont des types référence autres que `String`.|<xref:System.InvalidCastException> levée.|  
  
 Les comparaisons numériques traitent `Nothing` comme 0.  Les comparaisons de chaînes traitent `Nothing` comme `""` \(chaîne vide\).  
  
## Surcharge  
 Les opérateurs de comparaison relationnels \(`<`,   `<=`, `>`, `>=`, `=`, `<>`\) peuvent être *surchargés*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise l'un de ces opérateurs sur une telle classe ou structure, assurez\-vous que vous comprenez le comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Notez que le [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) peut être surchargé uniquement en tant qu'opérateur de comparaison relationnel, pas en tant qu'opérateur d'assignation.  
  
## Exemple  
 L'exemple suivant montre les différentes utilisations des opérateurs de comparaison relationnels dont vous vous servez pour comparer des expressions.  Les opérateurs de comparaison relationnels retournent un résultat `Boolean` qui indique si l'expression spécifiée a la valeur `True`.  Lorsque vous appliquez les opérateurs `>` et `<` à des chaînes, la comparaison est effectuée à l'aide de l'ordre de tri alphabétique normal des chaînes.  Cet ordre peut dépendre de vos paramètres régionaux.  Le fait que le tri respecte la casse ou non dépend du paramètre [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 Dans l'exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True`.  
  
## Voir aussi  
 <xref:System.InvalidCastException>   
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)