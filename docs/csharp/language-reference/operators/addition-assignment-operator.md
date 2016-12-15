---
title: "+=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "+=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "+= (opérateur C#)"
  - "opérateur d'assignation d'addition (+=) (C#)"
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# +=, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Opérateur d'assignation d'addition.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `+=`, comme  
  
```  
x += y  
```  
  
 est équivalent à  
  
```  
x = x + y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  La signification de l'[opérateur \+](../../../csharp/language-reference/operators/addition-operator.md) dépend des types de `x` et `y` \(addition pour les opérandes numériques, concaténation pour les opérandes de type chaîne, etc.\).  
  
 L'opérateur `+=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'[opérateur \+](../../../csharp/language-reference/operators/addition-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
 L'opérateur `+=` est également utilisé pour spécifier une méthode qui sera appelée en réponse à un événement ; ces méthodes sont appelées « gestionnaires d'événements ».  L'utilisation de l'opérateur `+=` dans ce contexte est connu sous le nom d'*abonnement à un événement*.  Pour plus d'informations, consultez [Comment : s'abonner et annuler l'abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  et [Délégués](../../../csharp/programming-guide/delegates/index.md).  
  
## Exemple  
 [!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)