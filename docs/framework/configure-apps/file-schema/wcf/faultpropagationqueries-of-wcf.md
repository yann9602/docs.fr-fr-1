---
title: '&lt;faultPropagationQueries&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 771908114f4f4e1cc2588e39e7f3d811c336a05a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="e0b14-102">&lt;faultPropagationQueries&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="e0b14-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="e0b14-103">Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e0b14-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0b14-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e0b14-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e0b14-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e0b14-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e0b14-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e0b14-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e0b14-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e0b14-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="e0b14-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e0b14-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e0b14-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="e0b14-109">\<tracking></span></span>  
<span data-ttu-id="e0b14-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e0b14-110">\<trackingProfile></span></span>  
<span data-ttu-id="e0b14-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="e0b14-111">\<workflow></span></span>  
<span data-ttu-id="e0b14-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e0b14-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b14-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0b14-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0b14-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0b14-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e0b14-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e0b14-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0b14-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0b14-116">Attributes</span></span>  
 <span data-ttu-id="e0b14-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="e0b14-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0b14-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0b14-118">Child Elements</span></span>  
  
|<span data-ttu-id="e0b14-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e0b14-119">Element</span></span>|<span data-ttu-id="e0b14-120">Description</span><span class="sxs-lookup"><span data-stu-id="e0b14-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0b14-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e0b14-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="e0b14-122">Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="e0b14-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0b14-123">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="e0b14-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0b14-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0b14-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e0b14-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e0b14-125">Element</span></span>|<span data-ttu-id="e0b14-126">Description</span><span class="sxs-lookup"><span data-stu-id="e0b14-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0b14-127">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="e0b14-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e0b14-128">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="e0b14-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0b14-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0b14-129">See Also</span></span>  
 <span data-ttu-id="e0b14-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e0b14-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e0b14-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e0b14-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e0b14-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="e0b14-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e0b14-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="e0b14-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
