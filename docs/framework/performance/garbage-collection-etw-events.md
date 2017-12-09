---
title: "Événements ETW de garbage collection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="7b94b-102">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="7b94b-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="7b94b-103">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="7b94b-104">Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="7b94b-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="7b94b-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="7b94b-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="7b94b-106">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="7b94b-107">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="7b94b-108">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="7b94b-109">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="7b94b-110">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="7b94b-111">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="7b94b-112">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="7b94b-113">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="7b94b-114">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="7b94b-115">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="7b94b-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="7b94b-116">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="7b94b-117">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="7b94b-118">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="7b94b-119">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="7b94b-120">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="7b94b-121">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="7b94b-122">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="7b94b-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7b94b-123">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-123">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-124">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-126">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-127">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-128">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-128">Event</span></span>|<span data-ttu-id="7b94b-129">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-129">Event ID</span></span>|<span data-ttu-id="7b94b-130">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="7b94b-131">1</span><span class="sxs-lookup"><span data-stu-id="7b94b-131">1</span></span>|<span data-ttu-id="7b94b-132">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="7b94b-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="7b94b-133">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-134">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-134">Field name</span></span>|<span data-ttu-id="7b94b-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-135">Data type</span></span>|<span data-ttu-id="7b94b-136">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-137">Nombre</span><span class="sxs-lookup"><span data-stu-id="7b94b-137">Count</span></span>|<span data-ttu-id="7b94b-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-138">win:UInt32</span></span>|<span data-ttu-id="7b94b-139">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="7b94b-140">Profondeur</span><span class="sxs-lookup"><span data-stu-id="7b94b-140">Depth</span></span>|<span data-ttu-id="7b94b-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-141">win:UInt32</span></span>|<span data-ttu-id="7b94b-142">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="7b94b-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="7b94b-143">Raison</span><span class="sxs-lookup"><span data-stu-id="7b94b-143">Reason</span></span>|<span data-ttu-id="7b94b-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-144">win:UInt32</span></span>|<span data-ttu-id="7b94b-145">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="7b94b-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="7b94b-146">0x0 – Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="7b94b-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="7b94b-147">0x1 – Induit.</span><span class="sxs-lookup"><span data-stu-id="7b94b-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="7b94b-148">0x2 – Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="7b94b-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="7b94b-149">0x3 – Vide.</span><span class="sxs-lookup"><span data-stu-id="7b94b-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="7b94b-150">0x4 – Allocation de tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="7b94b-151">0x5 – Espace insuffisant (pour un tas de petits objets)</span><span class="sxs-lookup"><span data-stu-id="7b94b-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="7b94b-152">0x6 – Espace insuffisant (pour un tas d'objets volumineux)</span><span class="sxs-lookup"><span data-stu-id="7b94b-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="7b94b-153">0x7 – Induit mais non forcé comme blocage</span><span class="sxs-lookup"><span data-stu-id="7b94b-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="7b94b-154">Type</span><span class="sxs-lookup"><span data-stu-id="7b94b-154">Type</span></span>|<span data-ttu-id="7b94b-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-155">win:UInt32</span></span>|<span data-ttu-id="7b94b-156">0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7b94b-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="7b94b-157">0x1 – Garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7b94b-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="7b94b-158">0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7b94b-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="7b94b-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-159">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-160">win:UInt16</span></span>|<span data-ttu-id="7b94b-161">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-162">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="7b94b-163">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="7b94b-164">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-165">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-165">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-166">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-168">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-169">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-170">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-170">Event</span></span>|<span data-ttu-id="7b94b-171">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-171">Event ID</span></span>|<span data-ttu-id="7b94b-172">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="7b94b-173">2</span><span class="sxs-lookup"><span data-stu-id="7b94b-173">2</span></span>|<span data-ttu-id="7b94b-174">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="7b94b-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="7b94b-175">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-176">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-176">Field name</span></span>|<span data-ttu-id="7b94b-177">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-177">Data type</span></span>|<span data-ttu-id="7b94b-178">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-179">Nombre</span><span class="sxs-lookup"><span data-stu-id="7b94b-179">Count</span></span>|<span data-ttu-id="7b94b-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-180">win:UInt32</span></span>|<span data-ttu-id="7b94b-181">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="7b94b-182">Profondeur</span><span class="sxs-lookup"><span data-stu-id="7b94b-182">Depth</span></span>|<span data-ttu-id="7b94b-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-183">win:UInt32</span></span>|<span data-ttu-id="7b94b-184">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="7b94b-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="7b94b-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-185">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-186">win:UInt16</span></span>|<span data-ttu-id="7b94b-187">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-188">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="7b94b-189">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="7b94b-190">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-191">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-191">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-192">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-194">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-195">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-196">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-196">Event</span></span>|<span data-ttu-id="7b94b-197">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-197">Event ID</span></span>|<span data-ttu-id="7b94b-198">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="7b94b-199">4</span><span class="sxs-lookup"><span data-stu-id="7b94b-199">4</span></span>|<span data-ttu-id="7b94b-200">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="7b94b-201">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-202">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-202">Field name</span></span>|<span data-ttu-id="7b94b-203">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-203">Data type</span></span>|<span data-ttu-id="7b94b-204">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="7b94b-205">GenerationSize0</span></span>|<span data-ttu-id="7b94b-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-206">win:UInt64</span></span>|<span data-ttu-id="7b94b-207">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="7b94b-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="7b94b-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="7b94b-208">TotalPromotedSize0</span></span>|<span data-ttu-id="7b94b-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-209">win:UInt64</span></span>|<span data-ttu-id="7b94b-210">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="7b94b-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="7b94b-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="7b94b-211">GenerationSize1</span></span>|<span data-ttu-id="7b94b-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-212">win:UInt64</span></span>|<span data-ttu-id="7b94b-213">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="7b94b-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="7b94b-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="7b94b-214">TotalPromotedSize1</span></span>|<span data-ttu-id="7b94b-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-215">win:UInt64</span></span>|<span data-ttu-id="7b94b-216">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="7b94b-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="7b94b-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="7b94b-217">GenerationSize2</span></span>|<span data-ttu-id="7b94b-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-218">win:UInt64</span></span>|<span data-ttu-id="7b94b-219">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="7b94b-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="7b94b-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="7b94b-220">TotalPromotedSize2</span></span>|<span data-ttu-id="7b94b-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-221">win:UInt64</span></span>|<span data-ttu-id="7b94b-222">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="7b94b-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="7b94b-223">GenerationSize3</span></span>|<span data-ttu-id="7b94b-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-224">win:UInt64</span></span>|<span data-ttu-id="7b94b-225">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="7b94b-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="7b94b-226">TotalPromotedSize3</span></span>|<span data-ttu-id="7b94b-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-227">win:UInt64</span></span>|<span data-ttu-id="7b94b-228">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="7b94b-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="7b94b-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="7b94b-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-230">win:UInt64</span></span>|<span data-ttu-id="7b94b-231">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="7b94b-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="7b94b-232">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="7b94b-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="7b94b-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-233">win:UInt64</span></span>|<span data-ttu-id="7b94b-234">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="7b94b-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="7b94b-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="7b94b-235">PinnedObjectCount</span></span>|<span data-ttu-id="7b94b-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-236">win:UInt32</span></span>|<span data-ttu-id="7b94b-237">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="7b94b-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="7b94b-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="7b94b-238">SinkBlockCount</span></span>|<span data-ttu-id="7b94b-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-239">win:UInt32</span></span>|<span data-ttu-id="7b94b-240">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="7b94b-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="7b94b-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="7b94b-241">GCHandleCount</span></span>|<span data-ttu-id="7b94b-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-242">win:UInt32</span></span>|<span data-ttu-id="7b94b-243">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="7b94b-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="7b94b-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-244">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-245">win:UInt16</span></span>|<span data-ttu-id="7b94b-246">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-247">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="7b94b-248">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="7b94b-249">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-250">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-250">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-251">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-253">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-254">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-255">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-255">Event</span></span>|<span data-ttu-id="7b94b-256">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-256">Event ID</span></span>|<span data-ttu-id="7b94b-257">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="7b94b-258">5</span><span class="sxs-lookup"><span data-stu-id="7b94b-258">5</span></span>|<span data-ttu-id="7b94b-259">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="7b94b-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="7b94b-260">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="7b94b-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="7b94b-261">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-262">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-262">Field name</span></span>|<span data-ttu-id="7b94b-263">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-263">Data type</span></span>|<span data-ttu-id="7b94b-264">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-265">Adresse</span><span class="sxs-lookup"><span data-stu-id="7b94b-265">Address</span></span>|<span data-ttu-id="7b94b-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-266">win:UInt64</span></span>|<span data-ttu-id="7b94b-267">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="7b94b-267">The address of the segment.</span></span>|  
|<span data-ttu-id="7b94b-268">Taille</span><span class="sxs-lookup"><span data-stu-id="7b94b-268">Size</span></span>|<span data-ttu-id="7b94b-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-269">win:UInt64</span></span>|<span data-ttu-id="7b94b-270">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="7b94b-270">The size of the segment.</span></span>|  
|<span data-ttu-id="7b94b-271">Type</span><span class="sxs-lookup"><span data-stu-id="7b94b-271">Type</span></span>|<span data-ttu-id="7b94b-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-272">win:UInt32</span></span>|<span data-ttu-id="7b94b-273">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="7b94b-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="7b94b-274">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="7b94b-275">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="7b94b-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="7b94b-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-276">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-277">win:UInt16</span></span>|<span data-ttu-id="7b94b-278">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="7b94b-279">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="7b94b-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="7b94b-280">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="7b94b-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="7b94b-281">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="7b94b-282">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="7b94b-283">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-284">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-284">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-285">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-287">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-288">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-289">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-289">Event</span></span>|<span data-ttu-id="7b94b-290">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-290">Event ID</span></span>|<span data-ttu-id="7b94b-291">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="7b94b-292">6</span><span class="sxs-lookup"><span data-stu-id="7b94b-292">6</span></span>|<span data-ttu-id="7b94b-293">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="7b94b-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="7b94b-294">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-295">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-295">Field name</span></span>|<span data-ttu-id="7b94b-296">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-296">Data type</span></span>|<span data-ttu-id="7b94b-297">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-298">Adresse</span><span class="sxs-lookup"><span data-stu-id="7b94b-298">Address</span></span>|<span data-ttu-id="7b94b-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-299">win:UInt64</span></span>|<span data-ttu-id="7b94b-300">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="7b94b-300">The address of the segment.</span></span>|  
|<span data-ttu-id="7b94b-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-301">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-302">win:UInt16</span></span>|<span data-ttu-id="7b94b-303">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-304">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="7b94b-305">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="7b94b-306">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-307">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-307">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-308">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-310">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-311">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-312">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-312">Event</span></span>|<span data-ttu-id="7b94b-313">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-313">Event ID</span></span>|<span data-ttu-id="7b94b-314">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="7b94b-315">7</span><span class="sxs-lookup"><span data-stu-id="7b94b-315">7</span></span>|<span data-ttu-id="7b94b-316">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="7b94b-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="7b94b-317">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-317">No event data.</span></span>  
  
 [<span data-ttu-id="7b94b-318">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="7b94b-319">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="7b94b-320">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-321">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-321">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-322">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-324">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-325">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-326">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-326">Event</span></span>|<span data-ttu-id="7b94b-327">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-327">Event Id</span></span>|<span data-ttu-id="7b94b-328">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="7b94b-329">3</span><span class="sxs-lookup"><span data-stu-id="7b94b-329">3</span></span>|<span data-ttu-id="7b94b-330">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="7b94b-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="7b94b-331">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-331">No event data.</span></span>  
  
 [<span data-ttu-id="7b94b-332">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="7b94b-333">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="7b94b-334">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-335">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-335">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-336">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-338">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-339">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-340">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-340">Event</span></span>|<span data-ttu-id="7b94b-341">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-341">Event ID</span></span>|<span data-ttu-id="7b94b-342">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="7b94b-343">9</span><span class="sxs-lookup"><span data-stu-id="7b94b-343">9</span></span>|<span data-ttu-id="7b94b-344">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="7b94b-345">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-346">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-346">Field name</span></span>|<span data-ttu-id="7b94b-347">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-347">Data type</span></span>|<span data-ttu-id="7b94b-348">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-349">Raison</span><span class="sxs-lookup"><span data-stu-id="7b94b-349">Reason</span></span>|<span data-ttu-id="7b94b-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-350">win:UInt16</span></span>|<span data-ttu-id="7b94b-351">0x0 – Autre.</span><span class="sxs-lookup"><span data-stu-id="7b94b-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="7b94b-352">0x1 – Garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="7b94b-353">0x2 – Fermeture du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="7b94b-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="7b94b-354">0x3 – Pitching de code.</span><span class="sxs-lookup"><span data-stu-id="7b94b-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="7b94b-355">0x4 – Arrêt.</span><span class="sxs-lookup"><span data-stu-id="7b94b-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="7b94b-356">0x5 – Débogueur.</span><span class="sxs-lookup"><span data-stu-id="7b94b-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="7b94b-357">0x6 – Préparation pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="7b94b-358">Nombre</span><span class="sxs-lookup"><span data-stu-id="7b94b-358">Count</span></span>|<span data-ttu-id="7b94b-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-359">win:UInt32</span></span>|<span data-ttu-id="7b94b-360">Nombre GC à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="7b94b-360">The GC count at the time.</span></span> <span data-ttu-id="7b94b-361">En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="7b94b-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-362">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-363">win:UInt16</span></span>|<span data-ttu-id="7b94b-364">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-365">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="7b94b-366">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="7b94b-367">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="7b94b-368">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-368">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-369">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-371">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-372">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="7b94b-373">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-373">Event</span></span>|<span data-ttu-id="7b94b-374">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-374">Event ID</span></span>|<span data-ttu-id="7b94b-375">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="7b94b-376">8</span><span class="sxs-lookup"><span data-stu-id="7b94b-376">8</span></span>|<span data-ttu-id="7b94b-377">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7b94b-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="7b94b-378">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-378">No event data.</span></span>  
  
 [<span data-ttu-id="7b94b-379">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="7b94b-380">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="7b94b-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="7b94b-381">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-382">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-382">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-383">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-385">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-386">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-387">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-387">Event</span></span>|<span data-ttu-id="7b94b-388">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-388">Event ID</span></span>|<span data-ttu-id="7b94b-389">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="7b94b-390">10</span><span class="sxs-lookup"><span data-stu-id="7b94b-390">10</span></span>|<span data-ttu-id="7b94b-391">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="7b94b-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="7b94b-392">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-393">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-393">Field name</span></span>|<span data-ttu-id="7b94b-394">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-394">Data type</span></span>|<span data-ttu-id="7b94b-395">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="7b94b-396">AllocationAmount</span></span>|<span data-ttu-id="7b94b-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-397">win:UInt32</span></span>|<span data-ttu-id="7b94b-398">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="7b94b-398">The allocation size, in bytes.</span></span> <span data-ttu-id="7b94b-399">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="7b94b-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="7b94b-400">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="7b94b-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="7b94b-401">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="7b94b-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="7b94b-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="7b94b-402">AllocationKind</span></span>|<span data-ttu-id="7b94b-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-403">win:UInt32</span></span>|<span data-ttu-id="7b94b-404">0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="7b94b-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="7b94b-405">0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="7b94b-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="7b94b-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-406">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-407">win:UInt16</span></span>|<span data-ttu-id="7b94b-408">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="7b94b-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="7b94b-409">AllocationAmount64</span></span>|<span data-ttu-id="7b94b-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7b94b-410">win:UInt64</span></span>|<span data-ttu-id="7b94b-411">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="7b94b-411">The allocation size, in bytes.</span></span> <span data-ttu-id="7b94b-412">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="7b94b-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="7b94b-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="7b94b-413">TypeId</span></span>|<span data-ttu-id="7b94b-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="7b94b-414">win:Pointer</span></span>|<span data-ttu-id="7b94b-415">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="7b94b-415">The address of the MethodTable.</span></span> <span data-ttu-id="7b94b-416">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="7b94b-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="7b94b-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="7b94b-417">TypeName</span></span>|<span data-ttu-id="7b94b-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7b94b-418">win:UnicodeString</span></span>|<span data-ttu-id="7b94b-419">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="7b94b-419">The name of the type that was allocated.</span></span> <span data-ttu-id="7b94b-420">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="7b94b-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="7b94b-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="7b94b-421">HeapIndex</span></span>|<span data-ttu-id="7b94b-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-422">win:UInt32</span></span>|<span data-ttu-id="7b94b-423">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="7b94b-423">The heap where the object was allocated.</span></span> <span data-ttu-id="7b94b-424">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="7b94b-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="7b94b-425">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="7b94b-426">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="7b94b-427">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-428">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-428">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-429">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-431">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-432">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-433">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-433">Event</span></span>|<span data-ttu-id="7b94b-434">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-434">Event ID</span></span>|<span data-ttu-id="7b94b-435">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="7b94b-436">14</span><span class="sxs-lookup"><span data-stu-id="7b94b-436">14</span></span>|<span data-ttu-id="7b94b-437">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="7b94b-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="7b94b-438">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-438">No event data.</span></span>  
  
 [<span data-ttu-id="7b94b-439">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="7b94b-440">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="7b94b-441">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-442">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-442">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-443">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-445">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-446">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-447">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-447">Event</span></span>|<span data-ttu-id="7b94b-448">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-448">Event ID</span></span>|<span data-ttu-id="7b94b-449">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="7b94b-450">13</span><span class="sxs-lookup"><span data-stu-id="7b94b-450">13</span></span>|<span data-ttu-id="7b94b-451">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="7b94b-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="7b94b-452">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7b94b-453">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="7b94b-453">Field name</span></span>|<span data-ttu-id="7b94b-454">Type de données</span><span class="sxs-lookup"><span data-stu-id="7b94b-454">Data type</span></span>|<span data-ttu-id="7b94b-455">Description</span><span class="sxs-lookup"><span data-stu-id="7b94b-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7b94b-456">Nombre</span><span class="sxs-lookup"><span data-stu-id="7b94b-456">Count</span></span>|<span data-ttu-id="7b94b-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7b94b-457">win:UInt32</span></span>|<span data-ttu-id="7b94b-458">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="7b94b-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="7b94b-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7b94b-459">ClrInstanceID</span></span>|<span data-ttu-id="7b94b-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7b94b-460">win:UInt16</span></span>|<span data-ttu-id="7b94b-461">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7b94b-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7b94b-462">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="7b94b-463">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="7b94b-464">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-465">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-465">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-466">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-468">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-468">Informational (4)</span></span>|  
|<span data-ttu-id="7b94b-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7b94b-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7b94b-470">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-471">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-472">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-472">Event</span></span>|<span data-ttu-id="7b94b-473">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-473">Event ID</span></span>|<span data-ttu-id="7b94b-474">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="7b94b-475">11</span><span class="sxs-lookup"><span data-stu-id="7b94b-475">11</span></span>|<span data-ttu-id="7b94b-476">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="7b94b-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="7b94b-477">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-477">No event data.</span></span>  
  
 [<span data-ttu-id="7b94b-478">Retour au début</span><span class="sxs-lookup"><span data-stu-id="7b94b-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="7b94b-479">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="7b94b-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="7b94b-480">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="7b94b-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7b94b-481">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-481">Keyword for raising the event</span></span>|<span data-ttu-id="7b94b-482">Niveau</span><span class="sxs-lookup"><span data-stu-id="7b94b-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7b94b-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="7b94b-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7b94b-484">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-484">Informational (4)</span></span>|  
|<span data-ttu-id="7b94b-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7b94b-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7b94b-486">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="7b94b-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="7b94b-487">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="7b94b-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7b94b-488">Événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-488">Event</span></span>|<span data-ttu-id="7b94b-489">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b94b-489">Event ID</span></span>|<span data-ttu-id="7b94b-490">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="7b94b-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="7b94b-491">12</span><span class="sxs-lookup"><span data-stu-id="7b94b-491">12</span></span>|<span data-ttu-id="7b94b-492">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="7b94b-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="7b94b-493">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="7b94b-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b94b-494">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b94b-494">See Also</span></span>  
 [<span data-ttu-id="7b94b-495">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="7b94b-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
