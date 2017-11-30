---
title: "Opérateurs de bits et opérateurs logiques en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba48f722a11e93f82ae99aa407c3096a964e5ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Opérateurs de bits et opérateurs logiques en Visual Basic
Comparent des opérateurs logiques `Boolean` expressions et retournent un `Boolean` résultat. Le `And`, `Or`, `AndAlso`, `OrElse`, et `Xor` opérateurs sont *binaire* parce qu’ils prennent deux opérandes, tandis que la `Not` opérateur est *unaire* parce qu’il prend un seul opérande. Certains de ces opérateurs peuvent également effectuer des opérations logiques au niveau du bit sur des valeurs intégrales.  
  
## <a name="unary-logical-operator"></a>Opérateur logique unaire  
 Le [pas d’opérateur](../../../../visual-basic/language-reference/operators/not-operator.md) effectue logique *négation* sur un `Boolean` expression. Il donne le contraire logique de son opérande. Si l’expression prend la valeur `True`, puis `Not` retourne `False`; si l’expression prend la valeur `False`, puis `Not` retourne `True`. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>Opérateurs logiques binaires  
 Le [opérateur et](../../../../visual-basic/language-reference/operators/and-operator.md) effectue logique *conjonction* sur deux `Boolean` expressions. Si les deux expressions ont `True`, puis `And` retourne `True`. Si au moins l’une des expressions a la valeur `False`, puis `And` retourne `False`.  
  
 Le [ou opérateur](../../../../visual-basic/language-reference/operators/or-operator.md) effectue logique *disjonction* ou *inclusion* sur deux `Boolean` expressions. Si des expressions a la valeur `True`, ou les deux ont la valeur `True`, puis `Or` retourne `True`. Si aucune expression `True`, `Or` retourne `False`.  
  
 Le [opérateur Xor](../../../../visual-basic/language-reference/operators/xor-operator.md) effectue logique *exclusion* sur deux `Boolean` expressions. Si une seule expression `True`, mais pas les deux, `Xor` retourne `True`. Si les deux expressions ont `True` ou les deux ont la valeur `False`, `Xor` retourne `False`.  
  
 L’exemple suivant illustre la `And`, `Or`, et `Xor` opérateurs.  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>Opérations logiques de court-circuit  
 Le [opérateur AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) est très similaire à la `And` (opérateur), car il effectue également une conjonction logique sur deux `Boolean` expressions. La principale différence entre les deux est que `AndAlso` expose *de court-circuit* comportement. Si la première expression dans une `AndAlso` expression renvoie la valeur `False`, puis la seconde expression n’est pas évaluée, car elle ne peut pas modifier le résultat final, et `AndAlso` retourne `False`.  
  
 De même, la [opérateur OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) effectue une disjonction logique sur deux court-circuit `Boolean` expressions. Si la première expression dans une `OrElse` expression renvoie la valeur `True`, puis la seconde expression n’est pas évaluée, car elle ne peut pas modifier le résultat final, et `OrElse` retourne `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Compromis de court-circuit  
 Court-circuit peut améliorer les performances en n’évaluant ne pas une expression qui ne peut pas modifier le résultat de l’opération logique. Toutefois, si cette expression effectue des actions supplémentaires, le court-circuit les ignore ces actions. Par exemple, si l’expression inclut un appel à une `Function` procédure, que procédure n’est pas appelée si l’expression est court-circuitée, et le code supplémentaire contenu dans le `Function` ne s’exécute pas. Par conséquent, la fonction peut s’exécuter qu’occasionnellement et ne peut pas être testée correctement. Ou la logique du programme peut dépendre du code dans le `Function`.  
  
 L’exemple suivant illustre la différence entre `And`, `Or`et leurs équivalents de court-circuit.  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 Dans l’exemple précédent, notez que du code important dans `checkIfValid()` ne s’exécute pas lorsque l’appel est court-circuité. La première `If` instruction appelle `checkIfValid()` bien `12 > 45` retourne `False`, car `And` n’effectue pas de court-circuit. La seconde `If` instruction n’appelle pas `checkIfValid()`, car lorsque `12 > 45` retourne `False`, `AndAlso` court-circuite la deuxième expression. La troisième `If` instruction appelle `checkIfValid()` bien `12 < 45` retourne `True`, car `Or` n’effectue pas de court-circuit. La quatrième `If` instruction n’appelle pas `checkIfValid()`, car lorsque `12 < 45` retourne `True`, `OrElse` court-circuite la deuxième expression.  
  
## <a name="bitwise-operations"></a>Opérations de bits  
 Opérations de bits évaluent deux valeurs intégrales sous forme binaire (base 2). Elles comparent les bits aux positions correspondantes et puis assignent des valeurs en fonction de la comparaison. L’exemple suivant illustre la `And` opérateur.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 L’exemple précédent définit la valeur de `x` à 1. Cela se produit pour les raisons suivantes :  
  
-   Les valeurs sont traitées en tant que binaire :  
  
     3 sous forme binaire = 011  
  
     5 sous forme binaire = 101  
  
-   Le `And` opérateur compare les représentations binaires par position binaire (bit). Si les deux bits à une position donnée sont 1, 1 est placé à cette position dans le résultat. Si des bits est 0, 0 est placé à cette position dans le résultat. Dans l’exemple précédent cela fonctionne comme suit :  
  
     011 (3 sous forme binaire)  
  
     101 (5 sous forme binaire)  
  
     001 (le résultat sous forme binaire)  
  
-   Le résultat est traité comme séparateur décimal. La valeur 001 est la représentation binaire de 1, donc `x` = 1.  
  
 L’opérateur de bits `Or` opération est similaire, à ceci près que 1 est assigné au bit de résultat si un ou les deux bits comparés est 1. `Xor`assigne un 1 au bit de résultat si exactement l’un des bits comparés (pas les deux) est 1. `Not`accepte un opérande unique et inverse tous les bits, y compris le bit de signe et assigne la valeur au résultat. Cela signifie que pour les nombres positifs signés, `Not` retourne toujours une valeur négative et pour les nombres négatifs, `Not` retourne toujours une valeur positive ou zéro.  
  
 Le `AndAlso` et `OrElse` opérateurs ne prennent pas en charge les opérations de bits.  
  
> [!NOTE]
>  Les opérations au niveau du bit peuvent être effectuées sur les types intégraux uniquement. Valeurs à virgule flottante doivent être converties en types intégraux avant de poursuivre l’opération au niveau du bit.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques/de bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
