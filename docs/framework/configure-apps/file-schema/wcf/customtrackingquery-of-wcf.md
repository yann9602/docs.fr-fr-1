---
title: '&lt;customTrackingQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27637abceb23a54e784afbcc2e0517db51542b53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="7cb49-102">&lt;customTrackingQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="7cb49-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="7cb49-103">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="7cb49-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="7cb49-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7cb49-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="7cb49-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7cb49-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="7cb49-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7cb49-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7cb49-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="7cb49-107">\<tracking></span></span>  
<span data-ttu-id="7cb49-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7cb49-108">\<trackingProfile></span></span>  
<span data-ttu-id="7cb49-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="7cb49-109">\<workflow></span></span>  
<span data-ttu-id="7cb49-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="7cb49-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="7cb49-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="7cb49-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb49-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cb49-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7cb49-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7cb49-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7cb49-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7cb49-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cb49-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="7cb49-115">Attributes</span></span>  
  
|<span data-ttu-id="7cb49-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="7cb49-116">Attribute</span></span>|<span data-ttu-id="7cb49-117">Description</span><span class="sxs-lookup"><span data-stu-id="7cb49-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7cb49-118">activityName</span><span class="sxs-lookup"><span data-stu-id="7cb49-118">activityName</span></span>|<span data-ttu-id="7cb49-119">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="7cb49-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="7cb49-120">name</span><span class="sxs-lookup"><span data-stu-id="7cb49-120">name</span></span>|<span data-ttu-id="7cb49-121">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="7cb49-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cb49-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7cb49-122">Child Elements</span></span>  
 <span data-ttu-id="7cb49-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7cb49-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cb49-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7cb49-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7cb49-125">Élément</span><span class="sxs-lookup"><span data-stu-id="7cb49-125">Element</span></span>|<span data-ttu-id="7cb49-126">Description</span><span class="sxs-lookup"><span data-stu-id="7cb49-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cb49-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="7cb49-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="7cb49-128">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="7cb49-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cb49-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cb49-129">See Also</span></span>  
 <span data-ttu-id="7cb49-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7cb49-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="7cb49-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7cb49-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="7cb49-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="7cb49-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7cb49-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="7cb49-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
