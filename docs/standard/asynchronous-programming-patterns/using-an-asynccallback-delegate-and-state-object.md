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
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="6b2e5-102">Utilisation d'un délégué AsyncCallback et objet d'état</span><span class="sxs-lookup"><span data-stu-id="6b2e5-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="6b2e5-103">Lorsque vous utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread séparé, vous pouvez utiliser un objet d’état pour passer des informations entre les rappels et pour récupérer un résultat final.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="6b2e5-104">Cette rubrique illustre cette pratique en développant l’exemple de [à l’aide d’un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="6b2e5-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b2e5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b2e5-105">Example</span></span>  
 <span data-ttu-id="6b2e5-106">L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer les informations de nom de domaine (DNS) pour les ordinateurs spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="6b2e5-107">Cet exemple définit et utilise la `HostRequest` classe pour stocker les informations d’état.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="6b2e5-108">A `HostRequest` objet est créé pour chaque nom d’ordinateur entré par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="6b2e5-109">Cet objet est passé à la <xref:System.Net.Dns.BeginGetHostByName%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6b2e5-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="6b2e5-110">Le `ProcessDnsInformation` méthode est appelée chaque fois une demande est terminée.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="6b2e5-111">Le `HostRequest` objet est récupéré à l’aide de la <xref:System.IAsyncResult.AsyncState%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="6b2e5-112">Le `ProcessDnsInformation` utilise le `HostRequest` objet à stocker le <xref:System.Net.IPHostEntry> retourné par la requête ou un <xref:System.Net.Sockets.SocketException> levé par la demande.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="6b2e5-113">Lorsque toutes les demandes sont terminées, l’application effectue une itération sur la `HostRequest` des objets et affiche les informations DNS ou <xref:System.Net.Sockets.SocketException> message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6b2e5-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6b2e5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2e5-114">See Also</span></span>  
 [<span data-ttu-id="6b2e5-115">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="6b2e5-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="6b2e5-116">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="6b2e5-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="6b2e5-117">Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="6b2e5-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
