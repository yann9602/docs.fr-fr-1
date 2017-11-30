---
title: "Comment : passer des procédures à une autre procédure en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Comment : passer des procédures à une autre procédure en Visual Basic
Cet exemple montre comment utiliser des délégués pour passer d’une procédure à une autre procédure.  
  
 Un délégué est un type que vous pouvez utiliser comme tout autre type dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Le `AddressOf` opérateur retourne un objet délégué quand il est appliqué à un nom de procédure.  
  
 Cet exemple comprend une procédure avec un paramètre de délégué qui peut prendre une référence à une autre procédure, obtenue avec la `AddressOf` opérateur.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Création du délégué et les procédures correspondantes  
  
1.  Créez un délégué nommé `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Créez une procédure nommée `AddNumbers` avec des paramètres et la valeur de retour qui correspondent à ceux de `MathOperator`, de sorte que les signatures correspondent.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Créez une procédure nommée `SubtractNumbers` avec une signature qui correspond à `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Créez une procédure nommée `DelegateTest` qui accepte un délégué en tant que paramètre.  
  
     Cette procédure peut accepter une référence à `AddNumbers` ou `SubtractNumbers`, car leurs signatures correspondent à la `MathOperator` signature.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Créez une procédure nommée `Test` qui appelle `DelegateTest` une autre fois avec le délégué de `AddNumbers` en tant que paramètre et une autre fois avec le délégué de `SubtractNumbers` en tant que paramètre.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Lorsque `Test` est appelée, elle affiche d’abord le résultat de `AddNumbers` sur `5` et `3`, qui est de 8. Le résultat de `SubtractNumbers` sur `9` et `3` s’affiche, qui est 6.  
  
## <a name="see-also"></a>Voir aussi  
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [AddressOf (opérateur)](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegate (instruction)](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Guide pratique : appeler une méthode déléguée](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
