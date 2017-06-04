---
title: "&lt;workflowUnhandledException&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;workflowUnhandledException&gt;
Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <workflowUnhandledException action=”Abandon/AbandonAndSuspend/Cancel/Terminate” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|action|Chaîne qui spécifie l'action à entreprendre lorsqu'une exception non gérée se produit.  Cet attribut est de type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionaction>|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>