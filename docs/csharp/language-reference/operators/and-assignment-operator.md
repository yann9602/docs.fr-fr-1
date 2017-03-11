---
title: "&amp;=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "&= (opérateur C#)"
  - "opérateur d'assignation AND (&=) (C#)"
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &amp;=, op&#233;rateur (r&#233;f&#233;rence C#)
Opérateur d'assignation AND.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `&=`, comme  
  
```  
x &= y  
```  
  
 est équivalent à  
  
```  
x = x & y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'opérateur [&](../../../csharp/language-reference/operators/and-operator.md) effectue une opération de bits AND logique sur les opérandes de type intégral et une opération AND logique sur les opérandes de type `bool`.  
  
 L'opérateur `&=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [&](../../../csharp/language-reference/operators/and-operator.md) binaire \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#34)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)