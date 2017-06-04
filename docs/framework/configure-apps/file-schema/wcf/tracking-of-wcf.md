---
title: "&lt;tracking&gt; de WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;tracking&gt; de WCF
Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.  
  
 Pour plus d'informations sur le suivi du flux de travail et sa configuration, consultez [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md) et [Configuration du suivi d'un workflow](../../../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md).  
  
## Syntaxe  
  
```vb  
  
<system.serviceModel>  
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
</system.serviceModel>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Collection d'éléments de configuration qui définissent des participants qui s'abonnent à des enregistrements de suivi.  Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi \(par exemple, ils peuvent choisir d'écrire dans un fichier\).|  
|[\<trackingProfile\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|system.ServiceModel|Élément racine de tous les éléments de configuration de flux de travail.|  
  
## Notes  
 Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail.  L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution.  Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis.  Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail.  Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi.  En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.  
  
## Voir aussi  
 [System.ServiceModel.Activities.Tracking.Configuration.TrackingSection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)