---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241684a3a2344d6eb7f3b34c81c581b0ec5130f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="8b16a-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8b16a-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="8b16a-103">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="8b16a-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8b16a-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8b16a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8b16a-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8b16a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8b16a-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8b16a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8b16a-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="8b16a-107">\<tracking></span></span>  
<span data-ttu-id="8b16a-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8b16a-108">\<trackingProfile></span></span>  
<span data-ttu-id="8b16a-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="8b16a-109">\<workflow></span></span>  
<span data-ttu-id="8b16a-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8b16a-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b16a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b16a-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b16a-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8b16a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8b16a-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8b16a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b16a-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b16a-114">Attributes</span></span>  
 <span data-ttu-id="8b16a-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="8b16a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b16a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b16a-116">Child Elements</span></span>  
  
|<span data-ttu-id="8b16a-117">Élément</span><span class="sxs-lookup"><span data-stu-id="8b16a-117">Element</span></span>|<span data-ttu-id="8b16a-118">Description</span><span class="sxs-lookup"><span data-stu-id="8b16a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b16a-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8b16a-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="8b16a-120">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="8b16a-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b16a-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b16a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8b16a-122">Élément</span><span class="sxs-lookup"><span data-stu-id="8b16a-122">Element</span></span>|<span data-ttu-id="8b16a-123">Description</span><span class="sxs-lookup"><span data-stu-id="8b16a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b16a-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="8b16a-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8b16a-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **activityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="8b16a-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b16a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b16a-126">See Also</span></span>  
 <span data-ttu-id="8b16a-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b16a-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8b16a-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b16a-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8b16a-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="8b16a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8b16a-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="8b16a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
