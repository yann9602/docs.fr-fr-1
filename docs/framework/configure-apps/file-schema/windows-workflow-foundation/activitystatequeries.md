---
title: '&lt;activityStateQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56845a0f596ca83f1abb31e481e38ccc3f808580
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="038de-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="038de-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="038de-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="038de-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="038de-104">Pouvez par exemple, si vous souhaitez effectuer le suivi de chaque fois que l’activité « Envoyer du courrier électronique » se termine dans une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="038de-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="038de-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="038de-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="038de-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="038de-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="038de-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="038de-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="038de-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="038de-108">\<system.serviceModel></span></span>  
<span data-ttu-id="038de-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="038de-109">\<tracking></span></span>  
<span data-ttu-id="038de-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="038de-110">\<trackingProfile></span></span>  
<span data-ttu-id="038de-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="038de-111">\<workflow></span></span>  
<span data-ttu-id="038de-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="038de-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="038de-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="038de-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="038de-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="038de-114">Attributes and Elements</span></span>  
 <span data-ttu-id="038de-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="038de-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="038de-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="038de-116">Attributes</span></span>  
 <span data-ttu-id="038de-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="038de-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="038de-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="038de-118">Child Elements</span></span>  
  
|<span data-ttu-id="038de-119">Élément</span><span class="sxs-lookup"><span data-stu-id="038de-119">Element</span></span>|<span data-ttu-id="038de-120">Description</span><span class="sxs-lookup"><span data-stu-id="038de-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="038de-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="038de-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="038de-122">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="038de-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="038de-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="038de-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="038de-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="038de-124">Parent Elements</span></span>  
  
|<span data-ttu-id="038de-125">Élément</span><span class="sxs-lookup"><span data-stu-id="038de-125">Element</span></span>|<span data-ttu-id="038de-126">Description</span><span class="sxs-lookup"><span data-stu-id="038de-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="038de-127">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="038de-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="038de-128">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **activityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="038de-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="038de-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="038de-129">See Also</span></span>  
 <span data-ttu-id="038de-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="038de-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="038de-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="038de-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="038de-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="038de-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="038de-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="038de-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
