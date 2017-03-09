---
title: "|, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "| (opérateur C#)"
  - "opérateur binaire (|) (C#)"
  - "opérateur de bits OR (C#)"
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# |, op&#233;rateur (r&#233;f&#233;rence C#)
Binaire        `|`  binaires sont prédéfinis pour les types intégraux et `bool`.  Pour les types intégraux,  `|`effectue l'opération de bits OR sur ses opérandes.  Pour les opérandes `bool`,  `|` effectue l'opération OR logique sur ses opérandes. Par conséquent, le résultat a la valeur `false` si et seulement si les deux opérandes ont la valeur `false`.  
  
## Notes  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur          `|` \(consultez [operator](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#31)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)