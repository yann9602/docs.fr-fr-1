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
ms.workload: dotnet
ms.openlocfilehash: 1ff40241bd48a4355738ca93ef2c80ceec55db11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="85bbf-102">Utilisation de contrats dans le workflow</span><span class="sxs-lookup"><span data-stu-id="85bbf-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="85bbf-103">Lorsque vous implémentez un service, vous définissez plusieurs contrats qui décrivent le service et les données qu'il envoie et reçoit.</span><span class="sxs-lookup"><span data-stu-id="85bbf-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="85bbf-104">Les données sont représentées par des contrats de données et des contrats de message ; à la fois les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et de workflow utilisent des définitions de contrat de données et de contrat de messages dans le cadre des descriptions de service.</span><span class="sxs-lookup"><span data-stu-id="85bbf-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="85bbf-105">Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service.</span><span class="sxs-lookup"><span data-stu-id="85bbf-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="85bbf-106">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="85bbf-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="85bbf-107">Toutefois, dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même ; ils sont exposés dans les métadonnées par un processus nommé inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="85bbf-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="85bbf-108">Inférence de contrat</span><span class="sxs-lookup"><span data-stu-id="85bbf-108">Contract Inference</span></span>  
 <span data-ttu-id="85bbf-109">Lorsqu'un service de workflow est hébergé à l'aide d'un objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la définition du workflow est examinée et un contrat est généré en fonction du jeu d'activités de messagerie qui se trouvent dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="85bbf-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="85bbf-110">En particulier, les activités et les propriétés suivantes sont utilisées pour générer le contrat :</span><span class="sxs-lookup"><span data-stu-id="85bbf-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="85bbf-111">Activité <xref:System.ServiceModel.Activities.Receive></span><span class="sxs-lookup"><span data-stu-id="85bbf-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="85bbf-112">Activité <xref:System.ServiceModel.Activities.SendReply></span><span class="sxs-lookup"><span data-stu-id="85bbf-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="85bbf-113">Activité <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="85bbf-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="85bbf-114">Le résultat final de l'inférence de contrat est une description du service utilisant les mêmes structures de données que le service WCF et les contrats d'opération.</span><span class="sxs-lookup"><span data-stu-id="85bbf-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="85bbf-115">Puis ces informations sont utilisées pour exposer WSDL pour le service de workflow.</span><span class="sxs-lookup"><span data-stu-id="85bbf-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85bbf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85bbf-116">See Also</span></span>  
 [<span data-ttu-id="85bbf-117">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="85bbf-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="85bbf-118">Activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="85bbf-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="85bbf-119">Guide pratique pour créer un service de workflow avec les activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="85bbf-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="85bbf-120">Guide pratique pour créer un service de workflow qui utilise un contrat de service existant</span><span class="sxs-lookup"><span data-stu-id="85bbf-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
