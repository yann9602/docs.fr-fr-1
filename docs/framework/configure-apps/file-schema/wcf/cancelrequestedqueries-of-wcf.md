---
title: '&lt;cancelRequestedQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be3c02bdf0d51006d7df3b382541b704f71f2463
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="dc454-102">&lt;cancelRequestedQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="dc454-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="dc454-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="dc454-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="dc454-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="dc454-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="dc454-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dc454-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="dc454-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dc454-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dc454-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="dc454-107">\<tracking></span></span>  
<span data-ttu-id="dc454-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dc454-108">\<trackingProfile></span></span>  
<span data-ttu-id="dc454-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="dc454-109">\<workflow></span></span>  
<span data-ttu-id="dc454-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="dc454-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc454-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc454-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc454-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dc454-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc454-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dc454-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc454-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="dc454-114">Attributes</span></span>  
 <span data-ttu-id="dc454-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="dc454-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc454-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc454-116">Child Elements</span></span>  
  
|<span data-ttu-id="dc454-117">Élément</span><span class="sxs-lookup"><span data-stu-id="dc454-117">Element</span></span>|<span data-ttu-id="dc454-118">Description</span><span class="sxs-lookup"><span data-stu-id="dc454-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc454-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="dc454-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="dc454-120">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="dc454-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc454-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc454-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dc454-122">Élément</span><span class="sxs-lookup"><span data-stu-id="dc454-122">Element</span></span>|<span data-ttu-id="dc454-123">Description</span><span class="sxs-lookup"><span data-stu-id="dc454-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc454-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="dc454-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="dc454-125">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="dc454-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc454-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc454-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="dc454-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="dc454-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dc454-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="dc454-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
