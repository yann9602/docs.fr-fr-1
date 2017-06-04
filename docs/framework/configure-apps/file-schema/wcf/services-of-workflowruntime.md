---
title: "&lt;services&gt; de &lt;workflowRuntime&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 219a05b1-f573-45c9-849b-e86bc373b62f
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;services&gt; de &lt;workflowRuntime&gt;
Représente la collection de services à ajouter au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.  Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Les services spécifiés dans la collection sont initialisés par le moteur d'exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.  Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.  Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
## Voir aussi  
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>   
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 [Workflow Configuration Files](http://msdn.microsoft.com/fr-fr/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)