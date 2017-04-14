---
title: "Using an AsyncCallback Delegate and State Object | Microsoft Docs"
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
  - "asynchronous programming, delegates"
  - "AsyncCallback delegate, samples"
  - "asynchronous programming, state objects"
  - "IAsyncResult interface, samples"
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Using an AsyncCallback Delegate and State Object
Lorsque vous utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l'opération asynchrone dans un thread séparé, vous pouvez utiliser un objet d'état pour transmettre des informations entre les fonctions de rappel et récupérer un résultat final.  Cette rubrique démontre cette pratique en développant l'exemple dans [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## Exemple  
 L'exemple de code suivant illustre l'utilisation de méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du système de noms de domaines \(DNS, Domain Name System\) pour des ordinateurs spécifiés par l'utilisateur.  Cet exemple définit et utilise la classe `HostRequest` pour stocker des informations d'état.  Un objet `HostRequest` est créé pour chaque nom d'ordinateur entré par l'utilisateur.  Cet objet est passé à la méthode <xref:System.Net.Dns.BeginGetHostByName%2A>.  La méthode `ProcessDnsInformation` est appelée chaque fois qu'une demande est terminée.  L'objet `HostRequest` est récupéré à l'aide de la propriété <xref:System.IAsyncResult.AsyncState%2A>.  La méthode `ProcessDnsInformation` utilise l'objet `HostRequest` pour stocker le <xref:System.Net.IPHostEntry> retourné par la demande ou un <xref:System.Net.Sockets.SocketException> levé par la demande.  Lorsque toutes les demandes sont terminées, l'application itère au sein des objets `HostRequest` et affiche les informations DNS ou le message d'erreur <xref:System.Net.Sockets.SocketException>.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## Voir aussi  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)