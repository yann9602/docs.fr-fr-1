---
title: "&gt;&gt;=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ">>=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">>= (opérateur d'assignation de décalage vers la droite) (C#)"
  - "opérateur d'assignation de décalage vers la droite (>>=) (C#)"
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &gt;&gt;=, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Opérateur d'assignation de décalage vers la droite.  
  
## Notes  
 Une expression de la forme  
  
```  
x >>= y  
```  
  
 est évaluée comme  
  
```  
x = x >> y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur \>\>](../../../csharp/language-reference/operators/right-shift-operator.md) décale `x` vers la droite d'une quantité spécifiée par `y`.  
  
 L'opérateur \>\>\= ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [\>\>](../../../csharp/language-reference/operators/right-shift-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)