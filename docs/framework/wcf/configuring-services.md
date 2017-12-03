---
title: Configuration des services
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de970bf27fdf3365daa0ac515852a68d01a246eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-services"></a><span data-ttu-id="acec6-102">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="acec6-102">Configuring Services</span></span>
<span data-ttu-id="acec6-103">Une fois que vous avez conçu et implémenté votre contrat de service, vous êtes prêt à configurer votre service.</span><span class="sxs-lookup"><span data-stu-id="acec6-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="acec6-104">C'est à ce stade que vous définissez et personnalisez la manière dont votre service est exposé aux clients, notamment l'adresse de son emplacement, l'encodage du transport et du message qu'il utilise pour envoyer et recevoir des messages, et le type de sécurité qu'il nécessite.</span><span class="sxs-lookup"><span data-stu-id="acec6-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="acec6-105">La configuration utilisée dans ce scénario comprend toutes les méthodes, de manière impérative dans le code ou à l'aide d'un fichier de configuration, permettant de définir et de personnaliser les divers aspects d'un service, tels que la spécification de ses adresses de point de terminaison, les transports utilisés et ses méthodes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="acec6-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="acec6-106">Dans la pratique, l'écriture de la configuration est une partie importante de la programmation des applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="acec6-106">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acec6-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="acec6-107">In This Section</span></span>  
 [<span data-ttu-id="acec6-108">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="acec6-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="acec6-109">Depuis [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est fourni avec un nouveau modèle de configuration par défaut qui simplifie les spécifications de configuration de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="acec6-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="acec6-110">Si vous ne fournissez aucune configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour un service particulier, le runtime configure automatiquement votre service à l'aide des liaisons, des comportements et des points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="acec6-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="acec6-111">Configuration des services à l’aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="acec6-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="acec6-112">Un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] est configurable à l'aide de la technologie de configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acec6-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="acec6-113">Le plus souvent, les éléments XML sont ajoutés au fichier Web.config pour un site IIS (Internet Information Services) qui héberge un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acec6-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="acec6-114">Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison (les adresses réelles qui communiquent avec le service), à partir de chaque ordinateur individuel.</span><span class="sxs-lookup"><span data-stu-id="acec6-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="acec6-115">Liaisons</span><span class="sxs-lookup"><span data-stu-id="acec6-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="acec6-116">De plus, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclut plusieurs configurations fournies par le système courantes sous la forme de liaisons qui vous permettent de sélectionner rapidement les fonctionnalités les plus simples permettant à un client et à un service de communiquer, en particulier les transports, la sécurité et les encodages de message utilisés.</span><span class="sxs-lookup"><span data-stu-id="acec6-116">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="acec6-117">Points de terminaison</span><span class="sxs-lookup"><span data-stu-id="acec6-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="acec6-118">Toutes les communications avec un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service s’effectue via le *points de terminaison* du service.</span><span class="sxs-lookup"><span data-stu-id="acec6-118">All communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="acec6-119">Les points de terminaison contiennent le contrat, les informations de configuration spécifiées dans les liaisons, et les adresses qui indiquent où rechercher le service ou comment obtenir des informations sur le service.</span><span class="sxs-lookup"><span data-stu-id="acec6-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="acec6-120">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="acec6-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="acec6-121">À l'aide de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et des mécanismes de sécurité existants, vous pouvez implémenter la confidentialité, l'intégrité, l'authentification et l'autorisation dans tout service.</span><span class="sxs-lookup"><span data-stu-id="acec6-121">Using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="acec6-122">Vous pouvez aussi auditer les succès et les défaillances de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="acec6-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="acec6-123">Création de services interopérables avec le profil WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="acec6-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="acec6-124">Les exigences pour déployer un service interopérable avec les services et les clients sur n’importe quelle autre plateforme ou système d’exploitation sont définies dans la spécification WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="acec6-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="acec6-125">Référence</span><span class="sxs-lookup"><span data-stu-id="acec6-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="acec6-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="acec6-126">Related Sections</span></span>  
 [<span data-ttu-id="acec6-127">Cycle de vie de la programmation de base</span><span class="sxs-lookup"><span data-stu-id="acec6-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="acec6-128">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="acec6-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="acec6-129">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="acec6-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="acec6-130">Génération de clients</span><span class="sxs-lookup"><span data-stu-id="acec6-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="acec6-131">Introduction à l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="acec6-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="acec6-132">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="acec6-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="acec6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acec6-133">See Also</span></span>  
 [<span data-ttu-id="acec6-134">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="acec6-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="acec6-135">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="acec6-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="acec6-136">Informations détaillées sur les fonctionnalités de WCF</span><span class="sxs-lookup"><span data-stu-id="acec6-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
