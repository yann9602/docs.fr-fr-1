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
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="fb0f2-102">Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="fb0f2-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="fb0f2-103">Les applications qui peuvent effectuer un autre travail en attendant les résultats d’une opération asynchrone ne doivent pas bloquer en attente jusqu'à ce que l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="fb0f2-104">Pour continuer l’exécution des instructions en attendant une opération asynchrone se termine, utilisez une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb0f2-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="fb0f2-105">Utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="fb0f2-106">Cette approche est présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="fb0f2-107">Utilisez le <xref:System.IAsyncResult.IsCompleted%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* méthode pour déterminer si l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="fb0f2-108">Pour obtenir un exemple qui illustre cette approche, consultez [d’interrogation de l’état d’une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fb0f2-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb0f2-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb0f2-109">Example</span></span>  
 <span data-ttu-id="fb0f2-110">L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer les informations de nom de domaine (DNS) pour les ordinateurs spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="fb0f2-111">Cet exemple crée un <xref:System.AsyncCallback> délégué qui référence le `ProcessDnsInformation` (méthode).</span><span class="sxs-lookup"><span data-stu-id="fb0f2-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="fb0f2-112">Cette méthode est appelée une fois pour chaque demande asynchrone d’informations DNS.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="fb0f2-113">Notez que l’hôte spécifié par l’utilisateur est passé à la <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> paramètre.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="fb0f2-114">Pour obtenir un exemple qui illustre la définition et à l’aide d’un objet d’état plus complexe, consultez [à l’aide d’un délégué AsyncCallback et un objet d’état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="fb0f2-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fb0f2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb0f2-115">See Also</span></span>  
 [<span data-ttu-id="fb0f2-116">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="fb0f2-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="fb0f2-117">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="fb0f2-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="fb0f2-118">Appel de méthodes asynchrones à l'aide d'IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="fb0f2-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="fb0f2-119">Utilisation d'un délégué AsyncCallback et objet d'état</span><span class="sxs-lookup"><span data-stu-id="fb0f2-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
