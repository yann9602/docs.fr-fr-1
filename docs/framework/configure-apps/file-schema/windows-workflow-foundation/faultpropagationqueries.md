---
title: "&lt;faultPropagationQueries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;faultPropagationQueries&gt;
Représente une collection de requêtes qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.  Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.  
  
 Pour plus d'informations sur les requêtes de modèle de suivi, consultez [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md).  
  
## Syntaxe  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
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
|[\<faultPropagationQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|Requête utilisée pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<workflow\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété **activityDefinitionId**.|  
  
## Voir aussi  
 [System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.FaultPropagationQuery](assetId:///System.Activities.Tracking.FaultPropagationQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)