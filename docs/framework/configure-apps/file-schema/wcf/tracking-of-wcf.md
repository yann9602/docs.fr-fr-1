---
title: '&lt;tracking&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7475c4a083d27e9c34e3662393981297c93580f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttrackinggt-of-wcf"></a><span data-ttu-id="64849-102">&lt;tracking&gt; de WCF</span><span class="sxs-lookup"><span data-stu-id="64849-102">&lt;tracking&gt; of WCF</span></span>
<span data-ttu-id="64849-103">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="64849-104">Pour plus d’informations dans le suivi de workflow et sa configuration, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi d’un flux de travail](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="64849-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="64849-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="64849-105">\<system.serviceModel></span></span>  
<span data-ttu-id="64849-106">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="64849-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64849-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64849-107">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>       <participants>       <add name="String"            profileName="String"           type="String" />      </participants>     <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64849-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64849-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64849-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64849-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64849-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="64849-110">Attributes</span></span>  
 <span data-ttu-id="64849-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64849-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64849-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64849-112">Child Elements</span></span>  
  
|<span data-ttu-id="64849-113">Élément</span><span class="sxs-lookup"><span data-stu-id="64849-113">Element</span></span>|<span data-ttu-id="64849-114">Description</span><span class="sxs-lookup"><span data-stu-id="64849-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64849-115">\<participants ></span><span class="sxs-lookup"><span data-stu-id="64849-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="64849-116">Une collection d’éléments de configuration définissent des participants qui s’abonnent aux enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="64849-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="64849-117">Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi (par exemple, ils peuvent choisir d'écrire dans un fichier).</span><span class="sxs-lookup"><span data-stu-id="64849-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="64849-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="64849-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="64849-119">Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64849-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64849-120">Parent Elements</span></span>  
  
|<span data-ttu-id="64849-121">Élément</span><span class="sxs-lookup"><span data-stu-id="64849-121">Element</span></span>|<span data-ttu-id="64849-122">Description</span><span class="sxs-lookup"><span data-stu-id="64849-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64849-123">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="64849-123">system.ServiceModel</span></span>|<span data-ttu-id="64849-124">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64849-125">Notes</span><span class="sxs-lookup"><span data-stu-id="64849-125">Remarks</span></span>  
 <span data-ttu-id="64849-126">Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="64849-127">L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="64849-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="64849-128">Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="64849-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="64849-129">Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="64849-130">Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="64849-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="64849-131">En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="64849-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64849-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64849-132">See Also</span></span>  
 <span data-ttu-id="64849-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64849-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="64849-134">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="64849-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
