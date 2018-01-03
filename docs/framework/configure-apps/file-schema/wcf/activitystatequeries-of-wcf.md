---
title: '&lt;activityStateQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5261e0769e63513720cc2df185920d424fa1a8f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="c054b-102">&lt;activityStateQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="c054b-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="c054b-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c054b-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="c054b-104">Pouvez par exemple, si vous souhaitez effectuer le suivi de chaque fois que l’activité « Envoyer du courrier électronique » se termine dans une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c054b-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="c054b-105">Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="c054b-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="c054b-106">Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="c054b-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="c054b-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c054b-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="c054b-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c054b-108">\<system.serviceModel></span></span>  
<span data-ttu-id="c054b-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="c054b-109">\<tracking></span></span>  
<span data-ttu-id="c054b-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c054b-110">\<trackingProfile></span></span>  
<span data-ttu-id="c054b-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="c054b-111">\<workflow></span></span>  
<span data-ttu-id="c054b-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="c054b-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c054b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c054b-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c054b-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c054b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c054b-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c054b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c054b-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="c054b-116">Attributes</span></span>  
 <span data-ttu-id="c054b-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c054b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c054b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c054b-118">Child Elements</span></span>  
  
|<span data-ttu-id="c054b-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c054b-119">Element</span></span>|<span data-ttu-id="c054b-120">Description</span><span class="sxs-lookup"><span data-stu-id="c054b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c054b-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="c054b-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="c054b-122">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="c054b-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c054b-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="c054b-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c054b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c054b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c054b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c054b-125">Element</span></span>|<span data-ttu-id="c054b-126">Description</span><span class="sxs-lookup"><span data-stu-id="c054b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c054b-127">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="c054b-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c054b-128">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="c054b-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c054b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c054b-129">See Also</span></span>  
 <span data-ttu-id="c054b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="c054b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="c054b-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="c054b-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="c054b-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c054b-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c054b-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="c054b-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
