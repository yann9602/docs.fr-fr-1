---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c9dc0e0580c884377e790fa8c1e9a23de9ecd1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="613eb-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="613eb-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="613eb-103">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="613eb-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="613eb-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="613eb-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="613eb-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="613eb-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="613eb-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="613eb-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="613eb-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="613eb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="613eb-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="613eb-108">\<system.serviceModel></span></span>  
<span data-ttu-id="613eb-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="613eb-109">\<tracking></span></span>  
<span data-ttu-id="613eb-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="613eb-110">\<trackingProfile></span></span>  
<span data-ttu-id="613eb-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="613eb-111">\<workflow></span></span>  
<span data-ttu-id="613eb-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="613eb-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="613eb-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="613eb-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613eb-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="613eb-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="613eb-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="613eb-115">Attributes and Elements</span></span>  
 <span data-ttu-id="613eb-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="613eb-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="613eb-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="613eb-117">Attributes</span></span>  
  
|<span data-ttu-id="613eb-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="613eb-118">Attribute</span></span>|<span data-ttu-id="613eb-119">Description</span><span class="sxs-lookup"><span data-stu-id="613eb-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="613eb-120">activityName</span><span class="sxs-lookup"><span data-stu-id="613eb-120">activityName</span></span>|<span data-ttu-id="613eb-121">Chaîne qui spécifie le nom de l'activité de gestionnaire d'erreur qui a propagé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="613eb-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="613eb-122">La valeur par défaut est *, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="613eb-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="613eb-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="613eb-123">faultHandlerActivityName</span></span>|<span data-ttu-id="613eb-124">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="613eb-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="613eb-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="613eb-125">Child Elements</span></span>  
 <span data-ttu-id="613eb-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="613eb-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="613eb-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="613eb-127">Parent Elements</span></span>  
  
|<span data-ttu-id="613eb-128">Élément</span><span class="sxs-lookup"><span data-stu-id="613eb-128">Element</span></span>|<span data-ttu-id="613eb-129">Description</span><span class="sxs-lookup"><span data-stu-id="613eb-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="613eb-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="613eb-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="613eb-131">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="613eb-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="613eb-132">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="613eb-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="613eb-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="613eb-133">See Also</span></span>  
 <span data-ttu-id="613eb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="613eb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="613eb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="613eb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="613eb-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="613eb-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="613eb-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="613eb-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
