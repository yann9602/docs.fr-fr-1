---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779ac3995d4d5fb1b63de6ae6b9db7103691d6f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="4d534-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="4d534-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="4d534-103">Représente une collection de requêtes qui permettent d’effectuer le suivi d’une activité dont l’exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="4d534-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4d534-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="4d534-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="4d534-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4d534-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4d534-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4d534-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4d534-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="4d534-107">\<tracking></span></span>  
<span data-ttu-id="4d534-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4d534-108">\<trackingProfile></span></span>  
<span data-ttu-id="4d534-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="4d534-109">\<workflow></span></span>  
<span data-ttu-id="4d534-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="4d534-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="4d534-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="4d534-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d534-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d534-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d534-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4d534-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4d534-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4d534-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d534-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="4d534-115">Attributes</span></span>  
  
|<span data-ttu-id="4d534-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="4d534-116">Attribute</span></span>|<span data-ttu-id="4d534-117">Description</span><span class="sxs-lookup"><span data-stu-id="4d534-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d534-118">activityName</span><span class="sxs-lookup"><span data-stu-id="4d534-118">activityName</span></span>|<span data-ttu-id="4d534-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="4d534-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="4d534-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="4d534-120">childActivityName</span></span>|<span data-ttu-id="4d534-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="4d534-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d534-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4d534-122">Child Elements</span></span>  
 <span data-ttu-id="4d534-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4d534-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d534-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4d534-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4d534-125">Élément</span><span class="sxs-lookup"><span data-stu-id="4d534-125">Element</span></span>|<span data-ttu-id="4d534-126">Description</span><span class="sxs-lookup"><span data-stu-id="4d534-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d534-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="4d534-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="4d534-128">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="4d534-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d534-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d534-129">See Also</span></span>  
 <span data-ttu-id="4d534-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4d534-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4d534-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4d534-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4d534-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="4d534-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4d534-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="4d534-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
