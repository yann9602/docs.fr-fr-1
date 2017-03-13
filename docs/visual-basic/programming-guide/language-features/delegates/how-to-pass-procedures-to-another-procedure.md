---
title: "How to: Pass Procedures to Another Procedure in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddressOf operator"
  - "delegates [Visual Basic], passing procedures"
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Pass Procedures to Another Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cet exemple montre comment utiliser des délégués pour passer une procédure à une autre procédure.  
  
 Un délégué est un type que vous pouvez utiliser comme n'importe quel autre type dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  L'opérateur `AddressOf` retourne un objet délégué lorsqu'il est appliqué à un nom de procédure.  
  
 Cet exemple comporte une procédure avec un paramètre de délégué qui peut prendre une référence à une autre procédure, obtenue avec l'opérateur `AddressOf`.  
  
### Création du délégué et des procédures correspondantes  
  
1.  Créez un délégué nommé `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Créez une procédure nommée `AddNumbers` avec des paramètres et une valeur de retour qui correspondent à ceux de `MathOperator`, de sorte que les signatures correspondent.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Créez une procédure nommée `SubtractNumbers` avec une signature qui correspond à `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Créez une procédure nommée `DelegateTest` qui prend un délégué comme paramètre.  
  
     Cette procédure peut accepter une référence à `AddNumbers` ou `SubtractNumbers`, car leurs signatures correspondent à la signature de `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Créez une procédure nommée `Test` qui appelle `DelegateTest` une fois avec le délégué de `AddNumbers` comme paramètre, puis une autre fois avec le délégué de `SubtractNumbers` comme paramètre.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Lorsque la procédure `Test` est appelée, elle affiche d'abord le résultat de l'application de `AddNumbers` sur `5` et `3`, ce qui donne 8.  Le résultat de l'application de `SubtractNumbers` sur `9` et `3` est affiché, ce qui donne 6.  
  
## Voir aussi  
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)