---
title: '&lt;activityScheduledQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 260b77789df6a03b640895ed158c94bfd1533f9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="96016-102">&lt;activityScheduledQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="96016-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="96016-103">Représente une collection de requêtes qui permettent d’effectuer le suivi d’une activité dont l’exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="96016-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="96016-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.</span><span class="sxs-lookup"><span data-stu-id="96016-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="96016-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="96016-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="96016-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="96016-106">\<system.serviceModel></span></span>  
<span data-ttu-id="96016-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="96016-107">\<tracking></span></span>  
<span data-ttu-id="96016-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="96016-108">\<trackingProfile></span></span>  
<span data-ttu-id="96016-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="96016-109">\<workflow></span></span>  
<span data-ttu-id="96016-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="96016-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="96016-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="96016-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96016-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96016-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96016-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="96016-113">Attributes and Elements</span></span>  
 <span data-ttu-id="96016-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="96016-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96016-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="96016-115">Attributes</span></span>  
  
|<span data-ttu-id="96016-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="96016-116">Attribute</span></span>|<span data-ttu-id="96016-117">Description</span><span class="sxs-lookup"><span data-stu-id="96016-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96016-118">activityName</span><span class="sxs-lookup"><span data-stu-id="96016-118">activityName</span></span>|<span data-ttu-id="96016-119">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="96016-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="96016-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="96016-120">childActivityName</span></span>|<span data-ttu-id="96016-121">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="96016-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96016-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="96016-122">Child Elements</span></span>  
 <span data-ttu-id="96016-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="96016-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96016-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="96016-124">Parent Elements</span></span>  
  
|<span data-ttu-id="96016-125">Élément</span><span class="sxs-lookup"><span data-stu-id="96016-125">Element</span></span>|<span data-ttu-id="96016-126">Description</span><span class="sxs-lookup"><span data-stu-id="96016-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96016-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="96016-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="96016-128">Requête qui permet d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée.</span><span class="sxs-lookup"><span data-stu-id="96016-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96016-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96016-129">See Also</span></span>  
 <span data-ttu-id="96016-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="96016-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="96016-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="96016-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="96016-132">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="96016-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="96016-133">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="96016-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
