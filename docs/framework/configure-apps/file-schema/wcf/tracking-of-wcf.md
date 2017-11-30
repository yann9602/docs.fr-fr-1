---
title: '&lt;tracking&gt; de WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f0b3ad28c5d19ce812b714ef8e2ae92c14ab2a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lttrackinggt-of-wcf"></a>&lt;tracking&gt; de WCF
Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.  
  
 Pour plus d’informations dans le suivi de workflow et sa configuration, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [configuration du suivi d’un flux de travail](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 \<system.serviceModel >  
\<suivi >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <system.serviceModel>  <tracking>       <participants>       <add name="String"            profileName="String"           type="String" />      </participants>     <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>  
```
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<participants >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Une collection d’éléments de configuration définissent des participants qui s’abonnent aux enregistrements de suivi. Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des enregistrements de suivi (par exemple, ils peuvent choisir d'écrire dans un fichier).|  
|[\<trackingProfile >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Modèle de suivi permettant de filtrer les enregistrements de suivi émis d'une instance de flux de travail.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|system.ServiceModel|Élément racine de tous les éléments de configuration de flux de travail.|  
  
## <a name="remarks"></a>Remarques  
 Le suivi vous fournit la capacité d'examiner l'exécution d'un flux de travail. L'infrastructure de suivi de flux de travail instrumente un flux de travail pour émettre des enregistrements qui reflètent les principaux événements pendant l'exécution. Par exemple, lorsqu'une instance de flux de travail démarre ou se termine, des enregistrements de suivi sont émis. Le suivi peut également extraire des données métier pertinentes associées aux variables de flux de travail. Par exemple, si le flux de travail représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'enregistrement de suivi. En général, l'activation du suivi WF facilite les diagnostics ou les analyses d'entreprise à partir d'une exécution de flux de travail.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
