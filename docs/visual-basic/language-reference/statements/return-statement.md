---
title: "Return Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Return"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Return statement, syntax"
  - "control flow, returning control to expressions"
  - "Return statement"
  - "expressions [Visual Basic], returning control to"
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Return Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Retourne le contrôle au code qui a appelé une procédure `Function`, `Sub`, `Get`, `Set` ou `Operator`.  
  
## Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## Élément  
 `expression`  
 Obligatoire dans une procédure `Function`, `Get` ou `Operator`.  Expression qui représente la valeur à retourner au code appelant.  
  
## Notes  
 Dans une procédure `Sub` ou `Set`, l'instruction `Return` est équivalente à une instruction `Exit Sub` `Exit Property`, et `expression` ne doit pas être fourni.  
  
 Dans une procédure `Function`, `Get` ou `Operator`, l'instruction `Return` doit contenir `expression`, et `expression` doit avoir pour valeur un type de données convertible vers le type de retour de la procédure.  Dans une procédure `Function` ou `Get`, vous pouvez également assigner une expression au nom de la procédure pour servir de valeur de retour, puis exécuter une instruction `Exit Function` ou `Exit Property`.  Dans une procédure `Operator`, vous devez utiliser `Return` `expression`.  
  
 Vous pouvez inclure autant d'instructions `Return` que nécessaire dans la même procédure.  
  
> [!NOTE]
>  Le code d'un bloc `Finally` est exécuté après que le programme rencontre une instruction `Return` dans un bloc `Try` ou `Catch`, mais avant que cette instruction `Return` ne soit exécutée.  Une instruction d' `Return` ne peut pas être incluse dans un bloc d' `Finally` .  
  
## Exemple  
 L'exemple suivant utilise plusieurs fois l'instruction `Return` pour retourner au code appelant lorsque la procédure ne doit pas effectuer d'autres opérations.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/return-statement_1.vb)]  
  
## Voir aussi  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)