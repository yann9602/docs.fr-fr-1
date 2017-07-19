---
title: "&lt;activityStateQueries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;activityStateQueries&gt;
Représente une collection de requêtes qui permettent d'effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow.  Par exemple, vous pouvez effectuer le suivi du nombre de fois où l'activité Envoyer un message se termine dans une instance de flux de travail.  Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.  Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.  
  
 Pour plus d'informations sur les requêtes de modèle de suivi, consultez [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md).  
  
## Syntaxe  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <activityStateQueries>  
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
       </workflow>  
   </trackingProfile>  
</tracking>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<workflow\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété **activityDefinitionId**.|  
  
## Voir aussi  
 [System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityStateQuery](assetId:///System.Activities.Tracking.ActivityStateQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)