---
title: "/ =, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab0a007f039d3dbda989bb605cb80fcf5fc7460a
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>/=, opérateur (Visual Basic)
Divise la valeur d’une variable ou une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à cette variable ou propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Remarques  
 L’élément sur le côté gauche de la `/=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Le `/=` opérateur divise d’abord la valeur de la variable ou la propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur assigne ensuite le résultat de cette opération en virgule flottante à cette variable ou propriété.  
  
 Cette instruction assigne une `Double` valeur à la variable ou la propriété sur la gauche. If `Option Strict` is `On`, `variableorproperty` must be a `Double`. Si `Option Strict` est `Off`, Visual Basic exécute une conversion implicite et assigne le résultat à `variableorproperty`, avec une erreur possible au moment de l’exécution. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Surcharge  
 Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge la `/` opérateur affecte le comportement de la `/=` (opérateur). Si votre code utilise `/=` sur une classe ou structure qui surcharge `/`, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `/=` opérateur pour diviser une `Integer` variable par une autre et assigner le quotient à la première variable.  
  
 [!code-vb[VbVbalrOperators&#17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)

