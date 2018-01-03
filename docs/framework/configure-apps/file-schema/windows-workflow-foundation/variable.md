---
title: '&lt;variable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971e3e366c2383828dde8e8f152660fb39c886ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="c99a6-102">&lt;variable&gt;</span><span class="sxs-lookup"><span data-stu-id="c99a6-102">&lt;variable&gt;</span></span>
<span data-ttu-id="c99a6-103">Représente une collection de variables associées à cette requête d'activité.</span><span class="sxs-lookup"><span data-stu-id="c99a6-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="c99a6-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c99a6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c99a6-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c99a6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c99a6-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="c99a6-106">\<tracking></span></span>  
<span data-ttu-id="c99a6-107">\<profils ></span><span class="sxs-lookup"><span data-stu-id="c99a6-107">\<profiles></span></span>  
<span data-ttu-id="c99a6-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c99a6-108">\<trackingProfile></span></span>  
<span data-ttu-id="c99a6-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="c99a6-109">\<workflow></span></span>  
<span data-ttu-id="c99a6-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="c99a6-110">\<activityStateQueries></span></span>  
<span data-ttu-id="c99a6-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="c99a6-111">\<activityStateQuery></span></span>  
<span data-ttu-id="c99a6-112">\<variables ></span><span class="sxs-lookup"><span data-stu-id="c99a6-112">\<variables></span></span>  
<span data-ttu-id="c99a6-113">\<variable ></span><span class="sxs-lookup"><span data-stu-id="c99a6-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99a6-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c99a6-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c99a6-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c99a6-115">Attributes and Elements</span></span>  
 <span data-ttu-id="c99a6-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c99a6-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c99a6-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="c99a6-117">Attributes</span></span>  
  
|<span data-ttu-id="c99a6-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="c99a6-118">Attribute</span></span>|<span data-ttu-id="c99a6-119">Description</span><span class="sxs-lookup"><span data-stu-id="c99a6-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c99a6-120">name</span><span class="sxs-lookup"><span data-stu-id="c99a6-120">name</span></span>|<span data-ttu-id="c99a6-121">Chaîne qui spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="c99a6-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c99a6-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c99a6-122">Child Elements</span></span>  
 <span data-ttu-id="c99a6-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c99a6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c99a6-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c99a6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c99a6-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c99a6-125">Element</span></span>|<span data-ttu-id="c99a6-126">Description</span><span class="sxs-lookup"><span data-stu-id="c99a6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c99a6-127">\<variable ></span><span class="sxs-lookup"><span data-stu-id="c99a6-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="c99a6-128">Variable associée à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="c99a6-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c99a6-129">Notes</span><span class="sxs-lookup"><span data-stu-id="c99a6-129">Remarks</span></span>  
 <span data-ttu-id="c99a6-130">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="c99a6-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="c99a6-131">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="c99a6-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="c99a6-132">Vous pouvez utiliser la [ \<arguments >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) et [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) éléments à extraire une variable ou un argument à partir de toutes les activités dans un flux de travail. L’exemple suivant montre une requête d’état d’activité qui extrait des variables et arguments lorsque l’activité `Closed` enregistrement de suivi est émis.</span><span class="sxs-lookup"><span data-stu-id="c99a6-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="c99a6-133">Variables et arguments peuvent être extraits uniquement avec un objet ActivityStateRecord et par conséquent êtes abonnés au sein d’un suivi à l’aide du profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="c99a6-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c99a6-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c99a6-134">See Also</span></span>  
 <span data-ttu-id="c99a6-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c99a6-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c99a6-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c99a6-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c99a6-137">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="c99a6-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c99a6-138">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="c99a6-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
