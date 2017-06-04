---
title: "Vue d&#39;ensemble de l&#39;h&#233;bergement de services de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Vue d&#39;ensemble de l&#39;h&#233;bergement de services de workflow
Les services de workflow doivent être hébergés pour s'exécuter.<xref:System.ServiceModel.WorkflowServiceHost> est l'hôte de workflow prêt à l'emploi qui prend en charge plusieurs instances, la configuration et la messagerie WCF \(bien que les workflows n'aient pas besoin d'utiliser la messagerie afin d'être hébergés\).Il permet également la persistance, le suivi et le contrôle de l'instance par un ensemble de comportements de service.Tout comme le <xref:System.ServiceModel.ServiceHost> de WCF, <xref:System.ServiceModel.WorkflowServiceHost> peut être auto\-hébergé dans n'importe quelle application .NET managée, ou hébergée sur le Web \(comme un fichier .xamlx\) dans IIS \/ WAS.Les rubriques de cette section décrivent comment héberger un service de workflow.  
  
## Dans cette section  
 [Hébergement de services de workflow](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 Décrit l'hébergement de services de workflow.  
  
 [Éléments internes de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Décrit comment <xref:System.ServiceModel.WorkflowServiceHost> traite les messages entrants.  
  
 [Extensibilité de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Décrit comment étendre les fonctionnalités de l'hôte de service de workflow.  
  
 [Point de terminaison de contrôle de workflow](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Décrit comment définir un point de terminaison qui vous permet de créer des instances de workflow.  
  
 [Procédure : héberger un workflow sans service dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Illustre comment héberger un workflow qui n'est pas un service de workflow dans IIS.  
  
 [Procédure : héberger un service de workflow avec Windows Server App Fabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Décrit comment héberger un service de workflow existant dans Windows Server App Fabric.  
  
 [Configuration de WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Décrit comment contrôler la persistance, le suivi, l'inactivité et le comportement en cas d'exception non gérée.  
  
## Référence  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## Rubriques connexes  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)