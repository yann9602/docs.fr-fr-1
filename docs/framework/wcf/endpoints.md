---
title: Points de terminaison Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1771f5c69442ea4e95925339c28204663f78eb2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="2f315-102">Points de terminaison Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2f315-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="2f315-103">Toutes les communications avec un [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service s’effectue via le *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="2f315-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="2f315-104">Les points de terminaison fournissent au client l'accès aux fonctionnalités offertes par un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f315-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="2f315-105">Pour une vue d’ensemble sur la création d’un point de terminaison, consultez [vue d’ensemble de la création de point de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2f315-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="2f315-106">Chaque point de terminaison contient :</span><span class="sxs-lookup"><span data-stu-id="2f315-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="2f315-107">Une adresse qui indique où rechercher le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2f315-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="2f315-108">Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2f315-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="2f315-109">Un contrat qui identifie les méthodes disponibles.</span><span class="sxs-lookup"><span data-stu-id="2f315-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="2f315-110">Pour obtenir une description de la manière dont les parties individuelles d'un point de terminaison sont spécifiées, consultez :</span><span class="sxs-lookup"><span data-stu-id="2f315-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="2f315-111">Spécification d’une adresse de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="2f315-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="2f315-112">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="2f315-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="2f315-113">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="2f315-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="2f315-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2f315-114">In This Section</span></span>  
 [<span data-ttu-id="2f315-115">Vue d’ensemble de la création de points de terminaison</span><span class="sxs-lookup"><span data-stu-id="2f315-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="2f315-116">Décrit la structure d’un point de terminaison et explique comment définir un point de terminaison dans la configuration et dans le code, ainsi que la manière d’utiliser les points de terminaison par défaut, les liaisons et les comportements fournis par le runtime.</span><span class="sxs-lookup"><span data-stu-id="2f315-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="2f315-117">Spécification d’une adresse de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="2f315-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="2f315-118">Décrit comment la communication avec un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a lieu par l'intermédiaire des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2f315-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="2f315-119">Comment : créer un point de terminaison de Service dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="2f315-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="2f315-120">Montre comment créer un point de terminaison de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="2f315-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="2f315-121">Comment : créer un point de terminaison de Service dans le Code</span><span class="sxs-lookup"><span data-stu-id="2f315-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="2f315-122">Montre comment créer un point de terminaison de service dans le code.</span><span class="sxs-lookup"><span data-stu-id="2f315-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="2f315-123">Publication de points de terminaison de métadonnées</span><span class="sxs-lookup"><span data-stu-id="2f315-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="2f315-124">Montre comment publier des métadonnées en publiant des points de terminaison de métadonnées dans la configuration et dans le code.</span><span class="sxs-lookup"><span data-stu-id="2f315-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2f315-125">Référence</span><span class="sxs-lookup"><span data-stu-id="2f315-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="2f315-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="2f315-126">Related Sections</span></span>  
 [<span data-ttu-id="2f315-127">Cycle de vie de la programmation de base</span><span class="sxs-lookup"><span data-stu-id="2f315-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
