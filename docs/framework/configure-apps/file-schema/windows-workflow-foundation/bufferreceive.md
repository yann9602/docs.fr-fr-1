---
title: "&lt;bufferReceive&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;bufferReceive&gt;
Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <bufferReceive maxPendingMessagesPerChannel=”Integer” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|maxPendingMessagesPerChannel|Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.  La valeur par défaut est 512.  Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>