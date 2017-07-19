---
title: "&lt;workflowInstanceManagement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;workflowInstanceManagement&gt;
Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <workflowInstanceManagement authorizedWindowsGroup=”” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|authorizedWindowsGroup||  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>