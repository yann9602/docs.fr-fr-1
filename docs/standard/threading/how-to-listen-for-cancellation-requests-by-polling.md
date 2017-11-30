---
title: "Comment : écouter les demandes d'annulation par l'interrogation"
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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="1dd57-102">Comment : écouter les demandes d'annulation par l'interrogation</span><span class="sxs-lookup"><span data-stu-id="1dd57-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="1dd57-103">L’exemple suivant montre une façon de code utilisateur d’interroger un jeton d’annulation à intervalles réguliers pour voir si l’annulation a été demandée à partir du thread appelant.</span><span class="sxs-lookup"><span data-stu-id="1dd57-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="1dd57-104">Cet exemple utilise le <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, mais le même modèle s’applique aux opérations asynchrones créées directement par le <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type ou le <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span><span class="sxs-lookup"><span data-stu-id="1dd57-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dd57-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1dd57-105">Example</span></span>  
 <span data-ttu-id="1dd57-106">L’interrogation requiert un certain genre de boucle ou code récursif qui peut lire régulièrement la valeur de la valeur booléenne <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1dd57-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="1dd57-107">Si vous utilisez la <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et vous sont en attente pour la tâche se termine sur le thread appelant, vous pouvez utiliser la <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> méthode pour vérifier la propriété et lever l’exception.</span><span class="sxs-lookup"><span data-stu-id="1dd57-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="1dd57-108">À l’aide de cette méthode, vous assurez que l’exception correcte est levée en réponse à une demande.</span><span class="sxs-lookup"><span data-stu-id="1dd57-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="1dd57-109">Si vous utilisez un <xref:System.Threading.Tasks.Task>, puis l’appel de cette méthode est préférable à la levée manuellement un <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="1dd57-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="1dd57-110">Si vous n’êtes pas obligé de lever l’exception, vous pouvez simplement vérifier la propriété et le retour de la méthode si la propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="1dd57-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="1dd57-111">Appel de <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> est extrêmement rapide et ne présente pas de surcharge importante dans les boucles.</span><span class="sxs-lookup"><span data-stu-id="1dd57-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="1dd57-112">Si vous appelez <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, vous avez uniquement à vérifier explicitement les <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété si vous avez un autre travail à faire en réponse à l’annulation, en plus de lever l’exception.</span><span class="sxs-lookup"><span data-stu-id="1dd57-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="1dd57-113">Dans cet exemple, vous pouvez voir que le code accède en fait deux fois à la propriété : une fois dans l’accès explicite et à nouveau dans le <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="1dd57-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="1dd57-114">Mais étant donné que l’opération de lecture la <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété implique une seule instruction par accès de lecture volatile, le double accès n’est pas significatif du point de vue des performances.</span><span class="sxs-lookup"><span data-stu-id="1dd57-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="1dd57-115">Il est toujours préférable d’appeler la méthode plutôt que de lever manuellement le <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="1dd57-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd57-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd57-116">See Also</span></span>  
 [<span data-ttu-id="1dd57-117">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="1dd57-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
