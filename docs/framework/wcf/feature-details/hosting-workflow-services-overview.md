---
title: "Vue d'ensemble de l'hébergement de services de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c38cd352eb860982b9b1e3aa32daa7aeeee9ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-workflow-services-overview"></a>Vue d'ensemble de l'hébergement de services de workflow
Les services de workflow doivent être hébergés pour s'exécuter. <xref:System.ServiceModel.WorkflowServiceHost> est l'hôte de workflow prêt à l'emploi qui prend en charge plusieurs instances, la configuration et la messagerie WCF (bien que les workflows n'aient pas besoin d'utiliser la messagerie afin d'être hébergés).  Il permet également la persistance, le suivi et le contrôle de l'instance par un ensemble de comportements de service.  Tout comme le <xref:System.ServiceModel.ServiceHost> de WCF, <xref:System.ServiceModel.WorkflowServiceHost> peut être auto-hébergé dans n'importe quelle application .NET managée, ou hébergée sur le Web (comme un fichier .xamlx) dans IIS / WAS.  Les rubriques de cette section décrivent comment héberger un service de workflow.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Services d’hébergement de flux de travail](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 Décrit l'hébergement de services de workflow.  
  
 [Éléments internes hôte de Service de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Décrit comment <xref:System.ServiceModel.WorkflowServiceHost> traite les messages entrants.  
  
 [Extensibilité d’hôte de Service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Décrit comment étendre les fonctionnalités de l'hôte de service de workflow.  
  
 [Point de terminaison de contrôle du flux de travail](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Décrit comment définir un point de terminaison qui vous permet de créer des instances de workflow.  
  
 [Comment : héberger un workflow sans service dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Illustre comment héberger un workflow qui n'est pas un service de workflow dans IIS.  
  
 [Comment : héberger un Service de flux de travail avec Windows Server AppFabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Décrit comment héberger un service de workflow existant dans Windows Server App Fabric.  
  
 [Configuration de WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Décrit comment contrôler la persistance, le suivi, l'inactivité et le comportement en cas d'exception non gérée.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)
