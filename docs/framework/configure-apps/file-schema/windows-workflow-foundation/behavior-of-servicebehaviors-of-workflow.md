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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 81dfde9a4b75caeea263cc0809f450cbc0c9a5e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a>&lt;behavior&gt; de &lt;serviceBehaviors&gt; de workflow
Le **comportement** élément contient une collection de paramètres pour le comportement d’un service. Chaque comportement est indexé par son **nom**. Services peuvent être liés à chaque comportement via ce nom à l’aide de la **behaviorConfiguration**attribut de la [ \<point de terminaison >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) élément. Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.  
  
\<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement. Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<bufferReceive >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.|  
|[\<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Comportement de service qui permet à un service à utiliser à l’aide du suivi ETW un <xref:System.Activities.Tracking.EtwTrackingParticipant>.|  
|[\<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|Un comportement de service qui permet de personnaliser le partage du cache niveaux, les paramètres du cache de fabrique de canal et les paramètres du cache de canal pour le flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’envoi d’activités de messagerie.|  
|[\<sqlWorkflowInstanceStore >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|Comportement de service qui vous permet de configurer le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge les informations d’état persistantes pour les instances de service de flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.|  
|[\<workflowIdle >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.|  
|[\<workflowInstanceManagement >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.|  
|[\<workflowUnhandledException >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Collection d’éléments de comportement de service.|
