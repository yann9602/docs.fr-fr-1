---
title: "Intégration à des applications COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0e625beaf20f6445099d8fb15cb175d3d71a860
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="364b7-102">Intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="364b7-102">Integrating with COM Applications</span></span>
<span data-ttu-id="364b7-103">Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être intégrés directement dans votre code existant à l'aide du moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="364b7-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="364b7-104">Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="364b7-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="364b7-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="364b7-105">In This Section</span></span>  
 [<span data-ttu-id="364b7-106">Intégration de la vue d’ensemble des Applications COM</span><span class="sxs-lookup"><span data-stu-id="364b7-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="364b7-107">Fournit une vue d'ensemble des principales phases du processus d'intégration.</span><span class="sxs-lookup"><span data-stu-id="364b7-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="364b7-108">Comment : inscrire et configurer un Moniker de Service</span><span class="sxs-lookup"><span data-stu-id="364b7-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="364b7-109">Pour utiliser le moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une application COM, inscrivez les types attribués requis avec COM et configurez l'application COM et le moniker avec la configuration de liaison requise.</span><span class="sxs-lookup"><span data-stu-id="364b7-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="364b7-110">Comment : utiliser le Moniker de Service Windows Communication Foundation sans inscription</span><span class="sxs-lookup"><span data-stu-id="364b7-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="364b7-111">Explique comment obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) ou à partir d'un point de terminaison WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="364b7-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="364b7-112">Comment : utiliser un Moniker de Service avec des contrats WSDL</span><span class="sxs-lookup"><span data-stu-id="364b7-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="364b7-113">Décrit comment appeler un exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un moniker WSDL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="364b7-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="364b7-114">Comment : utiliser un Moniker de Service avec les contrats d’échange de métadonnées</span><span class="sxs-lookup"><span data-stu-id="364b7-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="364b7-115">Décrit comment appeler un exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui spécifie un point de terminaison Mex.</span><span class="sxs-lookup"><span data-stu-id="364b7-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="364b7-116">Comment : spécifier des informations d’identification de sécurité de canal</span><span class="sxs-lookup"><span data-stu-id="364b7-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="364b7-117">Le moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'interface `IChannelCredentials` qui prévoit une plage de méthodes secondaires pour spécifier des informations d'identification de canal.</span><span class="sxs-lookup"><span data-stu-id="364b7-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="364b7-118">Référence</span><span class="sxs-lookup"><span data-stu-id="364b7-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="364b7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="364b7-119">See Also</span></span>  
 [<span data-ttu-id="364b7-120">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="364b7-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
