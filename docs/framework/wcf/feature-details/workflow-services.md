---
title: Services de workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8eeb446687b2aa75c90ec02995319fc5a0cbebf3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-services"></a><span data-ttu-id="b16eb-102">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="b16eb-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="b16eb-103"> vous permet de décrire entièrement un service basé sur le workflow de manière déclarative en XAML.</span><span class="sxs-lookup"><span data-stu-id="b16eb-103"> allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="b16eb-104">Vous pouvez définir un workflow qui l'implémente votre service et décrire les points de terminaison exposés par le service, le tout entièrement en XAML.</span><span class="sxs-lookup"><span data-stu-id="b16eb-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="b16eb-105">Les rubriques de cette section décrivent en détail le modèle de programmation qui prend en charge l'écriture de services de manière déclarative.</span><span class="sxs-lookup"><span data-stu-id="b16eb-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b16eb-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b16eb-106">In This Section</span></span>  
 [<span data-ttu-id="b16eb-107">Vue d’ensemble des Services de flux de travail</span><span class="sxs-lookup"><span data-stu-id="b16eb-107">Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services-overview.md)  
 <span data-ttu-id="b16eb-108">Décrit les composants impliqués dans la création et l'hébergement d'un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b16eb-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="b16eb-109">Activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="b16eb-109">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 <span data-ttu-id="b16eb-110">Décrit les activités qui permettent aux workflows d'envoyer et de recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="b16eb-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="b16eb-111">Comment : créer un Service de Workflow avec les activités de messagerie</span><span class="sxs-lookup"><span data-stu-id="b16eb-111">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="b16eb-112">Décrit comment utiliser des activités de messagerie pour créer un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b16eb-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="b16eb-113">Comment : Accéder à un Service à partir d’une Application de Workflow</span><span class="sxs-lookup"><span data-stu-id="b16eb-113">How To: Access a Service From a Workflow Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="b16eb-114">Explique comment appeler un service à partir d'une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="b16eb-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="b16eb-115">Corrélation</span><span class="sxs-lookup"><span data-stu-id="b16eb-115">Correlation</span></span>](../../../../docs/framework/wcf/feature-details/correlation.md)  
 <span data-ttu-id="b16eb-116">Explique comment la corrélation mappe des messages entre eux et aux instances.</span><span class="sxs-lookup"><span data-stu-id="b16eb-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="b16eb-117">Traitement des messages de non ordonnés</span><span class="sxs-lookup"><span data-stu-id="b16eb-117">Out-of-Order Message Processing</span></span>](../../../../docs/framework/wcf/feature-details/out-of-order-message-processing.md)  
 <span data-ttu-id="b16eb-118">Explique comment configurer un service pour accepter des messages désordonnés.</span><span class="sxs-lookup"><span data-stu-id="b16eb-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="b16eb-119">Comment : créer un Service de Workflow qui appelle un autre Workflow Service</span><span class="sxs-lookup"><span data-stu-id="b16eb-119">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 <span data-ttu-id="b16eb-120">Décrit comment appeler un service de workflow de façon synchrone à partir d’un autre service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b16eb-120">Describes how to synchronously call a workflow service from within another workflow service.</span></span>  
  
 [<span data-ttu-id="b16eb-121">Développement de services de workflow « contrat en premier »</span><span class="sxs-lookup"><span data-stu-id="b16eb-121">Contract First Workflow Service Development</span></span>](../../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="b16eb-122">Décrit la création d'un service de workflow basé sur un contrat de service existant.</span><span class="sxs-lookup"><span data-stu-id="b16eb-122">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="b16eb-123">Guide pratique pour créer un service de workflow qui utilise un contrat de service existant</span><span class="sxs-lookup"><span data-stu-id="b16eb-123">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="b16eb-124">Fournit un exemple pas à pas pour créer un service de workflow à l'aide d'un contrat de service existant.</span><span class="sxs-lookup"><span data-stu-id="b16eb-124">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="b16eb-125">Vue d’ensemble des Services de Workflow hébergement</span><span class="sxs-lookup"><span data-stu-id="b16eb-125">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 <span data-ttu-id="b16eb-126">Décrit les différents aspects de l'hébergement d'un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b16eb-126">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="b16eb-127">Utilisation de contrats dans le flux de travail</span><span class="sxs-lookup"><span data-stu-id="b16eb-127">Using Contracts in Workflow</span></span>](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  
 <span data-ttu-id="b16eb-128">Décrit les différents types de contrats et d'inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="b16eb-128">Describes the different types of contracts and contract inference.</span></span>
