---
title: "-&gt;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "->_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-> (opérateur C#)"
  - "opérateur d'accès aux membres (->) (C#)"
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# -&gt;, op&#233;rateur (r&#233;f&#233;rence C#)
L'opérateur `->` allie l'annulation de la référence d'un pointeur et l'accès au membre.  
  
## Notes  
 Une expression de forme  
  
```  
x->y  
```  
  
 \(où `x` est un pointeur de type `T*` et `y` un membre de `T`\) est équivalente à  
  
```  
(*x).y  
```  
  
 L'opérateur `->` peut être utilisé uniquement dans du code marqué comme [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 L'opérateur `->` ne peut pas être surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#15)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)