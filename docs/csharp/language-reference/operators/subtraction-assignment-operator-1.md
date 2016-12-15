---
title: "-=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "-=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-= opérateur (assignation de soustraction C#)"
  - "opérateur d'assignation de soustraction (-=) (C#)"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# -=, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Opérateur d'assignation de soustraction.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `-=`, comme  
  
```  
x -= y  
```  
  
 est équivalent à  
  
```  
x = x - y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  La signification de l'[opérateur \-](../../../csharp/language-reference/operators/subtraction-operator.md) dépend des types de `x` et `y` \(soustraction pour les opérandes numériques, suppression de délégués pour les opérandes de type délégué, etc.\).  
  
 L'opérateur `-=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [\-](../../../csharp/language-reference/operators/subtraction-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
 L'opérateur \-\= est également utilisé en C\# pour annuler un abonnement d'un événement.  Pour plus d'informations, consultez [Comment : s'abonner et annuler l'abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## Exemple  
 [!code-cs[csRefOperators#6](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-assignment-operator-1_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)