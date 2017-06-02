---
title: "Polling for the Status of an Asynchronous Operation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "asynchronous programming, status polling"
  - "polling asynchronous operation status"
  - "status information [.NET Framework], asynchronous operations"
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Polling for the Status of an Asynchronous Operation
Les applications qui peuvent effectuer un autre travail en attendant les résultats d'une opération asynchrone ne doivent pas bloquer l'attente jusqu'à la fin de l'opération.  Utilisez l'une des options suivantes pour continuer à exécuter les instructions en attendant la fin d'une opération asynchrone :  
  
-   Utilisez la propriété <xref:System.IAsyncResult.IsCompleted%2A> du <xref:System.IAsyncResult> renvoyé par la méthode **Begin** *OperationName* de l'opération asynchrone pour déterminer si l'opération est terminée.  Cette approche est appelée interrogation et est illustrée dans cette rubrique.  
  
-   Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l'opération asynchrone dans un thread séparé.  Pour obtenir un exemple illustrant cette approche, consultez [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## Exemple  
 L'exemple de code suivant illustre l'utilisation de méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du système de noms de domaines \(DNS, Domain Name System\) pour un ordinateur spécifié par l'utilisateur.  Cet exemple commence l'opération asynchrone et imprime des signes « . » \(point\) sur la console jusqu'à ce que l'opération soit terminée.  Notez que la valeur **null** \(**Nothing** en Visual Basic\) est passée pour les paramètres <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> et <xref:System.Object> car ces arguments ne sont pas requis lors de l'utilisation de cette approche.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## Voir aussi  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)