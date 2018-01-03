---
title: '&lt;behavior&gt; de &lt;serviceBehaviors&gt; de workflow'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ce452b97b31f1d552eda481d2f514857372e2d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="b057b-102">&lt;behavior&gt; de &lt;serviceBehaviors&gt; de workflow</span><span class="sxs-lookup"><span data-stu-id="b057b-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="b057b-103">Le **comportement** élément contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="b057b-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="b057b-104">Chaque comportement est indexé par son **nom**.</span><span class="sxs-lookup"><span data-stu-id="b057b-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="b057b-105">Services peuvent être liés à chaque comportement via ce nom à l’aide de la **behaviorConfiguration**attribut de la [ \<point de terminaison >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="b057b-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="b057b-106">Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b057b-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="b057b-107">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b057b-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="b057b-108">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="b057b-108">\<behaviors></span></span>  
<span data-ttu-id="b057b-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b057b-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="b057b-110">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="b057b-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b057b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b057b-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b057b-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b057b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b057b-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b057b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b057b-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="b057b-114">Attributes</span></span>  
  
|<span data-ttu-id="b057b-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="b057b-115">Attribute</span></span>|<span data-ttu-id="b057b-116">Description</span><span class="sxs-lookup"><span data-stu-id="b057b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b057b-117">name</span><span class="sxs-lookup"><span data-stu-id="b057b-117">name</span></span>|<span data-ttu-id="b057b-118">Chaîne unique qui contient le nom de configuration du comportement.</span><span class="sxs-lookup"><span data-stu-id="b057b-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="b057b-119">Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="b057b-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b057b-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b057b-120">Child Elements</span></span>  
  
|<span data-ttu-id="b057b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b057b-121">Element</span></span>|<span data-ttu-id="b057b-122">Description</span><span class="sxs-lookup"><span data-stu-id="b057b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b057b-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="b057b-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="b057b-124">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="b057b-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="b057b-125">\<routage ></span><span class="sxs-lookup"><span data-stu-id="b057b-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="b057b-126">Comportement de service qui permet à un service à utiliser à l’aide du suivi ETW un <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b057b-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="b057b-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="b057b-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="b057b-128">Un comportement de service qui permet de personnaliser le partage du cache niveaux, les paramètres du cache de fabrique de canal et les paramètres du cache de canal pour le flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’envoi d’activités de messagerie.</span><span class="sxs-lookup"><span data-stu-id="b057b-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="b057b-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="b057b-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="b057b-130">Comportement de service qui vous permet de configurer le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge les informations d’état persistantes pour les instances de service de flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b057b-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="b057b-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="b057b-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="b057b-132">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="b057b-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="b057b-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="b057b-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="b057b-134">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="b057b-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="b057b-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="b057b-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="b057b-136">Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b057b-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b057b-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b057b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="b057b-138">Élément</span><span class="sxs-lookup"><span data-stu-id="b057b-138">Element</span></span>|<span data-ttu-id="b057b-139">Description</span><span class="sxs-lookup"><span data-stu-id="b057b-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b057b-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b057b-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="b057b-141">Collection d’éléments de comportement de service.</span><span class="sxs-lookup"><span data-stu-id="b057b-141">A collection of service behavior elements.</span></span>|
