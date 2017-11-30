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
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="4ce7d-102">Blocage de l'exécution d'applications en mettant fin à une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="4ce7d-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="4ce7d-103">Les applications qui ne peut pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="4ce7d-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="4ce7d-104">Pour bloquer le thread principal de votre application en attendant une opération asynchrone se termine, utilisez une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ce7d-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="4ce7d-105">Appelez les opérations asynchrones **fin** *NomOpération* (méthode).</span><span class="sxs-lookup"><span data-stu-id="4ce7d-105">Call the asynchronous operations **End** *OperationName* method.</span></span> <span data-ttu-id="4ce7d-106">Cette approche est présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4ce7d-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="4ce7d-107">Utilisez le <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* (méthode).</span><span class="sxs-lookup"><span data-stu-id="4ce7d-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="4ce7d-108">Pour obtenir un exemple qui illustre cette approche, consultez [blocage Application d’exécution à l’aide d’un AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="4ce7d-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="4ce7d-109">Les applications qui utilisent la **fin** *NomOpération* méthode jusqu'à ce qu’une opération asynchrone se termine appellent généralement la **commencer**  *NomOpération* (méthode), effectuer des tâches qui peuvent être effectuée sans les résultats de l’opération, puis appellent **fin** *NomOpération*.</span><span class="sxs-lookup"><span data-stu-id="4ce7d-109">Applications that use the **End** *OperationName* method to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then call **End** *OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce7d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ce7d-110">Example</span></span>  
 <span data-ttu-id="4ce7d-111">L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer des informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ce7d-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="4ce7d-112">Notez que `null` (`Nothing` en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` et `stateObject` paramètres car ces arguments ne sont pas requis lors de l’utilisation de cette approche.</span><span class="sxs-lookup"><span data-stu-id="4ce7d-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4ce7d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ce7d-113">See Also</span></span>  
 [<span data-ttu-id="4ce7d-114">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="4ce7d-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="4ce7d-115">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="4ce7d-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
