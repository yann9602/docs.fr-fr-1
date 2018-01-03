---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="af6bf-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="af6bf-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="af6bf-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="af6bf-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="af6bf-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="af6bf-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="af6bf-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="af6bf-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="af6bf-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="af6bf-106">\<system.serviceModel></span></span>  
<span data-ttu-id="af6bf-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="af6bf-107">\<tracking></span></span>  
<span data-ttu-id="af6bf-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="af6bf-108">\<trackingProfile></span></span>  
<span data-ttu-id="af6bf-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="af6bf-109">\<workflow></span></span>  
<span data-ttu-id="af6bf-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="af6bf-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="af6bf-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="af6bf-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6bf-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af6bf-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af6bf-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af6bf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="af6bf-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af6bf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af6bf-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="af6bf-115">Attributes</span></span>  
 <span data-ttu-id="af6bf-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="af6bf-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af6bf-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af6bf-117">Child Elements</span></span>  
  
|<span data-ttu-id="af6bf-118">Élément</span><span class="sxs-lookup"><span data-stu-id="af6bf-118">Element</span></span>|<span data-ttu-id="af6bf-119">Description</span><span class="sxs-lookup"><span data-stu-id="af6bf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af6bf-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="af6bf-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="af6bf-121">Requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="af6bf-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="af6bf-122">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="af6bf-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af6bf-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af6bf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="af6bf-124">Élément</span><span class="sxs-lookup"><span data-stu-id="af6bf-124">Element</span></span>|<span data-ttu-id="af6bf-125">Description</span><span class="sxs-lookup"><span data-stu-id="af6bf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af6bf-126">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="af6bf-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="af6bf-127">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **activityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="af6bf-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af6bf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af6bf-128">See Also</span></span>  
 <span data-ttu-id="af6bf-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="af6bf-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="af6bf-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="af6bf-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="af6bf-131">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="af6bf-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="af6bf-132">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="af6bf-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
