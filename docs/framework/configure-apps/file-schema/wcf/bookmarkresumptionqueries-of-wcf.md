---
title: '&lt;bookmarkResumptionQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7afa80a0abfa29c02cdf2ec6c96d2049f98db436
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="bb006-102">&lt;bookmarkResumptionQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="bb006-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="bb006-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bb006-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bb006-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="bb006-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="bb006-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bb006-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="bb006-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bb006-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bb006-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="bb006-107">\<tracking></span></span>  
<span data-ttu-id="bb006-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bb006-108">\<trackingProfile></span></span>  
<span data-ttu-id="bb006-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="bb006-109">\<workflow></span></span>  
<span data-ttu-id="bb006-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="bb006-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="bb006-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="bb006-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb006-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb006-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb006-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bb006-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bb006-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bb006-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb006-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb006-115">Attributes</span></span>  
 <span data-ttu-id="bb006-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="bb006-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb006-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb006-117">Child Elements</span></span>  
  
|<span data-ttu-id="bb006-118">Élément</span><span class="sxs-lookup"><span data-stu-id="bb006-118">Element</span></span>|<span data-ttu-id="bb006-119">Description</span><span class="sxs-lookup"><span data-stu-id="bb006-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb006-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="bb006-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="bb006-121">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bb006-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bb006-122">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="bb006-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb006-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb006-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb006-124">Élément</span><span class="sxs-lookup"><span data-stu-id="bb006-124">Element</span></span>|<span data-ttu-id="bb006-125">Description</span><span class="sxs-lookup"><span data-stu-id="bb006-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb006-126">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="bb006-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="bb006-127">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="bb006-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb006-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb006-128">See Also</span></span>  
 <span data-ttu-id="bb006-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bb006-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="bb006-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bb006-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="bb006-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="bb006-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bb006-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="bb006-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
