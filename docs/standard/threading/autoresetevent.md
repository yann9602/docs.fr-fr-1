---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="26c24-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="26c24-102">AutoResetEvent</span></span>
<span data-ttu-id="26c24-103">La <xref:System.Threading.AutoResetEvent> classe représente un événement de handle d’attente local qui se réinitialise automatiquement quand il est signalé, après avoir libéré un seul thread en attente.</span><span class="sxs-lookup"><span data-stu-id="26c24-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="26c24-104">Cette classe représente un cas spécial de sa classe de base, <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="26c24-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="26c24-105">Consultez la documentation conceptuelle de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) relative à l’utilisation et aux fonctionnalités des événements de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="26c24-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="26c24-106">Un <xref:System.Threading.AutoResetEvent> objet est automatiquement réinitialisé à non signalé par le système après la libération d’un seul thread en attente.</span><span class="sxs-lookup"><span data-stu-id="26c24-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="26c24-107">Si aucun thread n’attend, l’état de l’objet d’événement reste signalé.</span><span class="sxs-lookup"><span data-stu-id="26c24-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="26c24-108"><xref:System.Threading.AutoResetEvent>correspond à un Win32 `CreateEvent` appelez, en spécifiant `false` pour la `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="26c24-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="26c24-109">Pour obtenir un exemple qui utilise <xref:System.Threading.AutoResetEvent>, consultez [analyse](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="26c24-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c24-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26c24-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="26c24-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="26c24-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="26c24-112">Thread</span><span class="sxs-lookup"><span data-stu-id="26c24-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="26c24-113">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="26c24-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="26c24-114">Descripteurs d’attente</span><span class="sxs-lookup"><span data-stu-id="26c24-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
