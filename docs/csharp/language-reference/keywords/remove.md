---
title: "remove (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "remove_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "remove (accesseur d'événement C#)"
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# remove (R&#233;f&#233;rence C#)
Le mot clé contextuel `remove` sert à définir un accesseur d'événement personnalisé appelé lorsque le code client annule son abonnement à votre [événement](../../../csharp/language-reference/keywords/event.md).  Si vous fournissez un accesseur `remove` personnalisé, vous devez également fournir un accesseur [add](../../../csharp/language-reference/keywords/add.md).  
  
## Exemple  
 L'exemple suivant illustre un événement avec des accesseurs [add](../../../csharp/language-reference/keywords/add.md) et `remove` personnalisés.  Pour obtenir l'exemple complet, consultez [Comment : implémenter des événements d'interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 En général, vous n'avez pas besoin de fournir vos propres accesseurs d'événements personnalisés.  Les accesseurs générés automatiquement par le compilateur lorsque vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)