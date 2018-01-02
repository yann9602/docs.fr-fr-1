---
title: '&lt;customTrackingQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a155f435fb61c19a50f1b047c7dd28b603716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="07659-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="07659-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="07659-103">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="07659-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="07659-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="07659-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="07659-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="07659-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="07659-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="07659-106">\<system.serviceModel></span></span>  
<span data-ttu-id="07659-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="07659-107">\<tracking></span></span>  
<span data-ttu-id="07659-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="07659-108">\<trackingProfile></span></span>  
<span data-ttu-id="07659-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="07659-109">\<workflow></span></span>  
<span data-ttu-id="07659-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="07659-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07659-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07659-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07659-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07659-112">Attributes and Elements</span></span>  
 <span data-ttu-id="07659-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="07659-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07659-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="07659-114">Attributes</span></span>  
 <span data-ttu-id="07659-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07659-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07659-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07659-116">Child Elements</span></span>  
  
|<span data-ttu-id="07659-117">Élément</span><span class="sxs-lookup"><span data-stu-id="07659-117">Element</span></span>|<span data-ttu-id="07659-118">Description</span><span class="sxs-lookup"><span data-stu-id="07659-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07659-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="07659-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="07659-120">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="07659-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07659-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07659-121">Parent Elements</span></span>  
  
|<span data-ttu-id="07659-122">Élément</span><span class="sxs-lookup"><span data-stu-id="07659-122">Element</span></span>|<span data-ttu-id="07659-123">Description</span><span class="sxs-lookup"><span data-stu-id="07659-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07659-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="07659-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="07659-125">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="07659-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07659-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07659-126">See Also</span></span>  
 <span data-ttu-id="07659-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="07659-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="07659-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="07659-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="07659-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="07659-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="07659-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="07659-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
