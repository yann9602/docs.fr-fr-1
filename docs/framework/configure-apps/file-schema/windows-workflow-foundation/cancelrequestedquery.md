---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c9ad0f766256d6507775c2cca1b9d54b474abc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="b1bf3-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b1bf3-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="b1bf3-103">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b1bf3-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="b1bf3-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b1bf3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b1bf3-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b1bf3-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-107">\<tracking></span></span>  
<span data-ttu-id="b1bf3-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-108">\<trackingProfile></span></span>  
<span data-ttu-id="b1bf3-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-109">\<workflow></span></span>  
<span data-ttu-id="b1bf3-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b1bf3-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bf3-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1bf3-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1bf3-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1bf3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b1bf3-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1bf3-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1bf3-115">Attributes</span></span>  
  
|<span data-ttu-id="b1bf3-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1bf3-116">Attribute</span></span>|<span data-ttu-id="b1bf3-117">Description</span><span class="sxs-lookup"><span data-stu-id="b1bf3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1bf3-118">activityName</span><span class="sxs-lookup"><span data-stu-id="b1bf3-118">activityName</span></span>|<span data-ttu-id="b1bf3-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b1bf3-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b1bf3-120">childActivityName</span></span>|<span data-ttu-id="b1bf3-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1bf3-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1bf3-122">Child Elements</span></span>  
 <span data-ttu-id="b1bf3-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1bf3-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1bf3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b1bf3-125">Élément</span><span class="sxs-lookup"><span data-stu-id="b1bf3-125">Element</span></span>|<span data-ttu-id="b1bf3-126">Description</span><span class="sxs-lookup"><span data-stu-id="b1bf3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1bf3-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b1bf3-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="b1bf3-128">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b1bf3-129">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="b1bf3-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1bf3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1bf3-130">See Also</span></span>  
 <span data-ttu-id="b1bf3-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1bf3-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b1bf3-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1bf3-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b1bf3-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="b1bf3-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b1bf3-134">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="b1bf3-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
