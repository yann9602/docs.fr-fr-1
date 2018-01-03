---
title: '&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edb6cc424be51e03b3c34182a2b456a9658e2bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="ee279-102">&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ee279-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="ee279-103">Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ee279-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="ee279-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ee279-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="ee279-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ee279-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ee279-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="ee279-106">\<tracking></span></span>  
<span data-ttu-id="ee279-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ee279-107">\<trackingProfile></span></span>  
<span data-ttu-id="ee279-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ee279-108">\<workflow></span></span>  
<span data-ttu-id="ee279-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ee279-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="ee279-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="ee279-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="ee279-111">\<États ></span><span class="sxs-lookup"><span data-stu-id="ee279-111">\<states></span></span>  
<span data-ttu-id="ee279-112">\<état ></span><span class="sxs-lookup"><span data-stu-id="ee279-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee279-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee279-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee279-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee279-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ee279-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee279-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee279-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee279-116">Attributes</span></span>  
  
|<span data-ttu-id="ee279-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee279-117">Attribute</span></span>|<span data-ttu-id="ee279-118">Description</span><span class="sxs-lookup"><span data-stu-id="ee279-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee279-119">name</span><span class="sxs-lookup"><span data-stu-id="ee279-119">name</span></span>|<span data-ttu-id="ee279-120">Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="ee279-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee279-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee279-121">Child Elements</span></span>  
 <span data-ttu-id="ee279-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ee279-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee279-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee279-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ee279-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ee279-124">Element</span></span>|<span data-ttu-id="ee279-125">Description</span><span class="sxs-lookup"><span data-stu-id="ee279-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee279-126">\<États ></span><span class="sxs-lookup"><span data-stu-id="ee279-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="ee279-127">Collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ee279-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee279-128">Notes</span><span class="sxs-lookup"><span data-stu-id="ee279-128">Remarks</span></span>  
 <span data-ttu-id="ee279-129">Les enregistrements retournés sont filtrés par états dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="ee279-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="ee279-130">Les valeurs d'état possibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="ee279-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="ee279-131">État</span><span class="sxs-lookup"><span data-stu-id="ee279-131">State</span></span>|<span data-ttu-id="ee279-132">Description</span><span class="sxs-lookup"><span data-stu-id="ee279-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee279-133">Abandonné</span><span class="sxs-lookup"><span data-stu-id="ee279-133">Aborted</span></span>|<span data-ttu-id="ee279-134">L'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="ee279-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="ee279-135">Terminé</span><span class="sxs-lookup"><span data-stu-id="ee279-135">Completed</span></span>|<span data-ttu-id="ee279-136">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="ee279-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="ee279-137">Supprimé</span><span class="sxs-lookup"><span data-stu-id="ee279-137">Deleted</span></span>|<span data-ttu-id="ee279-138">L'instance de flux de travail est supprimée.</span><span class="sxs-lookup"><span data-stu-id="ee279-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="ee279-139">Inactif</span><span class="sxs-lookup"><span data-stu-id="ee279-139">Idle</span></span>|<span data-ttu-id="ee279-140">L'instance de workflow est inactive.</span><span class="sxs-lookup"><span data-stu-id="ee279-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="ee279-141">Persistant</span><span class="sxs-lookup"><span data-stu-id="ee279-141">Persisted</span></span>|<span data-ttu-id="ee279-142">L'instance de flux de travail est persistante.</span><span class="sxs-lookup"><span data-stu-id="ee279-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="ee279-143">Repris</span><span class="sxs-lookup"><span data-stu-id="ee279-143">Resumed</span></span>|<span data-ttu-id="ee279-144">L'instance de flux de travail est reprise.</span><span class="sxs-lookup"><span data-stu-id="ee279-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="ee279-145">Démarré</span><span class="sxs-lookup"><span data-stu-id="ee279-145">Started</span></span>|<span data-ttu-id="ee279-146">L'instance de flux de travail est démarrée.</span><span class="sxs-lookup"><span data-stu-id="ee279-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="ee279-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="ee279-147">UnhandledException</span></span>|<span data-ttu-id="ee279-148">L'instance de flux de travail a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="ee279-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="ee279-149">Unloaded</span><span class="sxs-lookup"><span data-stu-id="ee279-149">Unloaded</span></span>|<span data-ttu-id="ee279-150">L'instance de flux de travail est déchargée.</span><span class="sxs-lookup"><span data-stu-id="ee279-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="ee279-151">Canceled</span><span class="sxs-lookup"><span data-stu-id="ee279-151">Canceled</span></span>|<span data-ttu-id="ee279-152">L'instance de flux de travail est annulée.</span><span class="sxs-lookup"><span data-stu-id="ee279-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="ee279-153">Interrompu</span><span class="sxs-lookup"><span data-stu-id="ee279-153">Suspended</span></span>|<span data-ttu-id="ee279-154">L'instance de workflow est interrompue.</span><span class="sxs-lookup"><span data-stu-id="ee279-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="ee279-155">Arrêté</span><span class="sxs-lookup"><span data-stu-id="ee279-155">Terminated</span></span>|<span data-ttu-id="ee279-156">L'instance de flux de travail est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="ee279-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="ee279-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="ee279-157">Unsuspended</span></span>|<span data-ttu-id="ee279-158">L'instance de flux de travail est non interrompue.</span><span class="sxs-lookup"><span data-stu-id="ee279-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee279-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee279-159">Example</span></span>  
 <span data-ttu-id="ee279-160">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="ee279-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee279-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee279-161">See Also</span></span>  
 <span data-ttu-id="ee279-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee279-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ee279-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee279-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ee279-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee279-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ee279-165">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ee279-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ee279-166">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ee279-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
