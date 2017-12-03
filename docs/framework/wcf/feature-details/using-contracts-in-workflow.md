---
title: Utilisation de contrats dans le workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c13da32e304e54d1826c6dd4ad83d5fbb17702a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-contracts-in-workflow"></a>Utilisation de contrats dans le workflow
Lorsque vous implémentez un service, vous définissez plusieurs contrats qui décrivent le service et les données qu'il envoie et reçoit. Les données sont représentées par des contrats de données et des contrats de message ; à la fois les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et de workflow utilisent des définitions de contrat de données et de contrat de messages dans le cadre des descriptions de service. Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service. Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge. Toutefois, dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même ; ils sont exposés dans les métadonnées par un processus nommé inférence de contrat.  
  
## <a name="contract-inference"></a>Inférence de contrat  
 Lorsqu'un service de workflow est hébergé à l'aide d'un objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la définition du workflow est examinée et un contrat est généré en fonction du jeu d'activités de messagerie qui se trouvent dans le workflow. En particulier, les activités et les propriétés suivantes sont utilisées pour générer le contrat :  
  
 Activité <xref:System.ServiceModel.Activities.Receive>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 Activité <xref:System.ServiceModel.Activities.SendReply>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 Activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
 Le résultat final de l'inférence de contrat est une description du service utilisant les mêmes structures de données que le service WCF et les contrats d'opération. Puis ces informations sont utilisées pour exposer WSDL pour le service de workflow.  
  
## <a name="see-also"></a>Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Activités de messagerie](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Comment : créer un Service de Workflow avec les activités de messagerie](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Guide pratique pour créer un service de workflow qui utilise un contrat de service existant](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
