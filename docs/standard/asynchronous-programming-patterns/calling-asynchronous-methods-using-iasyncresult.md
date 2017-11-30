---
title: "Appel de méthodes asynchrones à l'aide d'IAsyncResult"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81c05aeae00e79f614ef1514e54765b21e7e2dde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="f5595-102">Appel de méthodes asynchrones à l'aide d'IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="f5595-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="f5595-103">Types dans le .NET Framework et les bibliothèques de classes de tiers peuvent fournir des méthodes qui permettent à une application continuer l’exécution lors de l’exécution des opérations asynchrones dans les threads autres que le thread d’application principal.</span><span class="sxs-lookup"><span data-stu-id="f5595-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="f5595-104">Les sections suivantes décrivent et fournissent des exemples de code qui illustrent les différentes façons, vous pouvez appeler des méthodes asynchrones qui utilisent la <xref:System.IAsyncResult> modèle de conception.</span><span class="sxs-lookup"><span data-stu-id="f5595-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="f5595-105">[Bloquer l’exécution de l’Application en mettant fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="f5595-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="f5595-106">[Blocage de l’exécution d’applications à l’aide d’un AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="f5595-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="f5595-107">[Interrogation de l’état d’une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="f5595-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="f5595-108">[À l’aide d’un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="f5595-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5595-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5595-109">See Also</span></span>  
 [<span data-ttu-id="f5595-110">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="f5595-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="f5595-111">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="f5595-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
