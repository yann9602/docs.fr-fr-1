---
title: "Publication de points de terminaison de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64032fbc675e30e9f01a5db4d56ecc36574e08de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="4f652-102">Publication de points de terminaison de métadonnées</span><span class="sxs-lookup"><span data-stu-id="4f652-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="4f652-103">Les services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] publient les métadonnées à l'aide d'un ou de plusieurs points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4f652-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="4f652-104">La publication de métadonnées de service permet d'accéder à celles-ci à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX) et les requêtes HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="4f652-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="4f652-105">Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu'ils peuvent être ajoutés à un hôte de service via la configuration ou dans du code.</span><span class="sxs-lookup"><span data-stu-id="4f652-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="4f652-106">Pour activer la publication de points de terminaison de métadonnées, vous devez ajouter le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior> au service.</span><span class="sxs-lookup"><span data-stu-id="4f652-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f652-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4f652-107">In This Section</span></span>  
 [<span data-ttu-id="4f652-108">Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="4f652-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="4f652-109">Indique comment configurer un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin de publier les métadonnées et permettre ainsi aux clients de les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="4f652-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="4f652-110">Comment : publier les métadonnées d’un Service à l’aide de Code</span><span class="sxs-lookup"><span data-stu-id="4f652-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="4f652-111">Indique comment activer la publication de métadonnées pour un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans le code afin que les clients puissent les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="4f652-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f652-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f652-112">See Also</span></span>  
 [<span data-ttu-id="4f652-113">Publication des métadonnées</span><span class="sxs-lookup"><span data-stu-id="4f652-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
