---
title: "WCF Data Services 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8a0ab816aa21082cf98462f5f9d7ffd20e4dcfd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="4e7b0-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="4e7b0-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4e7b0-103"> (autrefois appelé « ADO.NET Data Services ») est un composant du .NET Framework qui permet de créer des services qui utilisent le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer et consommer des données sur le web ou l’intranet en utilisant la sémantique de [REST (representational state transfer)](http://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="4e7b0-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="4e7b0-104"> expose des données comme des ressources adressables par des URI.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="4e7b0-105">Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="4e7b0-106"> utilise les conventions de relation d’entité dans [EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md) pour exposer des ressources en tant que jeux d’entités liés par des associations.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4e7b0-107"> utilise le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pour adresser et mettre à jour les ressources.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="4e7b0-108">Vous pouvez ainsi accéder à ces services à partir de tout client qui prend en charge [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="4e7b0-109"> permet de demander et d’écrire des données dans les ressources en utilisant des formats de transfert bien connus : Atom, jeu de normes pour l’échange et la mise à jour de données au format XML, et JSON (JavaScript Objet Notation), format d’échange de données textuel utilisé largement dans l’application AJAX.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4e7b0-110"> peut exposer des données issues de différentes sources, telles que des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="4e7b0-111">Les outils de Visual Studio simplifient la création de services basés sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide d'un modèle de données ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="4e7b0-112">Vous pouvez aussi créer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] reposant sur des classes CLR (Common Language Runtime) et même des données à liaison tardive ou non typées.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4e7b0-113"> inclut également un jeu de bibliothèques clientes, un pour les applications clientes .NET Framework générales et un autre spécifique aux applications Silverlight.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="4e7b0-114">Ces bibliothèques clientes fournissent un modèle de programmation basé sur des objets quand vous accédez à un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir de certains environnements tels que le .NET Framework et Silverlight.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="4e7b0-115">Où est-ce que je dois démarrer ?</span><span class="sxs-lookup"><span data-stu-id="4e7b0-115">Where Should I Start?</span></span>  
 <span data-ttu-id="4e7b0-116">Selon ce qui vous intéresse, choisissez de démarrer avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] depuis l'une des rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="4e7b0-117">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="4e7b0-118">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="4e7b0-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-119">Prise en main</span><span class="sxs-lookup"><span data-stu-id="4e7b0-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-120">Démarrage rapide avec Silverlight</span><span class="sxs-lookup"><span data-stu-id="4e7b0-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="4e7b0-121">Démarrage rapide avec Silverlight pour le développement de Windows Phone</span><span class="sxs-lookup"><span data-stu-id="4e7b0-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="4e7b0-122">Montrez-moi des exemples de code...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="4e7b0-123">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="4e7b0-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-124">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="4e7b0-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-125">Comment : lier les données aux éléments Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="4e7b0-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="4e7b0-126">Je souhaite en savoir plus sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="4e7b0-127">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="4e7b0-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="4e7b0-128">Site web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="4e7b0-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="4e7b0-129">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="4e7b0-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="4e7b0-130">OData : forum aux questions</span><span class="sxs-lookup"><span data-stu-id="4e7b0-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="4e7b0-131">Je souhaite regarder des vidéos...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="4e7b0-132">Guide du débutant sur WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="4e7b0-133">Vidéos du développeur WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="4e7b0-134">OData : site web développeurs</span><span class="sxs-lookup"><span data-stu-id="4e7b0-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="4e7b0-135">Je souhaite consulter des exemples de bout en bout</span><span class="sxs-lookup"><span data-stu-id="4e7b0-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="4e7b0-136">Exemples de documentation WCF Data Services dans la galerie d’exemples MSDN</span><span class="sxs-lookup"><span data-stu-id="4e7b0-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="4e7b0-137">Autres exemples WCF Data Services dans la galerie d’exemples MSDN</span><span class="sxs-lookup"><span data-stu-id="4e7b0-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="4e7b0-138">Kit de développement logiciel (SDK) OData</span><span class="sxs-lookup"><span data-stu-id="4e7b0-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="4e7b0-139">Qu'en est-il de l'intégration avec Visual Studio ?</span><span class="sxs-lookup"><span data-stu-id="4e7b0-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="4e7b0-140">Génération de la bibliothèque cliente du service de données</span><span class="sxs-lookup"><span data-stu-id="4e7b0-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-141">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="4e7b0-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="4e7b0-142">Fournisseur Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4e7b0-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="4e7b0-143">Comment puis-je l'utiliser ?</span><span class="sxs-lookup"><span data-stu-id="4e7b0-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="4e7b0-144">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="4e7b0-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="4e7b0-145">Livre blanc : présentation d’OData</span><span class="sxs-lookup"><span data-stu-id="4e7b0-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="4e7b0-146">Scénarios d’application</span><span class="sxs-lookup"><span data-stu-id="4e7b0-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="4e7b0-147">Je souhaite utiliser Silverlight...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="4e7b0-148">Démarrage rapide avec Silverlight</span><span class="sxs-lookup"><span data-stu-id="4e7b0-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="4e7b0-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="4e7b0-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="4e7b0-150">Prise en main de Silverlight</span><span class="sxs-lookup"><span data-stu-id="4e7b0-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="4e7b0-151">Je souhaite créer une application Windows Phone…</span><span class="sxs-lookup"><span data-stu-id="4e7b0-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="4e7b0-152">Démarrage rapide avec Silverlight pour le développement de Windows Phone</span><span class="sxs-lookup"><span data-stu-id="4e7b0-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="4e7b0-153">Client OData (Open Data Protocol) pour Windows Phone</span><span class="sxs-lookup"><span data-stu-id="4e7b0-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="4e7b0-154">Je souhaite utiliser LINQ...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="4e7b0-155">Interrogation du service de données</span><span class="sxs-lookup"><span data-stu-id="4e7b0-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-156">Considérations sur LINQ</span><span class="sxs-lookup"><span data-stu-id="4e7b0-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="4e7b0-157">Comment : exécuter les requêtes de services de données</span><span class="sxs-lookup"><span data-stu-id="4e7b0-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="4e7b0-158">J'ai encore besoin d'informations supplémentaires...</span><span class="sxs-lookup"><span data-stu-id="4e7b0-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="4e7b0-159">Blog de l’équipe WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="4e7b0-160">Ressources</span><span class="sxs-lookup"><span data-stu-id="4e7b0-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="4e7b0-161">Centre de développement WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="4e7b0-162">Site web Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="4e7b0-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="4e7b0-163">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4e7b0-163">In This Section</span></span>  
 [<span data-ttu-id="4e7b0-164">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="4e7b0-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="4e7b0-165">Fournit une vue d'ensemble des caractéristiques et des fonctionnalités disponibles dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="4e7b0-166">Nouveautés de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="4e7b0-167">Décrit les nouvelles fonctionnalités de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et la prise en charge des nouvelles fonctions de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="4e7b0-168">Prise en main</span><span class="sxs-lookup"><span data-stu-id="4e7b0-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="4e7b0-169">Décrit comment exposer et consommer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l’aide d’[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="4e7b0-170">Définition de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="4e7b0-171">Décrit comment créer et configurer un service de données qui expose des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e7b0-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="4e7b0-172">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4e7b0-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="4e7b0-173">Décrit comment utiliser des bibliothèques clientes pour consommer les flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] d’une application cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e7b0-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7b0-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e7b0-174">See Also</span></span>  
 [<span data-ttu-id="4e7b0-175">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="4e7b0-175">Representational State Transfer (REST)</span></span>](http://go.microsoft.com/fwlink/?LinkId=113919)
