---
title: '&lt;activityScheduledQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 686b58d9efa4420de26fd7be52fe76208af63c6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="1b1d4-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1b1d4-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="1b1d4-103">Représente une collection de requêtes qui permettent d’effectuer le suivi d’une activité dont l’exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b1d4-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1b1d4-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b1d4-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="1b1d4-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1b1d4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1b1d4-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1b1d4-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-107">\<tracking></span></span>  
<span data-ttu-id="1b1d4-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-108">\<trackingProfile></span></span>  
<span data-ttu-id="1b1d4-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-109">\<workflow></span></span>  
<span data-ttu-id="1b1d4-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1d4-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b1d4-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b1d4-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1b1d4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1b1d4-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1b1d4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b1d4-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="1b1d4-114">Attributes</span></span>  
 <span data-ttu-id="1b1d4-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="1b1d4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b1d4-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1b1d4-116">Child Elements</span></span>  
  
|<span data-ttu-id="1b1d4-117">Élément</span><span class="sxs-lookup"><span data-stu-id="1b1d4-117">Element</span></span>|<span data-ttu-id="1b1d4-118">Description</span><span class="sxs-lookup"><span data-stu-id="1b1d4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b1d4-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="1b1d4-120">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b1d4-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b1d4-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1b1d4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1b1d4-122">Élément</span><span class="sxs-lookup"><span data-stu-id="1b1d4-122">Element</span></span>|<span data-ttu-id="1b1d4-123">Description</span><span class="sxs-lookup"><span data-stu-id="1b1d4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b1d4-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="1b1d4-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1b1d4-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **activityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="1b1d4-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b1d4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b1d4-126">See Also</span></span>  
 <span data-ttu-id="1b1d4-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1b1d4-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1b1d4-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1b1d4-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1b1d4-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="1b1d4-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1b1d4-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="1b1d4-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
