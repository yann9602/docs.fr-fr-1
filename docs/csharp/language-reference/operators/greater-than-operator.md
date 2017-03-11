---
title: "&gt;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - ">_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "> (opérateur C#)"
  - "opérateur supérieur à (>) (C#)"
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &gt;, op&#233;rateur (r&#233;f&#233;rence C#)
Tous les types numériques et d'énumération définissent un opérateur relationnel « supérieur à » \(`>`\) qui retourne `true` si le premier opérande est supérieur au second, et `false` dans le cas contraire.  
  
## Notes  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `>` \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  Si `>` est surchargé, [\<](../../../csharp/language-reference/operators/less-than-operator.md) doit l'être également.  Lorsqu'un opérateur binaire est surchargé, l'opérateur d'assignation correspondant \(s'il y en a un\) est, lui aussi, implicitement surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#29)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [explicites](../../../csharp/language-reference/keywords/explicit.md)