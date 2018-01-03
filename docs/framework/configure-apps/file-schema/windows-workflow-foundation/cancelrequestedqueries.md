---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 774012a0a64342bbd21832213a6c41fe41fdaef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="ba17b-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="ba17b-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="ba17b-103">Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent.</span><span class="sxs-lookup"><span data-stu-id="ba17b-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ba17b-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="ba17b-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="ba17b-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ba17b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ba17b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ba17b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ba17b-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="ba17b-107">\<tracking></span></span>  
<span data-ttu-id="ba17b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ba17b-108">\<trackingProfile></span></span>  
<span data-ttu-id="ba17b-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ba17b-109">\<workflow></span></span>  
<span data-ttu-id="ba17b-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="ba17b-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba17b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba17b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba17b-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ba17b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ba17b-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ba17b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba17b-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba17b-114">Attributes</span></span>  
 <span data-ttu-id="ba17b-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ba17b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba17b-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba17b-116">Child Elements</span></span>  
  
|<span data-ttu-id="ba17b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="ba17b-117">Element</span></span>|<span data-ttu-id="ba17b-118">Description</span><span class="sxs-lookup"><span data-stu-id="ba17b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba17b-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="ba17b-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="ba17b-120">Requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="ba17b-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba17b-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba17b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ba17b-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ba17b-122">Element</span></span>|<span data-ttu-id="ba17b-123">Description</span><span class="sxs-lookup"><span data-stu-id="ba17b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba17b-124">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ba17b-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ba17b-125">Un élément de configuration qui contient toutes les requêtes pour un flux de travail spécifique identifié par le **activityDefinitionId** propriété.</span><span class="sxs-lookup"><span data-stu-id="ba17b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba17b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba17b-126">See Also</span></span>  
 [<span data-ttu-id="ba17b-127">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ba17b-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ba17b-128">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ba17b-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
