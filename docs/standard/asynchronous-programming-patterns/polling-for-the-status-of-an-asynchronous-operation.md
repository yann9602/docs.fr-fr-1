---
title: "Interrogation de l'état d'une opération asynchrone"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Interrogation de l'état d'une opération asynchrone
Les applications qui peuvent effectuer un autre travail en attendant les résultats d’une opération asynchrone ne doivent pas bloquer en attente jusqu'à ce que l’opération se termine. Pour continuer l’exécution des instructions en attendant une opération asynchrone se termine, utilisez une des options suivantes :  
  
-   Utilisez le <xref:System.IAsyncResult.IsCompleted%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* méthode pour déterminer si l’opération est terminée. Cette approche est appelée interrogation et est présentée dans cette rubrique.  
  
-   Utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread distinct. Pour obtenir un exemple qui illustre cette approche, consultez [à l’aide d’un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer des informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur. Cet exemple démarre l’opération asynchrone et imprime ensuite des points («. ») au niveau de la console jusqu'à ce que l’opération est terminée. Notez que **null** (**rien** en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> et <xref:System.Object> paramètres car ces arguments ne sont pas requis lors de l’utilisation de cette approche.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
