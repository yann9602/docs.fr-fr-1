---
title: "Hébergement du service de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a11e7e499f705f4aace791320057e04205db58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="801d0-102">Hébergement du service de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="801d0-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="801d0-103">À l’aide de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez créer un service qui expose des données en tant qu’un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] de flux.</span><span class="sxs-lookup"><span data-stu-id="801d0-103">By using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="801d0-104">Ce service de données est défini comme une classe qui hérite de <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="801d0-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="801d0-105">Cette classe fournit la fonctionnalité requise pour traiter les messages de demande, effectuer des mises à jour par rapport à la source de données et générer des messages de réponses, comme requis par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="801d0-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="801d0-106">Toutefois, un service de données ne peut pas lier à et écouter sur un socket de réseau pour les requêtes HTTP entrantes.</span><span class="sxs-lookup"><span data-stu-id="801d0-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="801d0-107">Pour ces fonctionnalités requises, le service de données s'appuie sur un composant d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="801d0-107">For this required functionality, the data service relies on a hosting component.</span></span>  
  
 <span data-ttu-id="801d0-108">L'hôte du service de données effectue les tâches suivantes pour le compte du service de données :</span><span class="sxs-lookup"><span data-stu-id="801d0-108">The data service host performs the following tasks on behalf of the data service:</span></span>  
  
-   <span data-ttu-id="801d0-109">Écoute les demandes et les transmet au service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-109">Listens for requests and routes these requests to the data service.</span></span>  
  
-   <span data-ttu-id="801d0-110">Crée une instance du service de données pour chaque demande.</span><span class="sxs-lookup"><span data-stu-id="801d0-110">Creates an instance of the data service for each request.</span></span>  
  
-   <span data-ttu-id="801d0-111">Demande au service de données de traiter la requête entrante.</span><span class="sxs-lookup"><span data-stu-id="801d0-111">Requests that the data service process the incoming request.</span></span>  
  
