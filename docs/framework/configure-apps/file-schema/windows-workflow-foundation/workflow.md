---
title: '&lt;flux de travail&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55347764e9aa685879eb233793490206c68bf570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowgt"></a><span data-ttu-id="ba3f6-102">&lt;flux de travail&gt;</span><span class="sxs-lookup"><span data-stu-id="ba3f6-102">&lt;workflow&gt;</span></span>
<span data-ttu-id="ba3f6-103">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **un lien hypertexte « http://msdn.microsoft.com/en-us/library/ System.ServiceModel.Activities.Tracking.Configuration.profileworkflowelement.activitydefinitionid (VS.100) .aspx » ctivityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-103">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** property.</span></span>  
  
 <span data-ttu-id="ba3f6-104">Pour plus d’informations dans le suivi de workflow et sa configuration, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ba3f6-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ba3f6-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ba3f6-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-106">\<tracking></span></span>  
<span data-ttu-id="ba3f6-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-107">\<trackingProfile></span></span>  
<span data-ttu-id="ba3f6-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-108">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba3f6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba3f6-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba3f6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ba3f6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ba3f6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba3f6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba3f6-112">Attributes</span></span>  
  
|<span data-ttu-id="ba3f6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ba3f6-113">Attribute</span></span>|<span data-ttu-id="ba3f6-114">Description</span><span class="sxs-lookup"><span data-stu-id="ba3f6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba3f6-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="ba3f6-115">activityDefinitionId</span></span>|<span data-ttu-id="ba3f6-116">Chaîne qui spécifie l'ID de définition de l'activité du flux de travail faisant l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba3f6-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba3f6-117">Child Elements</span></span>  
  
|<span data-ttu-id="ba3f6-118">Élément</span><span class="sxs-lookup"><span data-stu-id="ba3f6-118">Element</span></span>|<span data-ttu-id="ba3f6-119">Description</span><span class="sxs-lookup"><span data-stu-id="ba3f6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba3f6-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-120">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="ba3f6-121">Représente une collection de requêtes qui permettent d’effectuer le suivi d’une activité dont l’exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ba3f6-122">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="ba3f6-123">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-123">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="ba3f6-124">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ba3f6-125">Pouvez par exemple, si vous souhaitez effectuer le suivi de chaque fois que l’activité « Envoyer du courrier électronique » se termine dans une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ba3f6-126">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ba3f6-127">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="ba3f6-128">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-128">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="ba3f6-129">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ba3f6-130">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="ba3f6-131">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-131">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="ba3f6-132">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ba3f6-133">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="ba3f6-134">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-134">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="ba3f6-135">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ba3f6-136">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="ba3f6-137">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-137">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="ba3f6-138">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ba3f6-139">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ba3f6-140">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ba3f6-141">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="ba3f6-142">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-142">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="ba3f6-143">Représente une collection d’éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d’une instance de flux de travail, tels que le début ou la fin d’un événement.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba3f6-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba3f6-144">Parent Elements</span></span>  
  
|<span data-ttu-id="ba3f6-145">Élément</span><span class="sxs-lookup"><span data-stu-id="ba3f6-145">Element</span></span>|<span data-ttu-id="ba3f6-146">Description</span><span class="sxs-lookup"><span data-stu-id="ba3f6-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba3f6-147">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ba3f6-147">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="ba3f6-148">Représente une section de configuration pour la création d’un abonnement pour le suivi des enregistrements dans un participant de suivi de workflow.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="ba3f6-149">Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="ba3f6-150">Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba3f6-151">Remarques</span><span class="sxs-lookup"><span data-stu-id="ba3f6-151">Remarks</span></span>  
 <span data-ttu-id="ba3f6-152">Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail particulière change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="ba3f6-153">L'instance de flux de travail faisant l'objet d'un suivi est identifiée par cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="ba3f6-154">Selon vos spécifications d'analyse, vous pouvez écrire un profil très général, qui s'abonne à un petit jeu de modifications d'état de haut niveau d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="ba3f6-155">Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="ba3f6-156">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="ba3f6-157">Il existe un certain nombre de types de requêtes qui permettent de que vous abonner à différentes classes d’enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="ba3f6-158">Pour obtenir une liste complète des requêtes, consultez la liste d’éléments enfants de cette rubrique et [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ba3f6-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ba3f6-159">L’exemple suivant montre un modèle de suivi dans un fichier de configuration qui permet à un participant de suivi pour vous abonner à la `Started` et `Completed` les événements de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ba3f6-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba3f6-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba3f6-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="ba3f6-161">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ba3f6-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ba3f6-162">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ba3f6-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
