---
title: "Événements ETW d'analyse de ressource de domaine d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="d1813-102">Événements ETW d'analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="d1813-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="d1813-103">Ces événements fournissent des informations de diagnostic détaillées sur l'état d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="d1813-104">Vous pouvez utiliser ces événements ou la fonctionnalité ARM d'analyse de ressource de domaine d'application pour obtenir les mêmes informations.</span><span class="sxs-lookup"><span data-stu-id="d1813-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="d1813-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="d1813-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="d1813-106">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="d1813-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="d1813-107">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="d1813-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="d1813-108">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="d1813-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="d1813-109">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="d1813-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="d1813-110">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="d1813-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="d1813-111">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="d1813-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="d1813-112">Cet événement est également déclenché sous le fournisseur d'arrêt en tant que `ThreadDC` (sous le mot clé `AppDomainResourceManagementRundownKeyword` ).</span><span class="sxs-lookup"><span data-stu-id="d1813-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="d1813-113">Il s’agit du seul événement déclenché sous le fournisseur d'arrêt dans cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="d1813-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="d1813-114">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d1813-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="d1813-115">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d1813-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d1813-116">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-116">Keyword for raising the event</span></span>|<span data-ttu-id="d1813-117">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1813-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1813-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="d1813-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d1813-119">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-119">Informational(4)</span></span>|  
|<span data-ttu-id="d1813-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d1813-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d1813-121">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1813-122">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1813-123">Événement</span><span class="sxs-lookup"><span data-stu-id="d1813-123">Event</span></span>|<span data-ttu-id="d1813-124">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-124">Event ID</span></span>|<span data-ttu-id="d1813-125">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d1813-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="d1813-126">85</span><span class="sxs-lookup"><span data-stu-id="d1813-126">85</span></span>|<span data-ttu-id="d1813-127">Un thread a été créé pour le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="d1813-128">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1813-129">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="d1813-129">Field name</span></span>|<span data-ttu-id="d1813-130">Type de données</span><span class="sxs-lookup"><span data-stu-id="d1813-130">Data type</span></span>|<span data-ttu-id="d1813-131">Description</span><span class="sxs-lookup"><span data-stu-id="d1813-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1813-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d1813-132">ThreadID</span></span>|<span data-ttu-id="d1813-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-133">win:UInt64</span></span>|<span data-ttu-id="d1813-134">ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="d1813-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="d1813-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d1813-135">AppDomainID</span></span>|<span data-ttu-id="d1813-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-136">win:UInt64</span></span>|<span data-ttu-id="d1813-137">Identificateur du domaine d'application pour lequel l'activité du thread est signalée.</span><span class="sxs-lookup"><span data-stu-id="d1813-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="d1813-138">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="d1813-138">Flags</span></span>|<span data-ttu-id="d1813-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d1813-139">win:UInt32</span></span>|<span data-ttu-id="d1813-140">Indicateurs de création de thread.</span><span class="sxs-lookup"><span data-stu-id="d1813-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="d1813-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="d1813-141">ManagedThreadIndex</span></span>|<span data-ttu-id="d1813-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d1813-142">win:UInt32</span></span>|<span data-ttu-id="d1813-143">Index managé du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="d1813-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="d1813-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="d1813-144">OSThreadID</span></span>|<span data-ttu-id="d1813-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d1813-145">win:UInt32</span></span>|<span data-ttu-id="d1813-146">ID de système d’exploitation du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="d1813-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="d1813-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1813-147">ClrInstanceID</span></span>|<span data-ttu-id="d1813-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d1813-148">win:UInt16</span></span>|<span data-ttu-id="d1813-149">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1813-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1813-150">Retour au début</span><span class="sxs-lookup"><span data-stu-id="d1813-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="d1813-151">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="d1813-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="d1813-152">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d1813-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d1813-153">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-153">Keyword for raising the event</span></span>|<span data-ttu-id="d1813-154">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1813-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1813-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="d1813-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d1813-156">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1813-157">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1813-158">Événement</span><span class="sxs-lookup"><span data-stu-id="d1813-158">Event</span></span>|<span data-ttu-id="d1813-159">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-159">Event ID</span></span>|<span data-ttu-id="d1813-160">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d1813-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="d1813-161">83</span><span class="sxs-lookup"><span data-stu-id="d1813-161">83</span></span>|<span data-ttu-id="d1813-162">Chaque bloc de 4 Mo de mémoire (environ) est alloué dans le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="d1813-163">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1813-164">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="d1813-164">Field name</span></span>|<span data-ttu-id="d1813-165">Type de données</span><span class="sxs-lookup"><span data-stu-id="d1813-165">Data type</span></span>|<span data-ttu-id="d1813-166">Description</span><span class="sxs-lookup"><span data-stu-id="d1813-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1813-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d1813-167">AppDomainID</span></span>|<span data-ttu-id="d1813-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-168">win:UInt64</span></span>|<span data-ttu-id="d1813-169">Identificateur du domaine d'application pour lequel l'utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="d1813-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="d1813-170">Allocated</span><span class="sxs-lookup"><span data-stu-id="d1813-170">Allocated</span></span>|<span data-ttu-id="d1813-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-171">win:UInt64</span></span>|<span data-ttu-id="d1813-172">Nombre total d'octets alloués dans ce domaine d'application depuis sa création (la quantité de mémoire libérée n'est pas soustraite).</span><span class="sxs-lookup"><span data-stu-id="d1813-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="d1813-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1813-173">ClrInstanceID</span></span>|<span data-ttu-id="d1813-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d1813-174">win:UInt16</span></span>|<span data-ttu-id="d1813-175">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1813-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1813-176">Retour au début</span><span class="sxs-lookup"><span data-stu-id="d1813-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="d1813-177">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="d1813-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="d1813-178">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d1813-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d1813-179">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-179">Keyword for raising the event</span></span>|<span data-ttu-id="d1813-180">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1813-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1813-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="d1813-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d1813-182">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1813-183">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1813-184">Événement</span><span class="sxs-lookup"><span data-stu-id="d1813-184">Event</span></span>|<span data-ttu-id="d1813-185">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-185">Event ID</span></span>|<span data-ttu-id="d1813-186">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d1813-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="d1813-187">84</span><span class="sxs-lookup"><span data-stu-id="d1813-187">84</span></span>|<span data-ttu-id="d1813-188">Chaque garbage collection est terminé.</span><span class="sxs-lookup"><span data-stu-id="d1813-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="d1813-189">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1813-190">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="d1813-190">Field name</span></span>|<span data-ttu-id="d1813-191">Type de données</span><span class="sxs-lookup"><span data-stu-id="d1813-191">Data type</span></span>|<span data-ttu-id="d1813-192">Description</span><span class="sxs-lookup"><span data-stu-id="d1813-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1813-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d1813-193">AppDomainID</span></span>|<span data-ttu-id="d1813-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-194">win:UInt64</span></span>|<span data-ttu-id="d1813-195">Identificateur du domaine pour lequel l’utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="d1813-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="d1813-196">Survived</span><span class="sxs-lookup"><span data-stu-id="d1813-196">Survived</span></span>|<span data-ttu-id="d1813-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-197">win:UInt64</span></span>|<span data-ttu-id="d1813-198">Nombre d'octets ayant survécu après la dernière collection et qui sont conservés par ce domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="d1813-199">Ce nombre est exact et complet après une collection complète, mais peut être incomplet après une collection éphémère.</span><span class="sxs-lookup"><span data-stu-id="d1813-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="d1813-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="d1813-200">ProcessSurvived</span></span>|<span data-ttu-id="d1813-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-201">win:UInt64</span></span>|<span data-ttu-id="d1813-202">Nombre total d'octets qui ont survécu à la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="d1813-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="d1813-203">Après une collection complète, ce nombre représente le nombre d'octets maintenus actifs dans les tas managés.</span><span class="sxs-lookup"><span data-stu-id="d1813-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="d1813-204">Après une collection éphémère, ce nombre représente le nombre d'octets maintenus actifs dans les générations éphémères.</span><span class="sxs-lookup"><span data-stu-id="d1813-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="d1813-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1813-205">ClrInstanceID</span></span>|<span data-ttu-id="d1813-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d1813-206">win:UInt16</span></span>|<span data-ttu-id="d1813-207">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1813-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1813-208">Retour au début</span><span class="sxs-lookup"><span data-stu-id="d1813-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="d1813-209">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="d1813-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="d1813-210">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d1813-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d1813-211">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-211">Keyword for raising the event</span></span>|<span data-ttu-id="d1813-212">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1813-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1813-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="d1813-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d1813-214">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-214">Informational(4)</span></span>|  
|<span data-ttu-id="d1813-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d1813-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d1813-216">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1813-217">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1813-218">Événement</span><span class="sxs-lookup"><span data-stu-id="d1813-218">Event</span></span>|<span data-ttu-id="d1813-219">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-219">Event ID</span></span>|<span data-ttu-id="d1813-220">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d1813-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="d1813-221">87</span><span class="sxs-lookup"><span data-stu-id="d1813-221">87</span></span>|<span data-ttu-id="d1813-222">Un thread entre dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="d1813-223">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d1813-224">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="d1813-224">Field name</span></span>|<span data-ttu-id="d1813-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="d1813-225">Data type</span></span>|<span data-ttu-id="d1813-226">Description</span><span class="sxs-lookup"><span data-stu-id="d1813-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1813-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d1813-227">ThreadID</span></span>|<span data-ttu-id="d1813-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-228">win:UInt64</span></span>|<span data-ttu-id="d1813-229">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="d1813-229">The thread identifier.</span></span>|  
|<span data-ttu-id="d1813-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d1813-230">AppDomainID</span></span>|<span data-ttu-id="d1813-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-231">win:UInt64</span></span>|<span data-ttu-id="d1813-232">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="d1813-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1813-233">ClrInstanceID</span></span>|<span data-ttu-id="d1813-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d1813-234">win:UInt16</span></span>|<span data-ttu-id="d1813-235">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1813-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d1813-236">Retour au début</span><span class="sxs-lookup"><span data-stu-id="d1813-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="d1813-237">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="d1813-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="d1813-238">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="d1813-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d1813-239">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-239">Keyword for raising the event</span></span>|<span data-ttu-id="d1813-240">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1813-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d1813-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="d1813-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d1813-242">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-242">Informational(4)</span></span>|  
|<span data-ttu-id="d1813-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d1813-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d1813-244">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="d1813-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="d1813-245">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d1813-246">Événement</span><span class="sxs-lookup"><span data-stu-id="d1813-246">Event</span></span>|<span data-ttu-id="d1813-247">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d1813-247">Event ID</span></span>|<span data-ttu-id="d1813-248">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="d1813-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="d1813-249">86</span><span class="sxs-lookup"><span data-stu-id="d1813-249">86</span></span>|<span data-ttu-id="d1813-250">Un thread se termine.</span><span class="sxs-lookup"><span data-stu-id="d1813-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="d1813-251">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="d1813-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="d1813-252">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="d1813-252">Field name</span></span>|<span data-ttu-id="d1813-253">Type de données</span><span class="sxs-lookup"><span data-stu-id="d1813-253">Data type</span></span>|<span data-ttu-id="d1813-254">Description</span><span class="sxs-lookup"><span data-stu-id="d1813-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d1813-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d1813-255">ThreadID</span></span>|<span data-ttu-id="d1813-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-256">win:UInt64</span></span>|<span data-ttu-id="d1813-257">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="d1813-257">The thread identifier.</span></span>|  
|<span data-ttu-id="d1813-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d1813-258">AppDomainID</span></span>|<span data-ttu-id="d1813-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d1813-259">win:UInt64</span></span>|<span data-ttu-id="d1813-260">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="d1813-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="d1813-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d1813-261">ClrInstanceID</span></span>|<span data-ttu-id="d1813-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d1813-262">win:UInt16</span></span>|<span data-ttu-id="d1813-263">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d1813-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1813-264">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1813-264">See Also</span></span>  
 [<span data-ttu-id="d1813-265">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="d1813-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
