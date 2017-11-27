---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc06c34cb4db99f5e7b6850ed8e7cf7ed073ef72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="67c6d-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="67c6d-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="67c6d-103">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="67c6d-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="67c6d-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="67c6d-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="67c6d-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="67c6d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="67c6d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="67c6d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="67c6d-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="67c6d-107">\<tracking></span></span>  
<span data-ttu-id="67c6d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="67c6d-108">\<trackingProfile></span></span>  
<span data-ttu-id="67c6d-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="67c6d-109">\<workflow></span></span>  
<span data-ttu-id="67c6d-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="67c6d-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="67c6d-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="67c6d-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c6d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67c6d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67c6d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="67c6d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="67c6d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="67c6d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67c6d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="67c6d-115">Attributes</span></span>  
  
|<span data-ttu-id="67c6d-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="67c6d-116">Attribute</span></span>|<span data-ttu-id="67c6d-117">Description</span><span class="sxs-lookup"><span data-stu-id="67c6d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67c6d-118">activityName</span><span class="sxs-lookup"><span data-stu-id="67c6d-118">activityName</span></span>|<span data-ttu-id="67c6d-119">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="67c6d-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="67c6d-120">name</span><span class="sxs-lookup"><span data-stu-id="67c6d-120">name</span></span>|<span data-ttu-id="67c6d-121">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="67c6d-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67c6d-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="67c6d-122">Child Elements</span></span>  
 <span data-ttu-id="67c6d-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="67c6d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67c6d-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="67c6d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="67c6d-125">Élément</span><span class="sxs-lookup"><span data-stu-id="67c6d-125">Element</span></span>|<span data-ttu-id="67c6d-126">Description</span><span class="sxs-lookup"><span data-stu-id="67c6d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67c6d-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="67c6d-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="67c6d-128">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="67c6d-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67c6d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67c6d-129">See Also</span></span>  
 <span data-ttu-id="67c6d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="67c6d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="67c6d-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="67c6d-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="67c6d-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="67c6d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="67c6d-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="67c6d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
