---
title: "Comment : écouter les demandes d'annulation avec des handles d'attente"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="813a9-102">Comment : écouter les demandes d'annulation avec des handles d'attente</span><span class="sxs-lookup"><span data-stu-id="813a9-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="813a9-103">Si une méthode est bloquée lorsqu’elle est en attente d’un événement soit signalé, il ne peut pas vérifier la valeur de jeton d’annulation et répondre en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="813a9-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="813a9-104">Le premier exemple montre comment résoudre ce problème lorsque vous travaillez avec des événements tels que <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> qui ne prennent pas en charge l’infrastructure d’annulation unifiée.</span><span class="sxs-lookup"><span data-stu-id="813a9-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="813a9-105">Le deuxième exemple montre une approche plus simple qui utilise <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, qui prend en charge l’annulation unifiée.</span><span class="sxs-lookup"><span data-stu-id="813a9-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="813a9-106">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="813a9-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="813a9-107">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="813a9-107">This error is benign.</span></span> <span data-ttu-id="813a9-108">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="813a9-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="813a9-109">Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.</span><span class="sxs-lookup"><span data-stu-id="813a9-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="813a9-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="813a9-110">Example</span></span>  
 <span data-ttu-id="813a9-111">L’exemple suivant utilise un <xref:System.Threading.ManualResetEvent> pour montrer comment débloquer des handles d’attente qui ne prennent pas en charge l’annulation unifiée.</span><span class="sxs-lookup"><span data-stu-id="813a9-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="813a9-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="813a9-112">Example</span></span>  
 <span data-ttu-id="813a9-113">L’exemple suivant utilise un <xref:System.Threading.ManualResetEventSlim> pour montrer comment débloquer la coordination primitives qui prennent en charge l’annulation d’unifiée.</span><span class="sxs-lookup"><span data-stu-id="813a9-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="813a9-114">La même approche peut être utilisée avec les autres primitives de coordination simplifiées, telles que <xref:System.Threading.Semaphore> `Slim` et <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="813a9-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="813a9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="813a9-115">See Also</span></span>  
 [<span data-ttu-id="813a9-116">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="813a9-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
