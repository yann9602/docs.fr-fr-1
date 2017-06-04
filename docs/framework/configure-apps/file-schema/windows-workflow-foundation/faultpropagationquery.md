---
title: "&lt;faultPropagationQuery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;faultPropagationQuery&gt;
Représente une requête qui permet d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.  Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.  
  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|activityName|Chaîne qui spécifie le nom de l'activité de gestionnaire d'erreur qui a propagé l'erreur.  La valeur par défaut est \*, qui indique que des enregistrements de propagation d'erreur sont retournés pour toutes les activités.|  
|faultHandlerActivityName|Chaîne qui spécifie le nom de l'activité à l'origine de l'erreur.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<faultPropagationQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|Représente une liste des éléments de configuration qui permettent d'effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur.|  
  
## Voir aussi  
 [System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement](assetId:///System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.FaultPropagationQuery](assetId:///System.Activities.Tracking.FaultPropagationQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)