---
title: '&lt;activityScheduledQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a857a86d45226e3dd3805a900612f55078c0bf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="ab229-102">&lt;activityScheduledQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="ab229-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="ab229-103">Représente une collection de requêtes qui permettent d’effectuer le suivi d’une activité dont l’exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="ab229-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ab229-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="ab229-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ab229-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ab229-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="ab229-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ab229-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ab229-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="ab229-107">\<tracking></span></span>  
<span data-ttu-id="ab229-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ab229-108">\<trackingProfile></span></span>  
<span data-ttu-id="ab229-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ab229-109">\<workflow></span></span>  
<span data-ttu-id="ab229-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ab229-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab229-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab229-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab229-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ab229-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ab229-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ab229-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab229-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ab229-114">Attributes</span></span>  
 <span data-ttu-id="ab229-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ab229-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab229-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ab229-116">Child Elements</span></span>  
  
|<span data-ttu-id="ab229-117">Élément</span><span class="sxs-lookup"><span data-stu-id="ab229-117">Element</span></span>|<span data-ttu-id="ab229-118">Description</span><span class="sxs-lookup"><span data-stu-id="ab229-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab229-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ab229-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="ab229-120">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="ab229-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab229-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ab229-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ab229-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ab229-122">Element</span></span>|<span data-ttu-id="ab229-123">Description</span><span class="sxs-lookup"><span data-stu-id="ab229-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab229-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ab229-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ab229-125">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="ab229-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab229-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab229-126">See Also</span></span>  
 <span data-ttu-id="ab229-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="ab229-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="ab229-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="ab229-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="ab229-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ab229-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ab229-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ab229-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
