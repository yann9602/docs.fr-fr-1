---
title: "=, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
dev_langs:
- VB
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
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
ms.openlocfilehash: 47b69a908f12ec36daf2848da6ee4b04895fd3a4
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>=, opérateur (Visual Basic)
Assigne une valeur à une variable ou propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
variableorproperty = value  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 N’importe quelle variable accessible en écriture ou n’importe quelle propriété.  
  
 `value`  
 N’importe quel littéral, une constante ou une expression.  
  
## <a name="remarks"></a>Notes  
 L’élément sur le côté gauche du signe égal (`=`) peut être une simple variable scalaire, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md). Le `=` opérateur assigne la valeur située à droite vers la variable ou propriété du côté gauche.  
  
> [!NOTE]
>  Le `=` opérateur est également utilisé comme opérateur de comparaison. Pour plus d’informations, consultez [opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Surcharge  
 Le `=` opérateur peut être surchargée uniquement comme un opérateur de comparaison relationnel et non comme un opérateur d’assignation. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’opérateur d’assignation. La valeur située à droite est assignée à la variable sur la gauche.  
  
 [!code-vb[VbVbalrOperators&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [< = (Opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [* =, Opérateur](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [+=, Opérateur](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [-=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [/ =, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [^ =, Opérateur](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [En lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

