---
title: "Définition des services de données WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e66c26c12f3f62ee61e02e16318e747793ff927
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="b5f28-102">Définition des services de données WCF</span><span class="sxs-lookup"><span data-stu-id="b5f28-102">Defining WCF Data Services</span></span>
<span data-ttu-id="b5f28-103">Cette section décrit comment créer et configurer [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour exposer des données comme un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux.</span><span class="sxs-lookup"><span data-stu-id="b5f28-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b5f28-104">les étapes de base requises pour créer un service de données, consultez [exposition de vos données en tant que Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b5f28-104"> the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5f28-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b5f28-105">In This Section</span></span>  
 [<span data-ttu-id="b5f28-106">Configuration du Service de données</span><span class="sxs-lookup"><span data-stu-id="b5f28-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="b5f28-107">Décrit les options de configuration du service de données fournies par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f28-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="b5f28-108">Fournisseurs de Services de données</span><span class="sxs-lookup"><span data-stu-id="b5f28-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="b5f28-109">Décrit les modèles de fournisseur pour l'exposition de données sous la forme d'un service de données.</span><span class="sxs-lookup"><span data-stu-id="b5f28-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="b5f28-110">Opérations de service</span><span class="sxs-lookup"><span data-stu-id="b5f28-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="b5f28-111">Décrit comment définir des opérations de service qui exposent des méthodes sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b5f28-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="b5f28-112">Personnalisation de flux</span><span class="sxs-lookup"><span data-stu-id="b5f28-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="b5f28-113">Décrit comment créer un mappage entre les entités du modèle de données défini par le fournisseur de services de données et les éléments du flux de données.</span><span class="sxs-lookup"><span data-stu-id="b5f28-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="b5f28-114">Intercepteurs</span><span class="sxs-lookup"><span data-stu-id="b5f28-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="b5f28-115">Décrit comment définir des méthodes d'intercepteur pour appliquer une logique métier personnalisée sur des requêtes au service de données.</span><span class="sxs-lookup"><span data-stu-id="b5f28-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="b5f28-116">Développement et le déploiement des Services de données WCF</span><span class="sxs-lookup"><span data-stu-id="b5f28-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="b5f28-117">Explique comment développer et déployer un service de données à l'aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5f28-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="b5f28-118">Sécurisation de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b5f28-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="b5f28-119">Décrit l'authentification et l'autorisation du service de données et fournit des considérations sur la sécurité.</span><span class="sxs-lookup"><span data-stu-id="b5f28-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="b5f28-120">Qui héberge le Service de données</span><span class="sxs-lookup"><span data-stu-id="b5f28-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="b5f28-121">Décrit comment sélectionner un hôte pour votre service de données.</span><span class="sxs-lookup"><span data-stu-id="b5f28-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="b5f28-122">Gestion des versions du Service de données</span><span class="sxs-lookup"><span data-stu-id="b5f28-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="b5f28-123">Décrit comment utiliser différentes versions du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f28-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="b5f28-124">Détails d’implémentation de protocole des Services de données WCF</span><span class="sxs-lookup"><span data-stu-id="b5f28-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="b5f28-125">Décrit les fonctionnalités facultatives du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] qui ne sont pas encore implémentées par WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="b5f28-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f28-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5f28-126">See Also</span></span>  
 [<span data-ttu-id="b5f28-127">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="b5f28-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="b5f28-128">L’accès aux ressources de Service de données</span><span class="sxs-lookup"><span data-stu-id="b5f28-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="b5f28-129">Prise en main</span><span class="sxs-lookup"><span data-stu-id="b5f28-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
