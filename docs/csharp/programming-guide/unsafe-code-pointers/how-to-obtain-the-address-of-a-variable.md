---
title: "Comment&#160;: obtenir l&#39;adresse d&#39;une variable (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressions de pointeur (C#), address-of (opérateur)"
  - "pointeurs (C#), & (opérateur)"
  - "variables (C#), opérateur d'adresse"
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: obtenir l&#39;adresse d&#39;une variable (Guide de programmation C#)
Pour obtenir l'adresse d'une expression unaire, dont l'évaluation est une variable fixe, utilisez l'opérateur address\-of :  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 L'opérateur address\-of ne peut pas être appliqué à une variable.  Si la variable est une variable pouvant être déplacée, vous pouvez utiliser l'[instruction fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour fixer temporairement la variable avant d'obtenir son adresse.  
  
 Il est de votre responsabilité de garantir que la variable est initialisée.  Le compilateur ne publiera pas de message d'erreur si la variable n'est pas initialisée.  
  
 Vous ne pouvez pas obtenir l'adresse d'une constante ou d'une valeur.  
  
## Exemple  
 Dans cet exemple, un pointeur vers `int`, `p`, est déclaré et se voit assigner l'adresse d'une variable entière, `number`.  La variable `number` est initialisée à la suite de l'assignation à \*p.  Si vous indiquez cette instruction d'assignation sous la forme d'un commentaire, l'initialisation de la variable `number` est supprimée, mais aucune erreur de compilation n'est émise.  Remarquez l'utilisation de l'opérateur `->` d'[accès au membre](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) pour obtenir et afficher l'adresse stockée dans le pointeur.  
  
 [!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers2.cs#7)]  
  
 [!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#8)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)