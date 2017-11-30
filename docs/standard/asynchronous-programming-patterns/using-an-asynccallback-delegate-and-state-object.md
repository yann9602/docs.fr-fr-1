---
title: "Utilisation d'un délégué AsyncCallback et objet d'état"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Utilisation d'un délégué AsyncCallback et objet d'état
Lorsque vous utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread séparé, vous pouvez utiliser un objet d’état pour passer des informations entre les rappels et pour récupérer un résultat final. Cette rubrique illustre cette pratique en développant l’exemple de [à l’aide d’un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer les informations de nom de domaine (DNS) pour les ordinateurs spécifiés par l’utilisateur. Cet exemple définit et utilise la `HostRequest` classe pour stocker les informations d’état. A `HostRequest` objet est créé pour chaque nom d’ordinateur entré par l’utilisateur. Cet objet est passé à la <xref:System.Net.Dns.BeginGetHostByName%2A> (méthode). Le `ProcessDnsInformation` méthode est appelée chaque fois une demande est terminée. Le `HostRequest` objet est récupéré à l’aide de la <xref:System.IAsyncResult.AsyncState%2A> propriété. Le `ProcessDnsInformation` utilise le `HostRequest` objet à stocker le <xref:System.Net.IPHostEntry> retourné par la requête ou un <xref:System.Net.Sockets.SocketException> levé par la demande. Lorsque toutes les demandes sont terminées, l’application effectue une itération sur la `HostRequest` des objets et affiche les informations DNS ou <xref:System.Net.Sockets.SocketException> message d’erreur.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
