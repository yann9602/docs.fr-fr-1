---
title: "Modèle de programmation HTTP Web WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f51ad4a228de0a4a2fae0fb325d045bb09263b3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="8b339-102">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="8b339-103">Le modèle de programmation HTTP Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permet aux développeurs d'exposer des opérations du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aux points de terminaison non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="8b339-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="8b339-104">Cette fonctionnalité est décrite en détail dans les rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="8b339-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b339-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8b339-105">In This Section</span></span>  
 [<span data-ttu-id="8b339-106">Vue d’ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="8b339-107">Offre une vue d'ensemble du modèle de programmation HTTP Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b339-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="8b339-108">Modèle objet de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="8b339-109">Présente le modèle de programmation HTTP Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="8b339-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="8b339-110">Comment : créer un Service Web HTTP de WCF de base</span><span class="sxs-lookup"><span data-stu-id="8b339-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="8b339-111">Décrit comment écrire un service de base qui expose un point de terminaison non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="8b339-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="8b339-112">Comment : exposer un contrat pour les Clients SOAP et Web</span><span class="sxs-lookup"><span data-stu-id="8b339-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="8b339-113">Décrit comment écrire un service de base qui expose le même contrat aux clients SOAP et non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="8b339-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="8b339-114">UriTemplate et UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="8b339-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="8b339-115">Décrit comment contrôler les URI à l'aide de <xref:System.UriTemplate> et <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="8b339-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="8b339-116">Mise en cache de la prise en charge des Services HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="8b339-117">Décrit comment spécifier un comportement de mise en cache pour un service HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="8b339-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="8b339-118">Mise en forme de HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="8b339-119">Décrit comment spécifier le format de la réponse à partir d'un service HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="8b339-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="8b339-120">Gestion d’erreurs HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="8b339-121">Décrit comment retourner des erreurs aux clients Web WCF, notamment les codes d'état HTTP et des données d'erreur supplémentaires définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b339-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="8b339-122">Appel d’un service de type REST à partir d’un service WCF</span><span class="sxs-lookup"><span data-stu-id="8b339-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="8b339-123">Décrit comment appeler un service REST à partir d'un service WCF.</span><span class="sxs-lookup"><span data-stu-id="8b339-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
