---
title: '&lt;variables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3eee12b8212243f286bb21604904b37273921e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltvariablesgt"></a><span data-ttu-id="cd25c-102">&lt;variables&gt;</span><span class="sxs-lookup"><span data-stu-id="cd25c-102">&lt;variables&gt;</span></span>
<span data-ttu-id="cd25c-103">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="cd25c-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="cd25c-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cd25c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="cd25c-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cd25c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cd25c-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="cd25c-106">\<tracking></span></span>  
<span data-ttu-id="cd25c-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="cd25c-107">\<trackingProfile></span></span>  
<span data-ttu-id="cd25c-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="cd25c-108">\<workflow></span></span>  
<span data-ttu-id="cd25c-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="cd25c-109">\<activityStateQueries></span></span>  
<span data-ttu-id="cd25c-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="cd25c-110">\<activityStateQuery></span></span>  
<span data-ttu-id="cd25c-111">\<variables ></span><span class="sxs-lookup"><span data-stu-id="cd25c-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd25c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd25c-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd25c-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cd25c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cd25c-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cd25c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd25c-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="cd25c-115">Attributes</span></span>  
 <span data-ttu-id="cd25c-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="cd25c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd25c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cd25c-117">Child Elements</span></span>  
  
|<span data-ttu-id="cd25c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="cd25c-118">Element</span></span>|<span data-ttu-id="cd25c-119">Description</span><span class="sxs-lookup"><span data-stu-id="cd25c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd25c-120">\<variable ></span><span class="sxs-lookup"><span data-stu-id="cd25c-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="cd25c-121">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="cd25c-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd25c-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cd25c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cd25c-123">Élément</span><span class="sxs-lookup"><span data-stu-id="cd25c-123">Element</span></span>|<span data-ttu-id="cd25c-124">Description</span><span class="sxs-lookup"><span data-stu-id="cd25c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd25c-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="cd25c-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="cd25c-126">Représente un élément de configuration qui permet d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="cd25c-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cd25c-127">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="cd25c-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd25c-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="cd25c-128">Remarks</span></span>  
 <span data-ttu-id="cd25c-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="cd25c-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="cd25c-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="cd25c-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="cd25c-131">Vous pouvez utiliser la [ \<arguments >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) et [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) éléments à extraire une variable ou un argument à partir de toutes les activités dans un flux de travail. L’exemple suivant montre une requête d’état d’activité qui extrait des variables et arguments lorsque l’activité `Closed` enregistrement de suivi est émis.</span><span class="sxs-lookup"><span data-stu-id="cd25c-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="cd25c-132">Variables et arguments peuvent être extraits uniquement avec un objet ActivityStateRecord et par conséquent êtes abonnés au sein d’un suivi à l’aide du profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="cd25c-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd25c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd25c-133">See Also</span></span>  
 <span data-ttu-id="cd25c-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cd25c-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="cd25c-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cd25c-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="cd25c-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="cd25c-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="cd25c-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="cd25c-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
