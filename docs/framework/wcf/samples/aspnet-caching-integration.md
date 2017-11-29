---
title: ASP.NET Caching Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8830f1c19b7a91d6c22d3b5955624c7d8a86f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="07564-102">ASP.NET Caching Integration</span><span class="sxs-lookup"><span data-stu-id="07564-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="07564-103">Cet exemple montre comment utiliser le cache de sortie ASP.NET avec le modèle de programmation HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="07564-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="07564-104">Consultez le [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample pour une version autonome de ce scénario présente l’implémentation de service en profondeur.</span><span class="sxs-lookup"><span data-stu-id="07564-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="07564-105">Cette rubrique met l’accent sur la fonctionnalité d’intégration du cache de sortie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="07564-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="07564-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="07564-106">Demonstrates</span></span>  
 <span data-ttu-id="07564-107">Intégration au cache de sortie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="07564-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07564-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="07564-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07564-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="07564-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07564-110">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="07564-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07564-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="07564-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="07564-112">Discussion</span><span class="sxs-lookup"><span data-stu-id="07564-112">Discussion</span></span>  
 <span data-ttu-id="07564-113">L'exemple emploie l'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pour utiliser la mise en cache de sortie ASP.NET avec le service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07564-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="07564-114">L'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est appliqué aux opérations de service et fournit le nom d'un profil de cache dans un fichier de configuration qui doit être appliqué aux réponses de l'opération donnée.</span><span class="sxs-lookup"><span data-stu-id="07564-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="07564-115">Dans le fichier Service.cs de l’exemple de projet de Service, à la fois le `GetCustomer` et `GetCustomers` opérations sont marquées avec le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, qui fournit le nom de profil de cache « CacheFor60Seconds ».</span><span class="sxs-lookup"><span data-stu-id="07564-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="07564-116">Dans le fichier Web.config du projet de Service, le profil de cache « CacheFor60Seconds » est fourni sous la <`caching`> élément de <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="07564-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="07564-117">Pour ce profil de cache, la valeur de la `duration` attribut étant « 60 », les réponses associées à ce profil sont mises en cache dans le cache de sortie ASP.NET pendant 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="07564-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="07564-118">En outre, pour ce profil de cache, le `varmByParam` attribut est défini sur « format » demande avec des valeurs différentes pour le `format` requête paramètre de chaîne ont leurs réponses mises en cache séparément.</span><span class="sxs-lookup"><span data-stu-id="07564-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="07564-119">D’Enfin, le profil de cache `varyByHeader` attribut est défini sur « Accepter », pour que les demandes avec différentes valeurs d’en-tête Accept aient leurs réponses mises en cache séparément.</span><span class="sxs-lookup"><span data-stu-id="07564-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="07564-120">Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="07564-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="07564-121">Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF.</span><span class="sxs-lookup"><span data-stu-id="07564-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="07564-122">Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme la fabrique de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="07564-122">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="07564-123">Autres exemples du SDK (telles que la [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) exemple et [la sélection automatique du Format](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemple) illustrent l’utilisation de ces classes pour communiquer avec un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="07564-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="07564-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="07564-124">To run the sample</span></span>  
 <span data-ttu-id="07564-125">Cet exemple est composé de trois projets :</span><span class="sxs-lookup"><span data-stu-id="07564-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="07564-126">**Service**: projet d’Application Web qui inclut un service HTTP WCF hébergé dans ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="07564-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="07564-127">**Client**: un projet d’application console qui passe des appels au service.</span><span class="sxs-lookup"><span data-stu-id="07564-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="07564-128">**Common**: une bibliothèque partagée qui contient le type de client utilisé par le client et le service.</span><span class="sxs-lookup"><span data-stu-id="07564-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="07564-129">Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="07564-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="07564-130">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="07564-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="07564-131">Ouvrez la solution de l'exemple ASP.NET Caching Integration.</span><span class="sxs-lookup"><span data-stu-id="07564-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="07564-132">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="07564-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="07564-133">Si le **l’Explorateur de solutions** fenêtre n’est pas déjà ouverte, appuyez sur CTRL + W + S.</span><span class="sxs-lookup"><span data-stu-id="07564-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="07564-134">À partir de la **l’Explorateur de solutions** fenêtre, le bouton droit sur le **Service** de projet et sélectionnez **démarrer une nouvelle Instance**.</span><span class="sxs-lookup"><span data-stu-id="07564-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="07564-135">Cette opération lance le serveur de développement ASP.NET, qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="07564-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="07564-136">À partir de la **l’Explorateur de solutions** fenêtre, le bouton droit sur le **Client** de projet et sélectionnez **démarrer une nouvelle Instance**.</span><span class="sxs-lookup"><span data-stu-id="07564-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="07564-137">La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.</span><span class="sxs-lookup"><span data-stu-id="07564-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="07564-138">Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="07564-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="07564-139">Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.</span><span class="sxs-lookup"><span data-stu-id="07564-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="07564-140">Appuyez sur une touche quelconque pour arrêter l'application console Client.</span><span class="sxs-lookup"><span data-stu-id="07564-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="07564-141">Appuyez sur MAJ+F5 pour arrêter le débogage du service.</span><span class="sxs-lookup"><span data-stu-id="07564-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="07564-142">Dans la zone de Notification Windows, cliquez avec le bouton droit sur l’icône serveur de développement ASP.NET et sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="07564-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
