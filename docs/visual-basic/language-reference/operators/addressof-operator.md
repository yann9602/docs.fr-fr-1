---
title: "AddressOf Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "AddressOf"
  - "vb.AddressOf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddressOf operator"
  - "addresses, passing to API procedures"
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# AddressOf Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Crée une instance déléguée de procédure qui fait référence à la procédure spécifique.  
  
## Syntaxe  
  
```  
  
AddressOf procedurename  
```  
  
## Composants  
 `procedurename`  
 Obligatoire.  Spécifie la procédure à référencer par le délégué de procédure créé récemment.  
  
## Notes  
 L'opérateur `AddressOf` crée un délégué de fonction qui pointe vers la fonction spécifiée par `procedurename`.  Lorsque la procédure spécifiée est une méthode d'instance, le délégué de fonction fait référence à l'instance et à la méthode.  Ensuite, lorsque le délégué de fonction est appelé, la méthode spécifiée de l'instance spécifiée est appelée.  
  
 L'opérateur `AddressOf` peut être utilisé comme opérande d'un constructeur délégué ou bien dans un contexte où le type du délégué peut être déterminé par le compilateur.  
  
## Exemple  
 Cet exemple utilise l'opérateur `AddressOf` pour désigner un délégué qui va gérer l'événement `Click` d'un bouton.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addressof-operator_1.vb)]  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `AddressOf` pour désigner la fonction de démarrage d'un thread.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addressof-operator_2.vb)]  
  
## Voir aussi  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)