---
title: "Intégration d'AJAX et prise en charge de JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd5c84250349f4adaaac68a302d771280328a4e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="677a0-102">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="677a0-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="677a0-103">La prise en charge [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour ASP.NET AJAX (Asynchronous JavaScript and XML) et le format de données JSON (JavaScript Object Notation) permet aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'exposer des opérations aux clients AJAX.</span><span class="sxs-lookup"><span data-stu-id="677a0-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="677a0-104">Les clients AJAX sont les pages Web qui exécutent le code JavaScript et accèdent à ces services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="677a0-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="677a0-105">Les rubriques de cette section fournissent des informations sur cette prise en charge et sur la manière de l'implémenter.</span><span class="sxs-lookup"><span data-stu-id="677a0-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="677a0-106">ASP.NET AJAX et son intégration avec ASP.NET 2.0, consultez [vue d’ensemble de ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="677a0-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="677a0-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="677a0-107">In This Section</span></span>  
 [<span data-ttu-id="677a0-108">Création de services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="677a0-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="677a0-109">Décrit comment un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être exposé aux clients AJAX en ajoutant le point de terminaison AJAX approprié par le biais de la configuration ou à l'aide d'une fabrique de l'hôte de service personnalisé pour générer un hôte de service qui configure automatiquement le point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="677a0-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="677a0-110">Création de services WCF AJAX sans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="677a0-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="677a0-111">Décrit comment créer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans utiliser ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="677a0-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="677a0-112">Prise en charge du format JSON et d’autres formats de transfert de données</span><span class="sxs-lookup"><span data-stu-id="677a0-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="677a0-113">Décrit la prise en charge du format JSON utilisé en général (à la place de XML) pour la messagerie avec les services ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="677a0-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="677a0-114">Guide pratique pour migrer des services web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="677a0-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="677a0-115">Explique comment migrer un service Web ASP.NET compatible AJAX vers un service Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="677a0-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677a0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="677a0-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="677a0-117">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="677a0-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
