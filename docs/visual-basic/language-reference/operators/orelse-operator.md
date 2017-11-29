---
title: "Opérateur OrElse (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47239a1d2b5b20f2b8cacc9b9185a0f95f63dc84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="orelse-operator-visual-basic"></a>Opérateur OrElse (Visual Basic)
Effectue une disjonction logique inclusive sur deux expressions de court-circuit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute expression `Boolean`.  
  
 `expression1`  
 Obligatoire. Toute expression `Boolean`.  
  
 `expression2`  
 Obligatoire. Toute expression `Boolean`.  
  
## <a name="remarks"></a>Remarques  
 Une opération logique est dite *de court-circuit* si le code compilé peut ignorer l’évaluation d’une expression en fonction du résultat d’une autre expression. Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas besoin d’évaluer la seconde expression, car elle ne peut pas changer le résultat final. Court-circuit peut améliorer les performances si l’expression ignorée est complexe, ou si elle implique des appels de procédure.  
  
 Si un ou les deux expressions ont `True`, `result` est `True`. Le tableau suivant illustre comment `result` est déterminée.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(non évaluée)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Types de données  
 Le `OrElse` opérateur est défini uniquement pour le [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic convertit chaque opérande si nécessaire en `Boolean` et effectue l’opération entière en `Boolean`. Si vous assignez le résultat à un type numérique, Visual Basic convertit de `Boolean` à ce type. Cela peut entraîner un comportement inattendu. Par exemple, `5 OrElse 12` entraîne `–1` lorsque converti en `Integer`.  
  
## <a name="overloading"></a>Surcharge  
 Le [ou opérateur](../../../visual-basic/language-reference/operators/or-operator.md) et [opérateur IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de cette classe ou une structure. La surcharge la `Or` et `IsTrue` opérateurs affecte le comportement de la `OrElse` opérateur. Si votre code utilise `OrElse` sur une classe ou structure qui surcharge `Or` et `IsTrue`, assurez-vous de bien comprendre leur comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `OrElse` opérateur pour effectuer une disjonction logique sur deux expressions. Le résultat est un `Boolean` valeur indiquant si une des deux expressions est vraie. Si la première expression est `True`, la seconde n’est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 L’exemple précédent produit des résultats de `True`, `True`, et `False` respectivement. Dans le calcul de `firstCheck`, la seconde expression n’est pas évaluée, car le premier est déjà `True`. Toutefois, la seconde expression est évaluée dans le calcul de `secondCheck`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un `If`... `Then` instruction contenant deux appels de procédure. Si le premier appel retourne `True`, la seconde procédure n’est pas appelée. Cela peut produire des résultats inattendus si la deuxième procédure effectue des tâches importantes qui doivent toujours être effectuées lors de l’exécution de cette section de code.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Or (opérateur)](../../../visual-basic/language-reference/operators/or-operator.md)  
 [IsTrue (opérateur)](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
