---
title: "add (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "add_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "add (accesseur d'événement C#)"
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# add (R&#233;f&#233;rence C#)
Le mot clé contextuel `add` sert à définir un accesseur d'événement personnalisé appelé lorsque le code client s'abonne à votre [événement](../../../csharp/language-reference/keywords/event.md).  Si vous fournissez un accesseur `add` personnalisé, vous devez également fournir un accesseur [remove](../../../csharp/language-reference/keywords/remove.md).  
  
## Exemple  
 L'exemple suivant illustre un événement qui a des accesseurs `add` et [remove](../../../csharp/language-reference/keywords/remove.md) personnalisés.  Pour obtenir l'exemple complet, consultez [Comment : implémenter des événements d'interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/csharp/add_1.cs)]  
  
 En général, vous n'avez pas besoin de fournir vos propres accesseurs d'événements personnalisés.  Les accesseurs générés automatiquement par le compilateur lorsque vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)