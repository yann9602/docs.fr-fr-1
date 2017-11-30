---
title: "Blocage de l'exécution d'applications en mettant fin à une opération asynchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blocage de l'exécution d'applications en mettant fin à une opération asynchrone
Les applications qui ne peut pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que l’opération se termine. Pour bloquer le thread principal de votre application en attendant une opération asynchrone se termine, utilisez une des options suivantes :  
  
-   Appelez les opérations asynchrones **fin** *NomOpération* (méthode). Cette approche est présentée dans cette rubrique.  
  
-   Utilisez le <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* (méthode). Pour obtenir un exemple qui illustre cette approche, consultez [blocage Application d’exécution à l’aide d’un AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Les applications qui utilisent la **fin** *NomOpération* méthode jusqu'à ce qu’une opération asynchrone se termine appellent généralement la **commencer**  *NomOpération* (méthode), effectuer des tâches qui peuvent être effectuée sans les résultats de l’opération, puis appellent **fin** *NomOpération*.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer des informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur. Notez que `null` (`Nothing` en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` et `stateObject` paramètres car ces arguments ne sont pas requis lors de l’utilisation de cette approche.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
