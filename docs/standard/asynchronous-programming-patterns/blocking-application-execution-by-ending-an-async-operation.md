---
title: "Blocking Application Execution by Ending an Async Operation | Microsoft Docs"
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
  - "blocks, asynchronous operations"
  - "AsyncWaitHandle property"
  - "asynchronous programming, blocking applications"
  - "blocking application execution"
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Blocking Application Execution by Ending an Async Operation
Les applications qui ne peuvent pas poursuivre un autre travail en attendant les résultats d'une opération asynchrone doivent se bloquer jusqu'à ce que l'opération se termine.  Utilisez l'une des options suivantes pour bloquer le thread principal de votre application en attendant qu'une opération asynchrone se termine :  
  
-   Appelle la méthode **End** *OperationName* de l'opération asynchrone.  Cette approche est présentée dans cette rubrique.  
  
-   Utilisez la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> du <xref:System.IAsyncResult> retourné par la méthode **Begin** *OperationName* de l'opération asynchrone.  Pour obtenir un exemple illustrant cette approche, consultez [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Les applications qui utilisent la méthode **End** *OperationName* pour se bloquer jusqu'à ce qu'une opération asynchrone soit terminée appellent en général la méthode **Begin** *OperationName*, exécutent le travail qui peut être effectué sans les résultats de l'opération, puis appellent **End** *OperationName*.  
  
## Exemple  
 L'exemple de code suivant illustre l'utilisation de méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du système de noms de domaines \(DNS, Domain Name System\) pour un ordinateur spécifié par l'utilisateur.  Notez que la valeur `null` \(`Nothing` en Visual Basic\) est passée pour les paramètres <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` et `stateObject` car ces derniers ne sont pas requis lors de l'utilisation de cette approche.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## Voir aussi  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)