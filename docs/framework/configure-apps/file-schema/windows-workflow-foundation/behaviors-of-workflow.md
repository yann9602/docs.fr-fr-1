---
title: "&lt;behaviors&gt; de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;behaviors&gt; de workflow
Cet élément contient la collection **serviceBehaviors**.  Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.  Chaque élément de comportement est identifié par son attribut **name** unique.  
  
 \<system.ServiceModel\>  
  
## Syntaxe  
  
```  
  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 None  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Élément racine de tous les éléments de configuration de flux de travail.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>   
 [Configuration et extension de l'exécution à l'aide de comportements](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)