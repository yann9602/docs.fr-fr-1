---
title: "Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle"
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
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle
Les applications qui ne peut pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que l’opération se termine. Pour bloquer le thread principal de votre application en attendant une opération asynchrone se termine, utilisez une des options suivantes :  
  
-   Utilisez le <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* (méthode). Cette approche est présentée dans cette rubrique.  
  
-   Appelez l’opération asynchrone **fin** *NomOpération* (méthode). Pour obtenir un exemple qui illustre cette approche, consultez [bloque l’exécution d’applications en mettant fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Les applications qui utilisent un ou plusieurs <xref:System.Threading.WaitHandle> objets jusqu'à ce qu’une opération asynchrone se termine appellent généralement la **commencer** *NomOpération* (méthode), effectuent le travail qui peut être effectuée sans les résultats de l’opération et bloquer jusqu'à ce que l’opération asynchrone se termine. Une application peut se bloquer sur une seule opération en appelant une de le <xref:System.Threading.WaitHandle.WaitOne%2A> méthodes à l’aide du <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Pour bloquer en attendant un ensemble d’opérations asynchrones se termine, stocker associé <xref:System.IAsyncResult.AsyncWaitHandle%2A> objets dans un tableau et appelez une de le <xref:System.Threading.WaitHandle.WaitAll%2A> méthodes. Pour bloquer en attendant que l’un d’un ensemble d’opérations asynchrones se termine, stocker associé <xref:System.IAsyncResult.AsyncWaitHandle%2A> objets dans un tableau et appelez une de le <xref:System.Threading.WaitHandle.WaitAny%2A> méthodes.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la classe DNS pour récupérer les informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur. L’exemple illustre le blocage à l’aide de la <xref:System.Threading.WaitHandle> associé à l’opération asynchrone. Notez que `null` (`Nothing` en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` et `stateObject` paramètres car ils ne sont pas requis lors de l’utilisation de cette approche.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
