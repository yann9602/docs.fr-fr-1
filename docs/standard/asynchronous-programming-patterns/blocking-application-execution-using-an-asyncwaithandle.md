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
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="deeb9-102">Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle</span><span class="sxs-lookup"><span data-stu-id="deeb9-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="deeb9-103">Les applications qui ne peut pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="deeb9-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="deeb9-104">Pour bloquer le thread principal de votre application en attendant une opération asynchrone se termine, utilisez une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="deeb9-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="deeb9-105">Utilisez le <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* (méthode).</span><span class="sxs-lookup"><span data-stu-id="deeb9-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="deeb9-106">Cette approche est présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="deeb9-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="deeb9-107">Appelez l’opération asynchrone **fin** *NomOpération* (méthode).</span><span class="sxs-lookup"><span data-stu-id="deeb9-107">Call the asynchronous operation's **End** *OperationName* method.</span></span> <span data-ttu-id="deeb9-108">Pour obtenir un exemple qui illustre cette approche, consultez [bloque l’exécution d’applications en mettant fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="deeb9-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="deeb9-109">Les applications qui utilisent un ou plusieurs <xref:System.Threading.WaitHandle> objets jusqu'à ce qu’une opération asynchrone se termine appellent généralement la **commencer** *NomOpération* (méthode), effectuent le travail qui peut être effectuée sans les résultats de l’opération et bloquer jusqu'à ce que l’opération asynchrone se termine.</span><span class="sxs-lookup"><span data-stu-id="deeb9-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="deeb9-110">Une application peut se bloquer sur une seule opération en appelant une de le <xref:System.Threading.WaitHandle.WaitOne%2A> méthodes à l’aide du <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="deeb9-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="deeb9-111">Pour bloquer en attendant un ensemble d’opérations asynchrones se termine, stocker associé <xref:System.IAsyncResult.AsyncWaitHandle%2A> objets dans un tableau et appelez une de le <xref:System.Threading.WaitHandle.WaitAll%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="deeb9-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="deeb9-112">Pour bloquer en attendant que l’un d’un ensemble d’opérations asynchrones se termine, stocker associé <xref:System.IAsyncResult.AsyncWaitHandle%2A> objets dans un tableau et appelez une de le <xref:System.Threading.WaitHandle.WaitAny%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="deeb9-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deeb9-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="deeb9-113">Example</span></span>  
 <span data-ttu-id="deeb9-114">L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la classe DNS pour récupérer les informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="deeb9-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="deeb9-115">L’exemple illustre le blocage à l’aide de la <xref:System.Threading.WaitHandle> associé à l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="deeb9-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="deeb9-116">Notez que `null` (`Nothing` en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` et `stateObject` paramètres car ils ne sont pas requis lors de l’utilisation de cette approche.</span><span class="sxs-lookup"><span data-stu-id="deeb9-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="deeb9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deeb9-117">See Also</span></span>  
 [<span data-ttu-id="deeb9-118">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="deeb9-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="deeb9-119">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="deeb9-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
