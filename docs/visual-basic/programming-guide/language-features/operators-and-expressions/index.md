---
title: "Opérateurs et expressions en Visual Basic | Microsoft Docs"
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
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands, definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 069178fe753c3e09116c8a4845f96faf13eb72ec
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
<a id="operators-and-expressions-in-visual-basic" class="xliff"></a>

# Opérateurs et expressions en Visual Basic
Un *opérateur* est un élément de code qui exécute une opération sur un ou plusieurs éléments de code qui contiennent des valeurs. Les éléments de valeur comprennent des variables, des constantes, des littéraux, des propriétés, des expressions et des retours provenant des procédures `Function` et `Operator`.  
  
 Une *expression* est une série d’éléments de valeur combinés à des opérateurs, ce qui retourne une nouvelle valeur. Les opérateurs agissent sur les éléments de valeur en effectuant des calculs, des comparaisons et d’autres opérations.  
  
<a id="types-of-operators" class="xliff"></a>

## Types d’opérateurs  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fournit les types d’opérateurs suivants :  
  
-   Les [opérateurs arithmétiques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) exécutent des calculs familiers sur les valeurs numériques, dont le décalage de leurs modèles binaires.  
  
-   Les [opérateurs de comparaison](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) comparent deux expressions et retournent une valeur `Boolean` représentant le résultat de la comparaison.  
  
-   Les [opérateurs de concaténation](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) joignent plusieurs chaînes dans une seule.  
  
-   Les [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combinent des valeurs `Boolean` ou numériques, et retournent un résultat du même type de données que les valeurs.  
  
 Les éléments de valeur associés à un opérateur sont appelés *opérandes* de cet opérateur. Les opérateurs associés aux éléments de valeur forment des expressions, à l’exception de l’opérateur d’assignation qui forme une *instruction*. Pour plus d’informations, consultez [Instructions](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
<a id="evaluation-of-expressions" class="xliff"></a>

## Évaluation d’expressions  
 Le résultat final d’une expression représente une valeur qui correspond généralement à un type de données familier tel que `Boolean`, `String` ou à un type numérique.  
  
 Voici des exemples d’expressions.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Plusieurs opérateurs peuvent effectuer des actions dans une expression ou instruction unique, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 Dans l’exemple précédent, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] exécute les opérations de l’expression située à droite de l’opérateur d’assignation (`=`), puis assigne la valeur obtenue à la variable `x` située à gauche. Dans la pratique, le nombre d’opérateurs pouvant être combinés dans une expression est illimité, mais il est nécessaire de comprendre la [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) pour garantir l’obtention des résultats attendus.  
  
 Pour obtenir plus d’informations et des exemples, consultez [Surcharge d’opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
<a id="see-also" class="xliff"></a>

## Voir aussi  
 [Opérateurs](../../../../visual-basic/language-reference/operators/index.md)   
 [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Instructions](../../../../visual-basic/language-reference/statements/index.md)
