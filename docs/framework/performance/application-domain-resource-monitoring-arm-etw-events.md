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
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="84b78-102">Événements ETW d'analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="84b78-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="84b78-103"><a name="top"></a> Ces événements fournissent des informations de diagnostic détaillées sur l'état d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="84b78-104">Vous pouvez utiliser ces événements ou la fonctionnalité ARM d'analyse de ressource de domaine d'application pour obtenir les mêmes informations.</span><span class="sxs-lookup"><span data-stu-id="84b78-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="84b78-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="84b78-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="84b78-106">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="84b78-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="84b78-107">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="84b78-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="84b78-108">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="84b78-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="84b78-109">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="84b78-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="84b78-110">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="84b78-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="84b78-111">Événement ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="84b78-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="84b78-112">Cet événement est également déclenché sous le fournisseur d'arrêt en tant que `ThreadDC` (sous le mot clé `AppDomainResourceManagementRundownKeyword` ).</span><span class="sxs-lookup"><span data-stu-id="84b78-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="84b78-113">Il s’agit du seul événement déclenché sous le fournisseur d'arrêt dans cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="84b78-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="84b78-114">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="84b78-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="84b78-115">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="84b78-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="84b78-116">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-116">Keyword for raising the event</span></span>|<span data-ttu-id="84b78-117">Niveau</span><span class="sxs-lookup"><span data-stu-id="84b78-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84b78-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="84b78-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="84b78-119">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-119">Informational(4)</span></span>|  
|<span data-ttu-id="84b78-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="84b78-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="84b78-121">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="84b78-122">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84b78-123">Événement</span><span class="sxs-lookup"><span data-stu-id="84b78-123">Event</span></span>|<span data-ttu-id="84b78-124">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-124">Event ID</span></span>|<span data-ttu-id="84b78-125">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="84b78-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="84b78-126">85</span><span class="sxs-lookup"><span data-stu-id="84b78-126">85</span></span>|<span data-ttu-id="84b78-127">Un thread a été créé pour le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="84b78-128">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84b78-129">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="84b78-129">Field name</span></span>|<span data-ttu-id="84b78-130">Type de données</span><span class="sxs-lookup"><span data-stu-id="84b78-130">Data type</span></span>|<span data-ttu-id="84b78-131">Description</span><span class="sxs-lookup"><span data-stu-id="84b78-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84b78-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="84b78-132">ThreadID</span></span>|<span data-ttu-id="84b78-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-133">win:UInt64</span></span>|<span data-ttu-id="84b78-134">ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="84b78-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="84b78-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="84b78-135">AppDomainID</span></span>|<span data-ttu-id="84b78-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-136">win:UInt64</span></span>|<span data-ttu-id="84b78-137">Identificateur du domaine d'application pour lequel l'activité du thread est signalée.</span><span class="sxs-lookup"><span data-stu-id="84b78-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="84b78-138">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="84b78-138">Flags</span></span>|<span data-ttu-id="84b78-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84b78-139">win:UInt32</span></span>|<span data-ttu-id="84b78-140">Indicateurs de création de thread.</span><span class="sxs-lookup"><span data-stu-id="84b78-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="84b78-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="84b78-141">ManagedThreadIndex</span></span>|<span data-ttu-id="84b78-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84b78-142">win:UInt32</span></span>|<span data-ttu-id="84b78-143">Index managé du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="84b78-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="84b78-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="84b78-144">OSThreadID</span></span>|<span data-ttu-id="84b78-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84b78-145">win:UInt32</span></span>|<span data-ttu-id="84b78-146">ID de système d’exploitation du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="84b78-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="84b78-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84b78-147">ClrInstanceID</span></span>|<span data-ttu-id="84b78-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84b78-148">win:UInt16</span></span>|<span data-ttu-id="84b78-149">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84b78-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="84b78-150">Retour au début</span><span class="sxs-lookup"><span data-stu-id="84b78-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="84b78-151">Événement AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="84b78-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="84b78-152">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="84b78-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="84b78-153">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-153">Keyword for raising the event</span></span>|<span data-ttu-id="84b78-154">Niveau</span><span class="sxs-lookup"><span data-stu-id="84b78-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84b78-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="84b78-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="84b78-156">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="84b78-157">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84b78-158">Événement</span><span class="sxs-lookup"><span data-stu-id="84b78-158">Event</span></span>|<span data-ttu-id="84b78-159">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-159">Event ID</span></span>|<span data-ttu-id="84b78-160">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="84b78-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="84b78-161">83</span><span class="sxs-lookup"><span data-stu-id="84b78-161">83</span></span>|<span data-ttu-id="84b78-162">Chaque bloc de 4 Mo de mémoire (environ) est alloué dans le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="84b78-163">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84b78-164">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="84b78-164">Field name</span></span>|<span data-ttu-id="84b78-165">Type de données</span><span class="sxs-lookup"><span data-stu-id="84b78-165">Data type</span></span>|<span data-ttu-id="84b78-166">Description</span><span class="sxs-lookup"><span data-stu-id="84b78-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84b78-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="84b78-167">AppDomainID</span></span>|<span data-ttu-id="84b78-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-168">win:UInt64</span></span>|<span data-ttu-id="84b78-169">Identificateur du domaine d'application pour lequel l'utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="84b78-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="84b78-170">Allocated</span><span class="sxs-lookup"><span data-stu-id="84b78-170">Allocated</span></span>|<span data-ttu-id="84b78-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-171">win:UInt64</span></span>|<span data-ttu-id="84b78-172">Nombre total d'octets alloués dans ce domaine d'application depuis sa création (la quantité de mémoire libérée n'est pas soustraite).</span><span class="sxs-lookup"><span data-stu-id="84b78-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="84b78-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84b78-173">ClrInstanceID</span></span>|<span data-ttu-id="84b78-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84b78-174">win:UInt16</span></span>|<span data-ttu-id="84b78-175">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84b78-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="84b78-176">Retour au début</span><span class="sxs-lookup"><span data-stu-id="84b78-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="84b78-177">Événement AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="84b78-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="84b78-178">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="84b78-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="84b78-179">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-179">Keyword for raising the event</span></span>|<span data-ttu-id="84b78-180">Niveau</span><span class="sxs-lookup"><span data-stu-id="84b78-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84b78-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="84b78-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="84b78-182">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="84b78-183">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84b78-184">Événement</span><span class="sxs-lookup"><span data-stu-id="84b78-184">Event</span></span>|<span data-ttu-id="84b78-185">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-185">Event ID</span></span>|<span data-ttu-id="84b78-186">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="84b78-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="84b78-187">84</span><span class="sxs-lookup"><span data-stu-id="84b78-187">84</span></span>|<span data-ttu-id="84b78-188">Chaque garbage collection est terminé.</span><span class="sxs-lookup"><span data-stu-id="84b78-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="84b78-189">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84b78-190">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="84b78-190">Field name</span></span>|<span data-ttu-id="84b78-191">Type de données</span><span class="sxs-lookup"><span data-stu-id="84b78-191">Data type</span></span>|<span data-ttu-id="84b78-192">Description</span><span class="sxs-lookup"><span data-stu-id="84b78-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84b78-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="84b78-193">AppDomainID</span></span>|<span data-ttu-id="84b78-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-194">win:UInt64</span></span>|<span data-ttu-id="84b78-195">Identificateur du domaine pour lequel l’utilisation des ressources est signalée.</span><span class="sxs-lookup"><span data-stu-id="84b78-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="84b78-196">Survived</span><span class="sxs-lookup"><span data-stu-id="84b78-196">Survived</span></span>|<span data-ttu-id="84b78-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-197">win:UInt64</span></span>|<span data-ttu-id="84b78-198">Nombre d'octets ayant survécu après la dernière collection et qui sont conservés par ce domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="84b78-199">Ce nombre est exact et complet après une collection complète, mais peut être incomplet après une collection éphémère.</span><span class="sxs-lookup"><span data-stu-id="84b78-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="84b78-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="84b78-200">ProcessSurvived</span></span>|<span data-ttu-id="84b78-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-201">win:UInt64</span></span>|<span data-ttu-id="84b78-202">Nombre total d'octets qui ont survécu à la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="84b78-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="84b78-203">Après une collection complète, ce nombre représente le nombre d'octets maintenus actifs dans les tas managés.</span><span class="sxs-lookup"><span data-stu-id="84b78-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="84b78-204">Après une collection éphémère, ce nombre représente le nombre d'octets maintenus actifs dans les générations éphémères.</span><span class="sxs-lookup"><span data-stu-id="84b78-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="84b78-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84b78-205">ClrInstanceID</span></span>|<span data-ttu-id="84b78-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84b78-206">win:UInt16</span></span>|<span data-ttu-id="84b78-207">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84b78-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="84b78-208">Retour au début</span><span class="sxs-lookup"><span data-stu-id="84b78-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="84b78-209">Événement ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="84b78-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="84b78-210">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="84b78-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="84b78-211">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-211">Keyword for raising the event</span></span>|<span data-ttu-id="84b78-212">Niveau</span><span class="sxs-lookup"><span data-stu-id="84b78-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84b78-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="84b78-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="84b78-214">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-214">Informational(4)</span></span>|  
|<span data-ttu-id="84b78-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="84b78-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="84b78-216">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="84b78-217">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84b78-218">Événement</span><span class="sxs-lookup"><span data-stu-id="84b78-218">Event</span></span>|<span data-ttu-id="84b78-219">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-219">Event ID</span></span>|<span data-ttu-id="84b78-220">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="84b78-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="84b78-221">87</span><span class="sxs-lookup"><span data-stu-id="84b78-221">87</span></span>|<span data-ttu-id="84b78-222">Un thread entre dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="84b78-223">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84b78-224">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="84b78-224">Field name</span></span>|<span data-ttu-id="84b78-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="84b78-225">Data type</span></span>|<span data-ttu-id="84b78-226">Description</span><span class="sxs-lookup"><span data-stu-id="84b78-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84b78-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="84b78-227">ThreadID</span></span>|<span data-ttu-id="84b78-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-228">win:UInt64</span></span>|<span data-ttu-id="84b78-229">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="84b78-229">The thread identifier.</span></span>|  
|<span data-ttu-id="84b78-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="84b78-230">AppDomainID</span></span>|<span data-ttu-id="84b78-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-231">win:UInt64</span></span>|<span data-ttu-id="84b78-232">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="84b78-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84b78-233">ClrInstanceID</span></span>|<span data-ttu-id="84b78-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84b78-234">win:UInt16</span></span>|<span data-ttu-id="84b78-235">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84b78-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="84b78-236">Retour au début</span><span class="sxs-lookup"><span data-stu-id="84b78-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="84b78-237">Événement ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="84b78-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="84b78-238">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="84b78-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="84b78-239">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-239">Keyword for raising the event</span></span>|<span data-ttu-id="84b78-240">Niveau</span><span class="sxs-lookup"><span data-stu-id="84b78-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84b78-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="84b78-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="84b78-242">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-242">Informational(4)</span></span>|  
|<span data-ttu-id="84b78-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="84b78-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="84b78-244">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="84b78-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="84b78-245">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84b78-246">Événement</span><span class="sxs-lookup"><span data-stu-id="84b78-246">Event</span></span>|<span data-ttu-id="84b78-247">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84b78-247">Event ID</span></span>|<span data-ttu-id="84b78-248">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="84b78-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="84b78-249">86</span><span class="sxs-lookup"><span data-stu-id="84b78-249">86</span></span>|<span data-ttu-id="84b78-250">Un thread se termine.</span><span class="sxs-lookup"><span data-stu-id="84b78-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="84b78-251">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="84b78-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="84b78-252">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="84b78-252">Field name</span></span>|<span data-ttu-id="84b78-253">Type de données</span><span class="sxs-lookup"><span data-stu-id="84b78-253">Data type</span></span>|<span data-ttu-id="84b78-254">Description</span><span class="sxs-lookup"><span data-stu-id="84b78-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84b78-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="84b78-255">ThreadID</span></span>|<span data-ttu-id="84b78-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-256">win:UInt64</span></span>|<span data-ttu-id="84b78-257">Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="84b78-257">The thread identifier.</span></span>|  
|<span data-ttu-id="84b78-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="84b78-258">AppDomainID</span></span>|<span data-ttu-id="84b78-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="84b78-259">win:UInt64</span></span>|<span data-ttu-id="84b78-260">Identificateur du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="84b78-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="84b78-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84b78-261">ClrInstanceID</span></span>|<span data-ttu-id="84b78-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84b78-262">win:UInt16</span></span>|<span data-ttu-id="84b78-263">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84b78-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84b78-264">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84b78-264">See Also</span></span>  
 [<span data-ttu-id="84b78-265">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="84b78-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
