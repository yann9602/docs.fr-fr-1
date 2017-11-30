---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="c0c70-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="c0c70-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="c0c70-103">Les handles d’attente d’événements permettent aux threads de synchroniser les activités en se signalant et en attendant les signaux des uns et des autres.</span><span class="sxs-lookup"><span data-stu-id="c0c70-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="c0c70-104">Ces événements de synchronisation s’appuient sur des handles d’attente Win32 et se divisent en deux types : ceux qui se réinitialisent automatiquement et ceux qui sont réinitialisés manuellement.</span><span class="sxs-lookup"><span data-stu-id="c0c70-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="c0c70-105">Handles d’attente d’événement sont utiles dans la plupart des scénarios de synchronisation même comme le <xref:System.Threading.Monitor> classe.</span><span class="sxs-lookup"><span data-stu-id="c0c70-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="c0c70-106">Handles d’attente d’événement sont souvent plus faciles à utiliser que les <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> et <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> méthodes et ils offrent davantage de contrôle sur la signalisation.</span><span class="sxs-lookup"><span data-stu-id="c0c70-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="c0c70-107">Les handles d’attente d’événements nommés peuvent également servir à synchroniser les activités entre les différents processus et domaines d’application, tandis que les moniteurs sont liés localement à un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c0c70-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0c70-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c0c70-108">In This Section</span></span>  
 [<span data-ttu-id="c0c70-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="c0c70-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="c0c70-110">La <xref:System.Threading.EventWaitHandle> classe peut représenter soit automatique ou manuel réinitialiser des événements et des événements locaux ou des événements de système nommés.</span><span class="sxs-lookup"><span data-stu-id="c0c70-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="c0c70-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="c0c70-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="c0c70-112">Le <xref:System.Threading.AutoResetEvent> dérive de la classe <xref:System.Threading.EventWaitHandle> et représente un événement local qui se réinitialise automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c0c70-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="c0c70-113">ManualResetEvent and ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="c0c70-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="c0c70-114">Le <xref:System.Threading.ManualResetEvent> dérive de la classe <xref:System.Threading.EventWaitHandle> et représente un événement local qui doit être réinitialisé manuellement.</span><span class="sxs-lookup"><span data-stu-id="c0c70-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="c0c70-115">La <xref:System.Threading.ManualResetEventSlim> classe est une version légère et plus rapide, qui peut être utilisée pour les événements dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="c0c70-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="c0c70-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="c0c70-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="c0c70-117">La <xref:System.Threading.CountdownEvent> classe fournit un moyen simple d’implémenter des modèles de parallélisme de bifurcation/jointure dans le code qui utilise les handles d’attente.</span><span class="sxs-lookup"><span data-stu-id="c0c70-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0c70-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c0c70-118">Related Sections</span></span>  
 [<span data-ttu-id="c0c70-119">Descripteurs d’attente</span><span class="sxs-lookup"><span data-stu-id="c0c70-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="c0c70-120">Le <xref:System.Threading.WaitHandle> est la classe de base pour le <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, et <xref:System.Threading.Mutex> classes.</span><span class="sxs-lookup"><span data-stu-id="c0c70-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="c0c70-121">Il contient des méthodes statiques telles que <xref:System.Threading.WaitHandle.SignalAndWait%2A> et <xref:System.Threading.WaitHandle.WaitAll%2A> qui sont utiles lorsque vous travaillez avec tous les types de handles d’attente.</span><span class="sxs-lookup"><span data-stu-id="c0c70-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c70-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0c70-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="c0c70-123">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="c0c70-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="c0c70-124">Éléments fondamentaux du threading managé</span><span class="sxs-lookup"><span data-stu-id="c0c70-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
