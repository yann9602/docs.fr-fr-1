---
title: "&lt;&lt;=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<<= (opérateur d'assignation de décalage vers la gauche C#)"
  - "opérateur d'assignation de décalage vers la gauche (<<=) (C#)"
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &lt;&lt;=, op&#233;rateur (r&#233;f&#233;rence C#)
Opérateur d'assignation de décalage vers la gauche.  
  
## Notes  
 Une expression de la forme  
  
```  
x <<= y  
```  
  
 est évaluée comme  
  
```  
x = x << y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur \<\<](../../../csharp/language-reference/operators/left-shift-operator.md) décale `x` vers la gauche d'un nombre de bits spécifié par `y`.  
  
 L'opérateur `<<=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#12)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)