---
title: "Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call | Microsoft Docs"
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
  - "vbc30220"
  - "bc30220"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30220"
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un appel à `Invoke` via un délégué a échoué car `Invoke` n'est pas implémenté sur la classe déléguée.  
  
 **ID d'erreur :** BC30220  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous qu'une instance de la classe déléguée a été créée avec une instruction `Dim` et qu'une procédure a été assignée à l'instance déléguée avec l'opérateur `AddressOf`.  
  
2.  Repérez le code qui implémente la classe déléguée et vérifiez qu'il implémente la procédure `Invoke`.  
  
## Voir aussi  
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)