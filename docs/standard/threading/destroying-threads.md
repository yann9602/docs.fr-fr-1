---
title: Destruction de threads
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
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a><span data-ttu-id="10779-102">Destruction de threads</span><span class="sxs-lookup"><span data-stu-id="10779-102">Destroying Threads</span></span>
<span data-ttu-id="10779-103">Le <xref:System.Threading.Thread.Abort%2A> méthode est utilisée pour arrêter définitivement un thread managé.</span><span class="sxs-lookup"><span data-stu-id="10779-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="10779-104">Lorsque vous appelez <xref:System.Threading.Thread.Abort%2A>, le common language runtime lève une <xref:System.Threading.ThreadAbortException> dans le thread cible, que le thread cible peut intercepter.</span><span class="sxs-lookup"><span data-stu-id="10779-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="10779-105">Pour plus d'informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10779-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10779-106">Si un thread est en cours d’exécution non managée du code lorsque son <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime marque <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10779-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="10779-107">L’exception est levée lorsque le thread retourne au code managé.</span><span class="sxs-lookup"><span data-stu-id="10779-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="10779-108">Une fois qu’un thread est abandonné, il ne peut pas être redémarré.</span><span class="sxs-lookup"><span data-stu-id="10779-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="10779-109">Le <xref:System.Threading.Thread.Abort%2A> méthode n’entraîne pas le thread d’abandonner immédiatement, car le thread cible peut intercepter le <xref:System.Threading.ThreadAbortException> et d’exécution arbitraire de code dans un `finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="10779-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="10779-110">Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous avez besoin d’attendre que le thread s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="10779-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="10779-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>est un appel bloquant qui ne retourne pas jusqu'à ce que le thread est en cours de l’exécution, ou un intervalle de délai d’attente facultatif a expiré.</span><span class="sxs-lookup"><span data-stu-id="10779-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="10779-112">Le thread interrompu pourrait appeler le <xref:System.Threading.Thread.ResetAbort%2A> méthode ou exécuter un traitement illimité dans un `finally` bloquer, donc si vous ne spécifiez pas un délai d’attente, il n’est pas garantie que l’attente de fin.</span><span class="sxs-lookup"><span data-stu-id="10779-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="10779-113">Les threads qui attendent un appel à la <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> méthode peut être interrompue par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10779-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="10779-114">Gestion de ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="10779-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="10779-115">Si vous pensez que votre thread est abandonnée, soit en tant que résultat de l’appel <xref:System.Threading.Thread.Abort%2A> à partir de votre propre code ou à la suite de décharger un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer. le <xref:System.Threading.ThreadAbortException> et d’effectuer un traitement final dans un `finally` clause, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="10779-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="10779-116">Votre code de nettoyage doit être dans le `catch` clause ou le `finally` clause, car un <xref:System.Threading.ThreadAbortException> est à nouveau levée par le système à la fin de la `finally` clause, ou à la fin de la `catch` clause s’il existe aucune `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="10779-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="10779-117">Vous pouvez empêcher le système de nouveau l’exception en appelant le <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="10779-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="10779-118">Toutefois, vous devez effectuer ce uniquement si votre propre code qui a provoqué le <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="10779-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10779-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10779-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="10779-120">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="10779-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
