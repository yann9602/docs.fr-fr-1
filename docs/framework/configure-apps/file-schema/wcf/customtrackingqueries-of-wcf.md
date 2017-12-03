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
ms.openlocfilehash: 8a7a69b481da7315c8d26b00c171d030f77d9b63
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="da89f-102">&lt;customTrackingQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="da89f-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="da89f-103">Représente une collection de requêtes permettant d’effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="da89f-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="da89f-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="da89f-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="da89f-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="da89f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="da89f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="da89f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="da89f-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="da89f-107">\<tracking></span></span>  
<span data-ttu-id="da89f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="da89f-108">\<trackingProfile></span></span>  
<span data-ttu-id="da89f-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="da89f-109">\<workflow></span></span>  
<span data-ttu-id="da89f-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="da89f-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da89f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da89f-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da89f-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="da89f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="da89f-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="da89f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da89f-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="da89f-114">Attributes</span></span>  
 <span data-ttu-id="da89f-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="da89f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da89f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="da89f-116">Child Elements</span></span>  
  
|<span data-ttu-id="da89f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="da89f-117">Element</span></span>|<span data-ttu-id="da89f-118">Description</span><span class="sxs-lookup"><span data-stu-id="da89f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da89f-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="da89f-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="da89f-120">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="da89f-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da89f-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="da89f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="da89f-122">Élément</span><span class="sxs-lookup"><span data-stu-id="da89f-122">Element</span></span>|<span data-ttu-id="da89f-123">Description</span><span class="sxs-lookup"><span data-stu-id="da89f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da89f-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="da89f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="da89f-125">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="da89f-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da89f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da89f-126">See Also</span></span>  
 <span data-ttu-id="da89f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="da89f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="da89f-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="da89f-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="da89f-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="da89f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="da89f-130">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="da89f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
