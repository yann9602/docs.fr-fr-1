---
title: Minuteries
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a><span data-ttu-id="10c6d-102">Minuteries</span><span class="sxs-lookup"><span data-stu-id="10c6d-102">Timers</span></span>
<span data-ttu-id="10c6d-103">Les minuteurs sont des objets légers qui vous permettent de spécifier un délégué est appelé à une heure spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10c6d-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="10c6d-104">Un thread dans le pool de threads effectue l’opération d’attente.</span><span class="sxs-lookup"><span data-stu-id="10c6d-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="10c6d-105">À l’aide de la <xref:System.Threading.Timer?displayProperty=nameWithType> classe est simple.</span><span class="sxs-lookup"><span data-stu-id="10c6d-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="10c6d-106">Vous créez un **Timer**, en passant un <xref:System.Threading.TimerCallback> délégué à la méthode de rappel, un objet représentant l’état qui sera passé au rappel, un temps de déclenchement initial et un temps représentant l’intervalle entre les appels de rappel.</span><span class="sxs-lookup"><span data-stu-id="10c6d-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="10c6d-107">Pour annuler une minuterie en attente, appelez le **Timer.Dispose** (fonction).</span><span class="sxs-lookup"><span data-stu-id="10c6d-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10c6d-108">Il existe deux autres classes de minuterie.</span><span class="sxs-lookup"><span data-stu-id="10c6d-108">There are two other timer classes.</span></span> <span data-ttu-id="10c6d-109">La <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> classe est un contrôle qui fonctionne avec les concepteurs visuels et est destiné à être utilisé dans des contextes d’interface utilisateur ; il déclenche des événements sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10c6d-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="10c6d-110">Le <xref:System.Timers.Timer?displayProperty=nameWithType> dérive de la classe <xref:System.ComponentModel.Component>, par conséquent, il peut être utilisé avec les concepteurs visuels ; il déclenche également des événements, mais elle déclenche les sur un <xref:System.Threading.ThreadPool> thread.</span><span class="sxs-lookup"><span data-stu-id="10c6d-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="10c6d-111">Le <xref:System.Threading.Timer?displayProperty=nameWithType> classe effectue des rappels sur un <xref:System.Threading.ThreadPool> de thread et n’utilise pas le modèle d’événement du tout.</span><span class="sxs-lookup"><span data-stu-id="10c6d-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="10c6d-112">Il fournit également un objet d’état à la méthode de rappel, qui n’exécutent pas les autres minuteurs.</span><span class="sxs-lookup"><span data-stu-id="10c6d-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="10c6d-113">Il est très légère.</span><span class="sxs-lookup"><span data-stu-id="10c6d-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="10c6d-114">L’exemple de code suivant démarre une minuterie déclenche après une seconde (1000 millisecondes) et marque chaque seconde jusqu'à ce que vous appuyez sur la **entrée** clé.</span><span class="sxs-lookup"><span data-stu-id="10c6d-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="10c6d-115">La variable contenant la référence à la minuterie est un champ de niveau classe, pour vous assurer que le minuteur n’est pas soumis au garbage collection pendant son exécution.</span><span class="sxs-lookup"><span data-stu-id="10c6d-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="10c6d-116">Pour plus d’informations sur un garbage collection agressif, consultez <xref:System.GC.KeepAlive%2A>.</span><span class="sxs-lookup"><span data-stu-id="10c6d-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="10c6d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10c6d-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="10c6d-118">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="10c6d-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