-   <span data-ttu-id="801d0-112">Envoie la réponse de la part du service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-112">Sends the response on behalf of the data service.</span></span>  
  
 <span data-ttu-id="801d0-113">Pour simplifier l’hébergement d’un service de données, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est conçu pour s’intégrer avec Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="801d0-113">To simplify hosting a data service, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="801d0-114">Le service de données fournit une implémentation WCF par défaut qui sert à l’hôte de service de données dans un [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="801d0-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="801d0-115">Vous pouvez donc héberger un service de données de l'une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="801d0-115">Therefore, you can host a data service in one of the following ways:</span></span>  
  
-   <span data-ttu-id="801d0-116">Dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="801d0-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
-   <span data-ttu-id="801d0-117">Dans une application managée qui prend en charge des services WCF auto-hébergés.</span><span class="sxs-lookup"><span data-stu-id="801d0-117">In a managed application that supports self-hosted WCF services.</span></span>  
  
-   <span data-ttu-id="801d0-118">Dans un autre hôte de service de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="801d0-118">In some other custom data service host.</span></span>  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="801d0-119">Hébergement de services de données dans une application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="801d0-119">Hosting a Data Service in an ASP.NET Application</span></span>  
 <span data-ttu-id="801d0-120">Lorsque vous utilisez la **ajouter un nouvel élément** boîte de dialogue dans Visual Studio pour définir un service de données dans une application ASP.NET, l’outil génère deux nouveaux fichiers dans le projet.</span><span class="sxs-lookup"><span data-stu-id="801d0-120">When you use the **Add New Item** dialog in Visual Studio to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="801d0-121">Le premier fichier a une extension `.svc` et indique à l'exécution WCF comment instancier le service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="801d0-122">Voici un exemple de ce fichier pour le service de données exemple Northwind créé lorsque vous effectuez la [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="801d0-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 <span data-ttu-id="801d0-123">Cette directive dit à l'application de créer l'hôte de service pour la classe de service de données nommée en utilisant la classe <xref:System.Data.Services.DataServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="801d0-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>  
  
 <span data-ttu-id="801d0-124">La page code-behind du fichier `.svc` contient la classe constituant l'implémentation du service de données lui-même, défini comme suit dans le cas de l'exemple de service de données Northwind :</span><span class="sxs-lookup"><span data-stu-id="801d0-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 <span data-ttu-id="801d0-125">Puisqu'un service de données se comporte comme un service WCF, le service de données s'intègre avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et suit le modèle de programmation Web WCF.</span><span class="sxs-lookup"><span data-stu-id="801d0-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="801d0-126">Pour plus d’informations, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) et [modèle de programmation WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="801d0-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>  
  
## <a name="self-hosted-wcf-services"></a><span data-ttu-id="801d0-127">Services WCF auto-hébergés</span><span class="sxs-lookup"><span data-stu-id="801d0-127">Self-Hosted WCF Services</span></span>  
 <span data-ttu-id="801d0-128">Car il intègre une implémentation WCF, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] auto-héberger un service de données comme un service WCF.</span><span class="sxs-lookup"><span data-stu-id="801d0-128">Because it incorporates a WCF implementation, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="801d0-129">Un service peut être auto-hébergé dans une application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], par exemple une application console.</span><span class="sxs-lookup"><span data-stu-id="801d0-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="801d0-130">La classe <xref:System.Data.Services.DataServiceHost>, qui hérite de <xref:System.ServiceModel.Web.WebServiceHost>, est utilisée pour instancier le service de données à une adresse spécifique.</span><span class="sxs-lookup"><span data-stu-id="801d0-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>  
  
 <span data-ttu-id="801d0-131">L'auto-hébergement peut être utilisé pour le développement et les tests parce qu'elle permet de simplifier le déploiement et le dépannage du service.</span><span class="sxs-lookup"><span data-stu-id="801d0-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="801d0-132">Toutefois, ce type d'hébergement ne fournit pas les fonctionnalités avancées d'hébergement et de gestion offertes par [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou par les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="801d0-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="801d0-133">Pour plus d’informations, consultez [hébergement dans une Application gérée](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="801d0-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="801d0-134">Définition d'un hôte de service de données personnalisé</span><span class="sxs-lookup"><span data-stu-id="801d0-134">Defining a Custom Data Service Host</span></span>  
 <span data-ttu-id="801d0-135">Dans les cas où l'implémentation hôte de WCF est trop restrictive, vous pouvez également définir un hôte personnalisé pour un service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="801d0-136">Toute classe qui implémente l'interface <xref:System.Data.Services.IDataServiceHost> peut être utilisée comme hôte de réseau pour un service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="801d0-137">Un hôte personnalisé doit implémenter l'interface <xref:System.Data.Services.IDataServiceHost> et pouvoir gérer les responsabilités de base suivantes de l'hôte de service de données :</span><span class="sxs-lookup"><span data-stu-id="801d0-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>  
  
-   <span data-ttu-id="801d0-138">Fournir le service de données avec le chemin d'accès racine du service.</span><span class="sxs-lookup"><span data-stu-id="801d0-138">Provide the data service with the service root path.</span></span>  
  
-   <span data-ttu-id="801d0-139">Traiter les informations d'en-tête de demande et de réponse à l'implémentation appropriée du membre <xref:System.Data.Services.IDataServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="801d0-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>  
  
-   <span data-ttu-id="801d0-140">Gérer les exceptions déclenchées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="801d0-140">Handle exceptions raised by the data service.</span></span>  
  
-   <span data-ttu-id="801d0-141">Valider les paramètres de la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="801d0-141">Validate parameters in the query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801d0-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="801d0-142">See Also</span></span>  
 [<span data-ttu-id="801d0-143">Définition de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="801d0-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="801d0-144">Exposition de vos données en tant que Service</span><span class="sxs-lookup"><span data-stu-id="801d0-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [<span data-ttu-id="801d0-145">Configuration du Service de données</span><span class="sxs-lookup"><span data-stu-id="801d0-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
