---
title: "Using an AsyncCallback Delegate to End an Asynchronous Operation | Microsoft Docs"
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
  - "ending asynchronous operations"
  - "asynchronous programming, ending operations"
  - "AsyncCallback delegate"
  - "stopping asynchronous operations"
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Using an AsyncCallback Delegate to End an Asynchronous Operation
Les applications qui peuvent effectuer un autre travail en attendant les résultats d'une opération asynchrone ne doivent pas bloquer l'attente jusqu'à la fin de l'opération.  Utilisez l'une des options suivantes pour continuer à exécuter les instructions en attendant la fin d'une opération asynchrone :  
  
-   Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l'opération asynchrone dans un thread séparé.  Cette approche est présentée dans cette rubrique.  
  
-   Utilisez la propriété <xref:System.IAsyncResult.IsCompleted%2A> du <xref:System.IAsyncResult> renvoyé par la méthode **Begin** *OperationName* de l'opération asynchrone pour déterminer si l'opération est terminée.  Pour obtenir un exemple illustrant cette approche, consultez [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## Exemple  
 L'exemple de code suivant illustre l'utilisation de méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du système de noms de domaines \(DNS, Domain Name System\) pour des ordinateurs spécifiés par l'utilisateur.  Cet exemple crée un délégué <xref:System.AsyncCallback> qui fait référence à la méthode `ProcessDnsInformation`.  Cette méthode est appelée une fois pour chaque demande asynchrone d'informations DNS.  
  
 Notez que l'hôte spécifié par l'utilisateur est passé au paramètre <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object>.  Pour obtenir un exemple présentant la définition et l'utilisation d'un objet état plus complexe, consultez [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## Voir aussi  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Calling Asynchronous Methods Using IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)   
 [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)