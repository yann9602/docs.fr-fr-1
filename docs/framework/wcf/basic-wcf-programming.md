---
title: Programmation WCF de base
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83404a56de68de8f8aec271c28e9896c4fa8702b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="a4ca7-102">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="a4ca7-102">Basic WCF Programming</span></span>
<span data-ttu-id="a4ca7-103">Cette section présente les notions de base de la création des applications [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4ca7-103">This section presents the fundamentals for creating [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4ca7-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a4ca7-104">In This Section</span></span>  
 [<span data-ttu-id="a4ca7-105">Cycle de vie de la programmation de base</span><span class="sxs-lookup"><span data-stu-id="a4ca7-105">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 <span data-ttu-id="a4ca7-106">Décrit le cycle de vie de conception, de construction et de déploiement des applications clientes et de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4ca7-106">Describes the lifecycle of designing, building, and deploying [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service and client applications.</span></span>  
  
 [<span data-ttu-id="a4ca7-107">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="a4ca7-107">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 <span data-ttu-id="a4ca7-108">Décrit comment concevoir et implémenter un contrat de service, choisir un modèle d’échange de messages, spécifier un contrat d’erreur, et d’autres aspects de base des services.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>  
  
 [<span data-ttu-id="a4ca7-109">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="a4ca7-109">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 <span data-ttu-id="a4ca7-110">Décrit comment configurer un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin de prendre en charge les spécifications de contrat, personnaliser le comportement d'exécution local et indiquer l'adresse pour publier le service.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-110">Describes how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>  
  
 [<span data-ttu-id="a4ca7-111">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="a4ca7-111">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 <span data-ttu-id="a4ca7-112">Décrit les notions de base d'hébergement des services dans une application.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-112">Describes the basics of hosting services in an application.</span></span>  
  
 [<span data-ttu-id="a4ca7-113">Génération de clients</span><span class="sxs-lookup"><span data-stu-id="a4ca7-113">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 <span data-ttu-id="a4ca7-114">Décrit comment obtenir les métadonnées à partir des services, les convertir en code client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], résoudre les problèmes de sécurité, et générer, configurer et héberger un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4ca7-114">Describes how to obtain metadata from services, convert that into [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code, handle security issues, and build, configure, and host an [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
 [<span data-ttu-id="a4ca7-115">Introduction à l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="a4ca7-115">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
 <span data-ttu-id="a4ca7-116">Décrit comment étendre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin de créer des solutions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-116">Describes how to extend [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to create custom solutions.</span></span>  
  
 [<span data-ttu-id="a4ca7-117">Démarrage rapide de la résolution des problèmes WCF</span><span class="sxs-lookup"><span data-stu-id="a4ca7-117">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 <span data-ttu-id="a4ca7-118">Décrit quelques-uns des problèmes les plus courants, les actions possibles pour les résoudre et où trouver davantage d'informations sur le problème rencontré.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>  
  
 [<span data-ttu-id="a4ca7-119">WCF et API web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a4ca7-119">WCF and ASP.NET Web API</span></span>](../../../docs/framework/wcf/wcf-and-aspnet-web-api.md)  
 <span data-ttu-id="a4ca7-120">Traite des deux technologies, de la manière dont elles sont en rapport l'une avec l'autre et indique quand les utiliser.</span><span class="sxs-lookup"><span data-stu-id="a4ca7-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4ca7-121">Référence</span><span class="sxs-lookup"><span data-stu-id="a4ca7-121">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="a4ca7-122">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a4ca7-122">Related Sections</span></span>  
 [<span data-ttu-id="a4ca7-123">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="a4ca7-123">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)  
  
 [<span data-ttu-id="a4ca7-124">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="a4ca7-124">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
  
 [<span data-ttu-id="a4ca7-125">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="a4ca7-125">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="a4ca7-126">Conseils et bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="a4ca7-126">Guidelines and Best Practices</span></span>](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
  
 [<span data-ttu-id="a4ca7-127">Outils Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a4ca7-127">Windows Communication Foundation Tools</span></span>](../../../docs/framework/wcf/tools.md)  
  
 [<span data-ttu-id="a4ca7-128">Exemples Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a4ca7-128">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [<span data-ttu-id="a4ca7-129">Prise en main</span><span class="sxs-lookup"><span data-stu-id="a4ca7-129">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
  
 [<span data-ttu-id="a4ca7-130">L’hébergement IIS à l’aide de Code Inline</span><span class="sxs-lookup"><span data-stu-id="a4ca7-130">IIS Hosting Using Inline Code</span></span>](../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)  
  
 [<span data-ttu-id="a4ca7-131">L’auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="a4ca7-131">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
