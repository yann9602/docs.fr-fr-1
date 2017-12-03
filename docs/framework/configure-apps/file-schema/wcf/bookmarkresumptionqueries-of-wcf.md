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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa46d62262b91d5b88564b50f97fccf7aefefa6d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="5a8d0-102">&lt;bookmarkResumptionQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="5a8d0-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="5a8d0-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5a8d0-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="5a8d0-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5a8d0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="5a8d0-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5a8d0-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-107">\<tracking></span></span>  
<span data-ttu-id="5a8d0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-108">\<trackingProfile></span></span>  
<span data-ttu-id="5a8d0-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-109">\<workflow></span></span>  
<span data-ttu-id="5a8d0-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="5a8d0-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8d0-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a8d0-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a8d0-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a8d0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5a8d0-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a8d0-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a8d0-115">Attributes</span></span>  
 <span data-ttu-id="5a8d0-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="5a8d0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a8d0-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a8d0-117">Child Elements</span></span>  
  
|<span data-ttu-id="5a8d0-118">Élément</span><span class="sxs-lookup"><span data-stu-id="5a8d0-118">Element</span></span>|<span data-ttu-id="5a8d0-119">Description</span><span class="sxs-lookup"><span data-stu-id="5a8d0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a8d0-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="5a8d0-121">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5a8d0-122">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a8d0-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a8d0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5a8d0-124">Élément</span><span class="sxs-lookup"><span data-stu-id="5a8d0-124">Element</span></span>|<span data-ttu-id="5a8d0-125">Description</span><span class="sxs-lookup"><span data-stu-id="5a8d0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a8d0-126">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="5a8d0-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5a8d0-127">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="5a8d0-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a8d0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a8d0-128">See Also</span></span>  
 <span data-ttu-id="5a8d0-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a8d0-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="5a8d0-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a8d0-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="5a8d0-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="5a8d0-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5a8d0-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="5a8d0-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
