---
title: "Comment&#160;: obtenir la valeur d&#39;une variable de pointeur (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressions de pointeur (C#), indirection"
  - "pointeurs (C#), * (opérateur)"
  - "pointeurs (C#), indirection"
  - "variables (C#), pointeurs"
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: obtenir la valeur d&#39;une variable de pointeur (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilisez l'opérateur d'indirection du pointeur pour obtenir la variable à l'emplacement pointé par un pointeur.  L'expression prend la forme suivante, où  `p` est un type pointeur :  
  
```  
*p;  
```  
  
 Vous ne pouvez pas utiliser l'opérateur d'indirection unaire sur une expression d'un type autre que le type pointeur.  De plus, vous ne pouvez pas l'appliquer à un pointeur [void](../../../csharp/language-reference/keywords/void.md).  
  
 Lorsque vous appliquez l'opérateur d'indirection à un pointeur [null](../../../csharp/language-reference/keywords/null.md), le résultat dépend de l'implémentation.  
  
## Exemple  
 Dans l'exemple suivant, des pointeurs de types différents accèdent à une variable du type `char`.  Notez que l'adresse de `theChar` variera d'exécution en exécution, car l'adresse physique allouée à une variable peut changer.  
  
 [!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
  **Valeur de theChar \= Z**   
**Adresse de theChar \= 12F718**  
**Valeur de pChar \= Z**   
**Valeur de pInt \= 90**    
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)