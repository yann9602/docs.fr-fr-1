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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50dc2c4c5d4c1517d6ac3409dc4d932f67cbeb8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="97c62-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="97c62-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="97c62-103">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="97c62-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="97c62-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="97c62-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="97c62-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="97c62-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="97c62-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="97c62-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="97c62-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="97c62-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="97c62-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="97c62-108">\<system.serviceModel></span></span>  
<span data-ttu-id="97c62-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="97c62-109">\<tracking></span></span>  
<span data-ttu-id="97c62-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="97c62-110">\<trackingProfile></span></span>  
<span data-ttu-id="97c62-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="97c62-111">\<workflow></span></span>  
<span data-ttu-id="97c62-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="97c62-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="97c62-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="97c62-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c62-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97c62-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97c62-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="97c62-115">Attributes and Elements</span></span>  
 <span data-ttu-id="97c62-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="97c62-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97c62-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="97c62-117">Attributes</span></span>  
  
|<span data-ttu-id="97c62-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="97c62-118">Attribute</span></span>|<span data-ttu-id="97c62-119">Description</span><span class="sxs-lookup"><span data-stu-id="97c62-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97c62-120">activityName</span><span class="sxs-lookup"><span data-stu-id="97c62-120">activityName</span></span>|<span data-ttu-id="97c62-121">Chaîne qui spécifie le nom de l'activité de gestionnaire d'erreur qui a propagé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="97c62-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="97c62-122">La valeur par défaut est *, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="97c62-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="97c62-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="97c62-123">faultHandlerActivityName</span></span>|<span data-ttu-id="97c62-124">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="97c62-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97c62-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="97c62-125">Child Elements</span></span>  
 <span data-ttu-id="97c62-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97c62-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97c62-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="97c62-127">Parent Elements</span></span>  
  
|<span data-ttu-id="97c62-128">Élément</span><span class="sxs-lookup"><span data-stu-id="97c62-128">Element</span></span>|<span data-ttu-id="97c62-129">Description</span><span class="sxs-lookup"><span data-stu-id="97c62-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97c62-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="97c62-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="97c62-131">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="97c62-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="97c62-132">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="97c62-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97c62-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97c62-133">See Also</span></span>  
 <span data-ttu-id="97c62-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="97c62-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="97c62-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="97c62-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="97c62-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="97c62-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="97c62-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="97c62-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
