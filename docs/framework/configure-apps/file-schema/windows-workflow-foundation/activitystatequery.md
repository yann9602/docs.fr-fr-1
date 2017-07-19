---
title: "&lt;activityStateQuery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;activityStateQuery&gt;
Représente une requête qui permet d'effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de flux de travail.  Par exemple, vous pouvez effectuer le suivi du nombre de fois où l'activité Envoyer un message se termine dans une instance de flux de travail.  Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité.  Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.  
  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|activityName|Chaîne qui spécifie le nom de l'activité sur lequel filtrer des instances <xref:System.Activities.Tracking.ActivityStateRecord>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<arguments\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|Collection d'arguments associés à cette requête d'activité.|  
|[\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Collection d'éléments de configuration qui contiennent les états de l'activité faisant l'objet d'un abonnement pour laquelle un enregistrement de suivi doit être émis.|  
|[\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Collection de variables associées à cette requête d'activité.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<faultPropagationQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.  La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.|  
  
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
 [System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement](assetId:///System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityStateQuery](assetId:///System.Activities.Tracking.ActivityStateQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)