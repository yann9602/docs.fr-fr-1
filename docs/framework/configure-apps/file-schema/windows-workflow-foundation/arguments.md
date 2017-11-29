---
title: '&lt;arguments&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b0cb0f132b21a419b0a173df169fbbd65673d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltargumentsgt"></a><span data-ttu-id="be48a-102">&lt;arguments&gt;</span><span class="sxs-lookup"><span data-stu-id="be48a-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="be48a-103">Représente une collection d'arguments associés à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="be48a-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="be48a-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="be48a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="be48a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="be48a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="be48a-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="be48a-106">\<tracking></span></span>  
<span data-ttu-id="be48a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="be48a-107">\<trackingProfile></span></span>  
<span data-ttu-id="be48a-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="be48a-108">\<workflow></span></span>  
<span data-ttu-id="be48a-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="be48a-109">\<activityStateQueries></span></span>  
<span data-ttu-id="be48a-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="be48a-110">\<activityStateQuery></span></span>  
<span data-ttu-id="be48a-111">\<arguments ></span><span class="sxs-lookup"><span data-stu-id="be48a-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be48a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be48a-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be48a-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="be48a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="be48a-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="be48a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be48a-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="be48a-115">Attributes</span></span>  
 <span data-ttu-id="be48a-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="be48a-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="be48a-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="be48a-117">Child Elements</span></span>  
  
|<span data-ttu-id="be48a-118">Élément</span><span class="sxs-lookup"><span data-stu-id="be48a-118">Element</span></span>|<span data-ttu-id="be48a-119">Description</span><span class="sxs-lookup"><span data-stu-id="be48a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be48a-120">\<argument ></span><span class="sxs-lookup"><span data-stu-id="be48a-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="be48a-121">Argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="be48a-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be48a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="be48a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="be48a-123">Élément</span><span class="sxs-lookup"><span data-stu-id="be48a-123">Element</span></span>|<span data-ttu-id="be48a-124">Description</span><span class="sxs-lookup"><span data-stu-id="be48a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be48a-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="be48a-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="be48a-126">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="be48a-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="be48a-127">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="be48a-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be48a-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="be48a-128">Remarks</span></span>  
 <span data-ttu-id="be48a-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="be48a-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="be48a-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="be48a-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="be48a-131">Vous pouvez utiliser la [ \<arguments >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) et [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) éléments à extraire une variable ou un argument à partir de toutes les activités dans un flux de travail. L’exemple suivant montre une requête d’état d’activité qui extrait des variables et arguments lorsque l’activité `Closed` enregistrement de suivi est émis.</span><span class="sxs-lookup"><span data-stu-id="be48a-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="be48a-132">Variables et arguments peuvent être extraits uniquement avec un objet ActivityStateRecord et par conséquent êtes abonnés au sein d’un suivi à l’aide du profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="be48a-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be48a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be48a-133">See Also</span></span>  
 <span data-ttu-id="be48a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="be48a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="be48a-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="be48a-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="be48a-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="be48a-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="be48a-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="be48a-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
