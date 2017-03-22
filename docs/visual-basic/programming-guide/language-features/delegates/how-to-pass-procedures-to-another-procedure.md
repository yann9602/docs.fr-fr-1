---
title: "Comment : passer des procédures à une autre procédure en Visual Basic | Documents Microsoft"
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
- AddressOf operator
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 9865e2d7d3786d289add3fa63b3db777317facdf
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Comment : passer des procédures à une autre procédure en Visual Basic
Cet exemple montre comment utiliser des délégués pour passer d’une procédure à une autre procédure.  
  
 Un délégué est un type que vous pouvez utiliser comme tout autre type dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Le `AddressOf` opérateur retourne un objet délégué lorsqu’il est appliqué à un nom de procédure.  
  
 Cet exemple comporte une procédure avec un paramètre de délégué qui peut prendre une référence à une autre procédure, obtenue avec la `AddressOf` opérateur.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Création du délégué et les procédures correspondantes  
  
1.  Créez un délégué nommé `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates n °&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Créez une procédure nommée `AddNumbers` avec des paramètres et la valeur de retour qui correspondent à celles de `MathOperator`, de sorte que les signatures correspondent.  
  
     [!code-vb[VbVbalrDelegates n °&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Créez une procédure nommée `SubtractNumbers` avec une signature qui correspond à `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates n °&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Créez une procédure nommée `DelegateTest` qui prend un délégué comme paramètre.  
  
     Cette procédure peut accepter une référence à `AddNumbers` ou `SubtractNumbers`, car leurs signatures correspondent à la `MathOperator` signature.  
  
     [!code-vb[VbVbalrDelegates n °&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Créez une procédure nommée `Test` qui appelle `DelegateTest` une fois avec le délégué de `AddNumbers` comme paramètre et à nouveau avec le délégué de `SubtractNumbers` en tant que paramètre.  
  
     [!code-vb[VbVbalrDelegates n °&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Lors de la `Test` est appelée, elle affiche d’abord le résultat de `AddNumbers` sur `5` et `3`, qui est de 8. Le résultat de `SubtractNumbers` sur `9` et `3` s’affiche, qui est de 6.  
  
## <a name="see-also"></a>Voir aussi  
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [AddressOf (opérateur)](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegate, instruction](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Guide pratique : appeler une méthode déléguée](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
