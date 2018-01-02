---
title: '&lt;cancelRequestedQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2af49aab76e82a97aeee92b4799b91011f70c509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="41815-102">&lt;cancelRequestedQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="41815-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="41815-103">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="41815-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="41815-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="41815-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="41815-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="41815-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="41815-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="41815-106">\<system.serviceModel></span></span>  
<span data-ttu-id="41815-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="41815-107">\<tracking></span></span>  
<span data-ttu-id="41815-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="41815-108">\<trackingProfile></span></span>  
<span data-ttu-id="41815-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="41815-109">\<workflow></span></span>  
<span data-ttu-id="41815-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="41815-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="41815-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="41815-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41815-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41815-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41815-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="41815-113">Attributes and Elements</span></span>  
 <span data-ttu-id="41815-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="41815-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41815-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="41815-115">Attributes</span></span>  
  
|<span data-ttu-id="41815-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="41815-116">Attribute</span></span>|<span data-ttu-id="41815-117">Description</span><span class="sxs-lookup"><span data-stu-id="41815-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41815-118">activityName</span><span class="sxs-lookup"><span data-stu-id="41815-118">activityName</span></span>|<span data-ttu-id="41815-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="41815-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="41815-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="41815-120">childActivityName</span></span>|<span data-ttu-id="41815-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="41815-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41815-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="41815-122">Child Elements</span></span>  
 <span data-ttu-id="41815-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="41815-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41815-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="41815-124">Parent Elements</span></span>  
  
|<span data-ttu-id="41815-125">Élément</span><span class="sxs-lookup"><span data-stu-id="41815-125">Element</span></span>|<span data-ttu-id="41815-126">Description</span><span class="sxs-lookup"><span data-stu-id="41815-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41815-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="41815-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="41815-128">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="41815-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="41815-129">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="41815-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41815-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41815-130">See Also</span></span>  
 <span data-ttu-id="41815-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="41815-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="41815-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="41815-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="41815-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="41815-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="41815-134">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="41815-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
