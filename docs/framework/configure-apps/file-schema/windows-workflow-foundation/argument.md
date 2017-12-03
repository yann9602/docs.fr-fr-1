---
title: '&lt;argument&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3625d3bf6aa415c34b9c05bebdec390bcb51f69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltargumentgt"></a><span data-ttu-id="9ebb4-102">&lt;argument&gt;</span><span class="sxs-lookup"><span data-stu-id="9ebb4-102">&lt;argument&gt;</span></span>
<span data-ttu-id="9ebb4-103">Élément de configuration qui représente un argument associé à une requête d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="9ebb4-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9ebb4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9ebb4-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9ebb4-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-106">\<tracking></span></span>  
<span data-ttu-id="9ebb4-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-107">\<trackingProfile></span></span>  
<span data-ttu-id="9ebb4-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-108">\<workflow></span></span>  
<span data-ttu-id="9ebb4-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-109">\<activityStateQueries></span></span>  
<span data-ttu-id="9ebb4-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-110">\<activityStateQuery></span></span>  
<span data-ttu-id="9ebb4-111">\<arguments ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-111">\<arguments></span></span>  
<span data-ttu-id="9ebb4-112">\<argument ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ebb4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ebb4-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ebb4-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ebb4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9ebb4-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ebb4-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ebb4-116">Attributes</span></span>  
  
|<span data-ttu-id="9ebb4-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ebb4-117">Attribute</span></span>|<span data-ttu-id="9ebb4-118">Description</span><span class="sxs-lookup"><span data-stu-id="9ebb4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ebb4-119">name</span><span class="sxs-lookup"><span data-stu-id="9ebb4-119">name</span></span>|<span data-ttu-id="9ebb4-120">Chaîne qui spécifie le nom de l'argument.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ebb4-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ebb4-121">Child Elements</span></span>  
 <span data-ttu-id="9ebb4-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ebb4-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ebb4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9ebb4-124">Élément</span><span class="sxs-lookup"><span data-stu-id="9ebb4-124">Element</span></span>|<span data-ttu-id="9ebb4-125">Description</span><span class="sxs-lookup"><span data-stu-id="9ebb4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ebb4-126">\<arguments ></span><span class="sxs-lookup"><span data-stu-id="9ebb4-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="9ebb4-127">Collection d’arguments associés à cette requête d’activité.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ebb4-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ebb4-128">Remarks</span></span>  
 <span data-ttu-id="9ebb4-129">Une fonctionnalité propre à ActivityStateQuery est la possibilité d’extraire des données lors du suivi de l’exécution d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9ebb4-130">Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9ebb4-131">Vous pouvez utiliser la [ \<arguments >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) et [ \<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) éléments à extraire une variable ou un argument à partir de toutes les activités dans un flux de travail. L’exemple suivant montre une requête d’état d’activité qui extrait des variables et arguments lorsque l’activité `Closed` enregistrement de suivi est émis.</span><span class="sxs-lookup"><span data-stu-id="9ebb4-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9ebb4-132">Variables et arguments peuvent être extraits uniquement avec un objet ActivityStateRecord et par conséquent êtes abonnés au sein d’un suivi à l’aide du profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="9ebb4-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ebb4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ebb4-133">See Also</span></span>  
 <span data-ttu-id="9ebb4-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9ebb4-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9ebb4-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9ebb4-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9ebb4-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="9ebb4-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9ebb4-137">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="9ebb4-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
