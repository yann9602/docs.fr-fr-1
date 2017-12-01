---
title: "Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
Les applications qui peuvent effectuer un autre travail en attendant les résultats d’une opération asynchrone ne doivent pas bloquer en attente jusqu'à ce que l’opération se termine. Pour continuer l’exécution des instructions en attendant une opération asynchrone se termine, utilisez une des options suivantes :  
  
-   Utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread distinct. Cette approche est présentée dans cette rubrique.  
  
-   Utilisez le <xref:System.IAsyncResult.IsCompleted%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* méthode pour déterminer si l’opération est terminée. Pour obtenir un exemple qui illustre cette approche, consultez [d’interrogation de l’état d’une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer les informations de nom de domaine (DNS) pour les ordinateurs spécifiés par l’utilisateur. Cet exemple crée un <xref:System.AsyncCallback> délégué qui référence le `ProcessDnsInformation` (méthode). Cette méthode est appelée une fois pour chaque demande asynchrone d’informations DNS.  
  
 Notez que l’hôte spécifié par l’utilisateur est passé à la <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> paramètre. Pour obtenir un exemple qui illustre la définition et à l’aide d’un objet d’état plus complexe, consultez [à l’aide d’un délégué AsyncCallback et un objet d’état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Appel de méthodes asynchrones à l'aide d'IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [Utilisation d'un délégué AsyncCallback et objet d'état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
