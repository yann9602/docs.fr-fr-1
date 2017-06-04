---
title: "&lt;system.serviceModel&gt; de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;system.serviceModel&gt; de workflow
Cette section de configuration contient tous les éléments de configuration de flux de travail.  
  
## Syntaxe  
  
```  
  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel=”Integer” />  
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
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 None  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|Cette section définit la collection **serviceBehaviors**.  Chaque élément dans la collection définit des éléments de comportement consommés par des services.  Chaque élément de comportement est identifié par son attribut **name** unique.|  
|[\<tracking\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.<br /><br /> Pour plus d'informations sur le suivi du flux de travail et sa configuration, consultez [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md) et [Configuration du suivi d'un workflow](../../../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md).|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<configuration\>|Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.|