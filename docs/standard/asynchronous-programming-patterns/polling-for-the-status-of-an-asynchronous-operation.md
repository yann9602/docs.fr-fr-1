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
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="21340-102">Interrogation de l'état d'une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="21340-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="21340-103">Les applications qui peuvent effectuer un autre travail en attendant les résultats d’une opération asynchrone ne doivent pas bloquer en attente jusqu'à ce que l’opération se termine.</span><span class="sxs-lookup"><span data-stu-id="21340-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="21340-104">Pour continuer l’exécution des instructions en attendant une opération asynchrone se termine, utilisez une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="21340-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="21340-105">Utilisez le <xref:System.IAsyncResult.IsCompleted%2A> propriété de la <xref:System.IAsyncResult> retourné par l’opération asynchrone **commencer** *NomOpération* méthode pour déterminer si l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="21340-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="21340-106">Cette approche est appelée interrogation et est présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="21340-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="21340-107">Utilisez un <xref:System.AsyncCallback> délégué pour traiter les résultats de l’opération asynchrone dans un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="21340-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="21340-108">Pour obtenir un exemple qui illustre cette approche, consultez [à l’aide d’un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="21340-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21340-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="21340-109">Example</span></span>  
 <span data-ttu-id="21340-110">L’exemple de code suivant illustre l’utilisation de méthodes asynchrones dans la <xref:System.Net.Dns> classe pour récupérer des informations de système de nom de domaine pour un ordinateur spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="21340-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="21340-111">Cet exemple démarre l’opération asynchrone et imprime ensuite des points («. ») au niveau de la console jusqu'à ce que l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="21340-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="21340-112">Notez que **null** (**rien** en Visual Basic) est passée pour le <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> et <xref:System.Object> paramètres car ces arguments ne sont pas requis lors de l’utilisation de cette approche.</span><span class="sxs-lookup"><span data-stu-id="21340-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="21340-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21340-113">See Also</span></span>  
 [<span data-ttu-id="21340-114">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="21340-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="21340-115">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="21340-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
