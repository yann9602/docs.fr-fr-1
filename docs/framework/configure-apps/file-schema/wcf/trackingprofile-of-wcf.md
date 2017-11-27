---
title: '&lt;trackingProfile&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a4c317a4fcf4efb2f1b8210faa768cc290a784c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="e75fc-102">&lt;trackingProfile&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="e75fc-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="e75fc-103">Représente une section de configuration pour la création d’un abonnement pour le suivi des enregistrements dans un participant de suivi de workflow.</span><span class="sxs-lookup"><span data-stu-id="e75fc-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="e75fc-104">Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e75fc-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e75fc-105">Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="e75fc-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="e75fc-106">Pour plus d’informations dans le suivi de workflow et sa configuration, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e75fc-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="e75fc-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e75fc-107">\<system.serviceModel></span></span>  
<span data-ttu-id="e75fc-108">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="e75fc-108">\<tracking></span></span>  
<span data-ttu-id="e75fc-109">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e75fc-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75fc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e75fc-110">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>      <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>    
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e75fc-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e75fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e75fc-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e75fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e75fc-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e75fc-113">Attributes</span></span>  
  
|<span data-ttu-id="e75fc-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e75fc-114">Attribute</span></span>|<span data-ttu-id="e75fc-115">Description</span><span class="sxs-lookup"><span data-stu-id="e75fc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e75fc-116">name</span><span class="sxs-lookup"><span data-stu-id="e75fc-116">name</span></span>|<span data-ttu-id="e75fc-117">Chaîne qui spécifie le nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="e75fc-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e75fc-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e75fc-118">Child Elements</span></span>  
  
|<span data-ttu-id="e75fc-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e75fc-119">Element</span></span>|<span data-ttu-id="e75fc-120">Description</span><span class="sxs-lookup"><span data-stu-id="e75fc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e75fc-121">\<participants ></span><span class="sxs-lookup"><span data-stu-id="e75fc-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="e75fc-122">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="e75fc-122">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e75fc-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e75fc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e75fc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e75fc-124">Element</span></span>|<span data-ttu-id="e75fc-125">Description</span><span class="sxs-lookup"><span data-stu-id="e75fc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e75fc-126">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="e75fc-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="e75fc-127">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e75fc-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75fc-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="e75fc-128">Remarks</span></span>  
 <span data-ttu-id="e75fc-129">Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e75fc-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e75fc-130">Selon vos spécifications d'analyse, vous pouvez écrire un profil très général, qui s'abonne à un petit jeu de modifications d'état de haut niveau d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="e75fc-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e75fc-131">Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.</span><span class="sxs-lookup"><span data-stu-id="e75fc-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="e75fc-132">Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers.</span><span class="sxs-lookup"><span data-stu-id="e75fc-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="e75fc-133">Il existe un certain nombre de types de requêtes qui permettent de que vous abonner à différentes classes d’objets de lien hypertexte « http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord (VS.100).aspx » TrackingRecord.</span><span class="sxs-lookup"><span data-stu-id="e75fc-133">There are a handful of query types that allow you subscribe to different classes of  HYPERLINK "http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objects.</span></span> <span data-ttu-id="e75fc-134">Pour obtenir une liste complète des requêtes, consultez [ \<participants >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) et [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="e75fc-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="e75fc-135">L’exemple suivant montre un modèle de suivi dans un fichier de configuration qui permet à un participant de suivi pour vous abonner à la `Started` et `Completed` les événements de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e75fc-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e75fc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e75fc-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="e75fc-137">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e75fc-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e75fc-138">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e75fc-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
