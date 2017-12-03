---
title: '&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d6edb83370f36b73955ab9d619c8b956f36a007e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;
Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.  
  
 Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel >  
\<suivi >  
\<trackingProfile >  
\<flux de travail >  
\<workflowInstanceQueries >  
\<workflowInstanceQuery >  
\<États >  
\<état >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<États >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.|  
  
## <a name="remarks"></a>Remarques  
 Les enregistrements retournés sont filtrés par états dans cette collection.  
  
 Les valeurs d'état possibles sont décrites dans le tableau suivant.  
  
|État|Description|  
|-----------|-----------------|  
|Abandonné|L'instance de flux de travail est abandonnée.|  
|Terminé|L'instance de flux de travail est terminée.|  
|Supprimé|L'instance de flux de travail est supprimée.|  
|Inactif|L'instance de workflow est inactive.|  
|Persistant|L'instance de flux de travail est persistante.|  
|Repris|L'instance de flux de travail est reprise.|  
|Démarré|L'instance de flux de travail est démarrée.|  
|UnhandledException|L'instance de flux de travail a rencontré une exception non gérée.|  
|Unloaded|L'instance de flux de travail est déchargée.|  
|Canceled|L'instance de flux de travail est annulée.|  
|Interrompu|L'instance de workflow est interrompue.|  
|Arrêté|L'instance de flux de travail est arrêtée.|  
|Unsuspended|L'instance de flux de travail est non interrompue.|  
  
## <a name="example"></a>Exemple  
 La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profils de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
