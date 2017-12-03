---
title: '&lt;system.serviceModel&gt; de workflow'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 650cc0850b76cd6c855ea1f20b639752d7bef8cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt-of-workflow"></a><span data-ttu-id="df8b6-102">&lt;system.serviceModel&gt; de workflow</span><span class="sxs-lookup"><span data-stu-id="df8b6-102">&lt;system.serviceModel&gt; of workflow</span></span>
<span data-ttu-id="df8b6-103">Cette section de configuration contient tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="df8b6-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df8b6-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df8b6-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="df8b6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="df8b6-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="df8b6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df8b6-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="df8b6-107">Attributes</span></span>  
 <span data-ttu-id="df8b6-108">Aucun</span><span class="sxs-lookup"><span data-stu-id="df8b6-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df8b6-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="df8b6-109">Child Elements</span></span>  
  
|<span data-ttu-id="df8b6-110">Élément</span><span class="sxs-lookup"><span data-stu-id="df8b6-110">Element</span></span>|<span data-ttu-id="df8b6-111">Description</span><span class="sxs-lookup"><span data-stu-id="df8b6-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df8b6-112">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="df8b6-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="df8b6-113">Cette section définit les **serviceBehaviors** collection.</span><span class="sxs-lookup"><span data-stu-id="df8b6-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="df8b6-114">Chaque élément dans la collection définit des éléments de comportement consommés par des services.</span><span class="sxs-lookup"><span data-stu-id="df8b6-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="df8b6-115">Chaque élément de comportement est identifié par son unique **nom** attribut.</span><span class="sxs-lookup"><span data-stu-id="df8b6-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="df8b6-116">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="df8b6-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="df8b6-117">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="df8b6-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="df8b6-118">Pour plus d’informations dans le suivi de workflow et sa configuration, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi d’un flux de travail](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="df8b6-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df8b6-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="df8b6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="df8b6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="df8b6-120">Element</span></span>|<span data-ttu-id="df8b6-121">Description</span><span class="sxs-lookup"><span data-stu-id="df8b6-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df8b6-122">\<configuration></span><span class="sxs-lookup"><span data-stu-id="df8b6-122">\<configuration></span></span>|<span data-ttu-id="df8b6-123">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="df8b6-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
