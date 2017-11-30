---
title: "Threads de premier plan et d'arrière-plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="4669b-102">Threads de premier plan et d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="4669b-102">Foreground and Background Threads</span></span>
<span data-ttu-id="4669b-103">Un thread managé est un thread d’arrière-plan ou un thread de premier plan.</span><span class="sxs-lookup"><span data-stu-id="4669b-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="4669b-104">Threads d’arrière-plan sont identiques aux threads de premier plan à une exception près : un thread d’arrière-plan ne conserve pas l’environnement d’exécution managé en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4669b-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="4669b-105">Une fois que tous les threads de premier plan ont été arrêtés dans un processus managé (où le fichier .exe est un assembly managé), le système arrête tous les threads d’arrière-plan et s’arrête.</span><span class="sxs-lookup"><span data-stu-id="4669b-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4669b-106">Lorsque le runtime interrompt un thread d’arrière-plan, car le processus est en cours d’arrêt, aucune exception n’est levée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="4669b-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="4669b-107">Toutefois, lorsque les threads sont arrêtés, car le <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> méthode décharge le domaine d’application, un <xref:System.Threading.ThreadAbortException> est levée dans les threads de premier plan et arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4669b-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="4669b-108">Utilisez le <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> propriété pour déterminer si un thread est un thread d’arrière-plan ou au premier plan, ou pour modifier son état.</span><span class="sxs-lookup"><span data-stu-id="4669b-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="4669b-109">Un thread peut être modifié à un thread d’arrière-plan à tout moment en définissant son <xref:System.Threading.Thread.IsBackground%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="4669b-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4669b-110">L’état de premier plan ou d’arrière-plan d’un thread n’affecte pas le résultat d’une exception non gérée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="4669b-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="4669b-111">Dans le .NET Framework version 2.0, une exception non gérée dans les threads de premier plan ou d’arrière-plan entraîne l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="4669b-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="4669b-112">Consultez [Exceptions dans les Threads managés](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="4669b-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="4669b-113">Les threads qui appartiennent au pool de threads managé (autrement dit, les threads dont <xref:System.Threading.Thread.IsThreadPoolThread%2A> propriété `true`) sont des threads d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4669b-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="4669b-114">Tous les threads qui entrent dans l’environnement d’exécution managé à partir de code non managé sont marqués comme threads d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4669b-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="4669b-115">Tous les threads générés en créant et en démarrant un nouvel <xref:System.Threading.Thread> objet sont par défaut des threads de premier plan.</span><span class="sxs-lookup"><span data-stu-id="4669b-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="4669b-116">Si vous utilisez un thread pour contrôler une activité, telle qu’une connexion de socket, définissez son <xref:System.Threading.Thread.IsBackground%2A> propriété `true` afin que le thread n’empêche pas votre processus de s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="4669b-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4669b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4669b-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
