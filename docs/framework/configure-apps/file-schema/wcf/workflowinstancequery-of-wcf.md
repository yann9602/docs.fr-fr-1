---
title: '&lt;workflowInstanceQuery&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63b56a927c16a746352e030df2a4de2ed28f7a09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="20c04-102">&lt;workflowInstanceQuery&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="20c04-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="20c04-103">Représente une requête qui effectue le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début et la fin d'un événement.</span><span class="sxs-lookup"><span data-stu-id="20c04-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="20c04-104">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="20c04-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="20c04-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="20c04-105">\<system.serviceModel></span></span>  
<span data-ttu-id="20c04-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="20c04-106">\<tracking></span></span>  
<span data-ttu-id="20c04-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="20c04-107">\<trackingProfile></span></span>  
<span data-ttu-id="20c04-108">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="20c04-108">\<workflow></span></span>  
<span data-ttu-id="20c04-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="20c04-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="20c04-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="20c04-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c04-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20c04-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20c04-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="20c04-112">Attributes and Elements</span></span>  
 <span data-ttu-id="20c04-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="20c04-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20c04-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="20c04-114">Attributes</span></span>  
 <span data-ttu-id="20c04-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="20c04-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20c04-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20c04-116">Child Elements</span></span>  
  
|<span data-ttu-id="20c04-117">Élément</span><span class="sxs-lookup"><span data-stu-id="20c04-117">Element</span></span>|<span data-ttu-id="20c04-118">Description</span><span class="sxs-lookup"><span data-stu-id="20c04-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20c04-119">\<États ></span><span class="sxs-lookup"><span data-stu-id="20c04-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="20c04-120">Collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="20c04-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20c04-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20c04-121">Parent Elements</span></span>  
  
|<span data-ttu-id="20c04-122">Élément</span><span class="sxs-lookup"><span data-stu-id="20c04-122">Element</span></span>|<span data-ttu-id="20c04-123">Description</span><span class="sxs-lookup"><span data-stu-id="20c04-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20c04-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="20c04-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="20c04-125">Représente une collection d’éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d’une instance de flux de travail, tels que le début ou la fin d’un événement.</span><span class="sxs-lookup"><span data-stu-id="20c04-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20c04-126">Notes</span><span class="sxs-lookup"><span data-stu-id="20c04-126">Remarks</span></span>  
 <span data-ttu-id="20c04-127">L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :</span><span class="sxs-lookup"><span data-stu-id="20c04-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="20c04-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="20c04-128">Example</span></span>  
 <span data-ttu-id="20c04-129">La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.</span><span class="sxs-lookup"><span data-stu-id="20c04-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20c04-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20c04-130">See Also</span></span>  
 <span data-ttu-id="20c04-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="20c04-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="20c04-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="20c04-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="20c04-133">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="20c04-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="20c04-134">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="20c04-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
