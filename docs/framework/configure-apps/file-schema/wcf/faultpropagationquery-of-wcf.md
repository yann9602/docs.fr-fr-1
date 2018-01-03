---
title: '&lt;faultPropagationQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f017b695b91a08c1126b48c944977c054c73affe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="ef706-102">&lt;faultPropagationQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="ef706-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="ef706-103">Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ef706-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ef706-104">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="ef706-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ef706-105">Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ef706-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ef706-106">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.</span><span class="sxs-lookup"><span data-stu-id="ef706-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="ef706-107">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ef706-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ef706-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ef706-108">\<system.serviceModel></span></span>  
<span data-ttu-id="ef706-109">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="ef706-109">\<tracking></span></span>  
<span data-ttu-id="ef706-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ef706-110">\<trackingProfile></span></span>  
<span data-ttu-id="ef706-111">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="ef706-111">\<workflow></span></span>  
<span data-ttu-id="ef706-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ef706-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="ef706-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="ef706-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef706-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef706-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef706-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ef706-115">Attributes and Elements</span></span>  
 <span data-ttu-id="ef706-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ef706-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef706-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="ef706-117">Attributes</span></span>  
  
|<span data-ttu-id="ef706-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="ef706-118">Attribute</span></span>|<span data-ttu-id="ef706-119">Description</span><span class="sxs-lookup"><span data-stu-id="ef706-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef706-120">activityName</span><span class="sxs-lookup"><span data-stu-id="ef706-120">activityName</span></span>|<span data-ttu-id="ef706-121">Chaîne qui spécifie le nom de l'activité de gestionnaire d'erreur qui a propagé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="ef706-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="ef706-122">La valeur par défaut est *, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="ef706-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="ef706-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="ef706-123">faultHandlerActivityName</span></span>|<span data-ttu-id="ef706-124">Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="ef706-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef706-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ef706-125">Child Elements</span></span>  
 <span data-ttu-id="ef706-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ef706-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef706-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ef706-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ef706-128">Élément</span><span class="sxs-lookup"><span data-stu-id="ef706-128">Element</span></span>|<span data-ttu-id="ef706-129">Description</span><span class="sxs-lookup"><span data-stu-id="ef706-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef706-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ef706-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="ef706-131">Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.</span><span class="sxs-lookup"><span data-stu-id="ef706-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ef706-132">Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.</span><span class="sxs-lookup"><span data-stu-id="ef706-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef706-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef706-133">See Also</span></span>  
 <span data-ttu-id="ef706-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ef706-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ef706-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ef706-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ef706-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ef706-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ef706-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="ef706-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
