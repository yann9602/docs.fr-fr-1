---
title: "&lt;Variable&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;Variable&gt;
Représente une collection de variables associées à cette requête d'activité.  
  
 Pour plus d'informations sur les requêtes de modèle de suivi, consultez [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md).  
  
## Syntaxe  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <activityStateQueries>  
             <activityStateQuery activityName="String" />  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Chaîne qui spécifie le nom de la variable.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<variable\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|Variable associée à une requête d'état d'activité.|  
  
## Notes  
 Une fonctionnalité propre à ActivityStateQuery est la possibilité d'extraire des données lors du suivi de l'exécution d'un flux de travail.  Vous disposez ainsi d'un contexte supplémentaire lors de l'accès à une post\-exécution d'enregistrements de suivi.  Vous pouvez utiliser les éléments [\<arguments\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) et [\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) pour extraire une variable ou un argument d'une activité dans un flux de travail. L'exemple suivant présente une requête d'état d'activité qui extrait des variables et des arguments lors de l'émission de l'enregistrement de suivi `Closed` de l'activité.  L'extraction des variables et des arguments n'est possible qu'avec un ActivityStateRecord, l'abonnement à ces derniers s'effectue donc dans un modèle de suivi à l'aide de [\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).  
  
```  
  
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
  
## Voir aussi  
 [System.ServiceModel.Activities.Tracking.Configuration.VariableElement](assetId:///System.ServiceModel.Activities.Tracking.Configuration.VariableElement?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityStateQuery](assetId:///System.Activities.Tracking.ActivityStateQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)