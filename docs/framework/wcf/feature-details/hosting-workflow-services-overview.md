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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06012da95660fb4dc20d034c2d1691afad12037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="8fecf-102">Vue d'ensemble de l'hébergement de services de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="8fecf-103">Les services de workflow doivent être hébergés pour s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="8fecf-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="8fecf-104"><xref:System.ServiceModel.WorkflowServiceHost> est l'hôte de workflow prêt à l'emploi qui prend en charge plusieurs instances, la configuration et la messagerie WCF (bien que les workflows n'aient pas besoin d'utiliser la messagerie afin d'être hébergés).</span><span class="sxs-lookup"><span data-stu-id="8fecf-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="8fecf-105">Il permet également la persistance, le suivi et le contrôle de l'instance par un ensemble de comportements de service.</span><span class="sxs-lookup"><span data-stu-id="8fecf-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="8fecf-106">Tout comme le <xref:System.ServiceModel.ServiceHost> de WCF, <xref:System.ServiceModel.WorkflowServiceHost> peut être auto-hébergé dans n'importe quelle application .NET managée, ou hébergée sur le Web (comme un fichier .xamlx) dans IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="8fecf-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="8fecf-107">Les rubriques de cette section décrivent comment héberger un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="8fecf-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fecf-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8fecf-108">In This Section</span></span>  
 [<span data-ttu-id="8fecf-109">Hébergement de services de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="8fecf-110">Décrit l'hébergement de services de workflow.</span><span class="sxs-lookup"><span data-stu-id="8fecf-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="8fecf-111">Éléments internes de l’hôte du service de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="8fecf-112">Décrit comment <xref:System.ServiceModel.WorkflowServiceHost> traite les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="8fecf-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="8fecf-113">Extensibilité de l’hôte du service de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="8fecf-114">Décrit comment étendre les fonctionnalités de l'hôte de service de workflow.</span><span class="sxs-lookup"><span data-stu-id="8fecf-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="8fecf-115">Point de terminaison de contrôle de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="8fecf-116">Décrit comment définir un point de terminaison qui vous permet de créer des instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="8fecf-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="8fecf-117">Guide pratique pour héberger un workflow sans service dans IIS</span><span class="sxs-lookup"><span data-stu-id="8fecf-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="8fecf-118">Illustre comment héberger un workflow qui n'est pas un service de workflow dans IIS.</span><span class="sxs-lookup"><span data-stu-id="8fecf-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="8fecf-119">Guide pratique pour héberger un service de workflow avec Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="8fecf-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="8fecf-120">Décrit comment héberger un service de workflow existant dans Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="8fecf-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="8fecf-121">Configuration de WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8fecf-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="8fecf-122">Décrit comment contrôler la persistance, le suivi, l'inactivité et le comportement en cas d'exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="8fecf-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8fecf-123">Référence</span><span class="sxs-lookup"><span data-stu-id="8fecf-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="8fecf-124">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8fecf-124">Related Sections</span></span>  
 [<span data-ttu-id="8fecf-125">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="8fecf-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
