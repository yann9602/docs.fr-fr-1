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
ms.openlocfilehash: 6fc9df52c691e13802607714977f3aa778cde84e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="62ecb-102">&lt;cancelRequestedQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="62ecb-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="62ecb-103">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="62ecb-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="62ecb-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="62ecb-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="62ecb-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="62ecb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="62ecb-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="62ecb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="62ecb-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="62ecb-107">\<tracking></span></span>  
<span data-ttu-id="62ecb-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="62ecb-108">\<trackingProfile></span></span>  
<span data-ttu-id="62ecb-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="62ecb-109">\<workflow></span></span>  
<span data-ttu-id="62ecb-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="62ecb-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="62ecb-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="62ecb-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ecb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62ecb-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62ecb-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="62ecb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="62ecb-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="62ecb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62ecb-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="62ecb-115">Attributes</span></span>  
  
|<span data-ttu-id="62ecb-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="62ecb-116">Attribute</span></span>|<span data-ttu-id="62ecb-117">Description</span><span class="sxs-lookup"><span data-stu-id="62ecb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62ecb-118">activityName</span><span class="sxs-lookup"><span data-stu-id="62ecb-118">activityName</span></span>|<span data-ttu-id="62ecb-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="62ecb-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="62ecb-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="62ecb-120">childActivityName</span></span>|<span data-ttu-id="62ecb-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="62ecb-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62ecb-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="62ecb-122">Child Elements</span></span>  
 <span data-ttu-id="62ecb-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="62ecb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62ecb-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="62ecb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="62ecb-125">Élément</span><span class="sxs-lookup"><span data-stu-id="62ecb-125">Element</span></span>|<span data-ttu-id="62ecb-126">Description</span><span class="sxs-lookup"><span data-stu-id="62ecb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62ecb-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="62ecb-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="62ecb-128">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="62ecb-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="62ecb-129">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="62ecb-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62ecb-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62ecb-130">See Also</span></span>  
 <span data-ttu-id="62ecb-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="62ecb-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="62ecb-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="62ecb-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="62ecb-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="62ecb-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="62ecb-134">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="62ecb-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
