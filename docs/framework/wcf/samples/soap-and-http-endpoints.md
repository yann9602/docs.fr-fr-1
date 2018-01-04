---
title: Points de terminaison SOAP et HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef5059a886012c00d3d33327baeaae49a9d5b54c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="3301a-102">Points de terminaison SOAP et HTTP</span><span class="sxs-lookup"><span data-stu-id="3301a-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="3301a-103">Cet exemple montre comment implémenter un service RPC et l’exposer aux formats SOAP et mettre en forme le « Plain Old XML » (POX) à l’aide de la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modèle de programmation Web.</span><span class="sxs-lookup"><span data-stu-id="3301a-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="3301a-104">Consultez le [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) sample pour plus d’informations sur la liaison HTTP pour le service.</span><span class="sxs-lookup"><span data-stu-id="3301a-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="3301a-105">Cet exemple se concentre sur les détails ayant trait à l’exposition du même service sur SOAP et HTTP au moyen de différentes liaisons.</span><span class="sxs-lookup"><span data-stu-id="3301a-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3301a-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="3301a-106">Demonstrates</span></span>  
 <span data-ttu-id="3301a-107">Exposition d'un service RPC sur SOAP et HTTP à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3301a-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3301a-108">Discussion</span><span class="sxs-lookup"><span data-stu-id="3301a-108">Discussion</span></span>  
 <span data-ttu-id="3301a-109">Cet exemple est constitué de deux composants : un projet d'application Web (Service) qui contient un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et une application console (Client) qui appelle des opérations de service à l'aide de  liaisons SOAP et HTTP.</span><span class="sxs-lookup"><span data-stu-id="3301a-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="3301a-110">Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose 2 opérations, `GetData` et `PutData`, qui renvoient la chaîne passée en entrée.</span><span class="sxs-lookup"><span data-stu-id="3301a-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="3301a-111">Les opérations de service sont annotées avec <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3301a-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="3301a-112">Ces attributs contrôlent la projection HTTP de ces opérations.</span><span class="sxs-lookup"><span data-stu-id="3301a-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="3301a-113">Elles sont aussi annotées avec <xref:System.ServiceModel.OperationContractAttribute>, ce qui permet leur exposition sur des liaisons SOAP.</span><span class="sxs-lookup"><span data-stu-id="3301a-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="3301a-114">La méthode `PutData` du service lève un <xref:System.ServiceModel.Web.WebFaultException>, qui est renvoyé sur HTTP avec le code d'état HTTP et sur SOAP en tant qu'erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="3301a-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="3301a-115">Le fichier Web.config configure le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec 3 points de terminaison :</span><span class="sxs-lookup"><span data-stu-id="3301a-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="3301a-116">le point de terminaison ~/service.svc/mex qui expose les métadonnées du service pour l'accès des clients SOAP ;</span><span class="sxs-lookup"><span data-stu-id="3301a-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="3301a-117">le point de terminaison ~/service.svc/http qui permet aux clients d'accéder au service en utilisant la liaison HTTP ;</span><span class="sxs-lookup"><span data-stu-id="3301a-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="3301a-118">le point de terminaison ~/service.svc/soap qui permet aux clients d'accéder au service en utilisant la liaison SOAP sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="3301a-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="3301a-119">Le point de terminaison HTTP est configuré avec un point de terminaison <`webHttp`> standard où `helpEnabled` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="3301a-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="3301a-120">Par conséquent, le service expose sous ~/service.svc/http/help une page d'aide XHTML que les clients HTTP peuvent utiliser pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="3301a-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="3301a-121">Le projet client illustre l’accès au service à l’aide d’un proxy SOAP (généré via **ajouter une référence de Service**) et à l’aide <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="3301a-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="3301a-122">L'exemple se compose d'un service hébergé sur le Web et d'une application console.</span><span class="sxs-lookup"><span data-stu-id="3301a-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="3301a-123">Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="3301a-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="3301a-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3301a-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="3301a-125">Ouvrez la solution de l'exemple des points de terminaison SOAP et HTTP.</span><span class="sxs-lookup"><span data-stu-id="3301a-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="3301a-126">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="3301a-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="3301a-127">Si elle n’est pas déjà ouverte, appuyez sur CTRL + W + S pour ouvrir le **l’Explorateur de solutions** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3301a-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="3301a-128">À partir de la **l’Explorateur de solutions** fenêtre, avec le bouton droit le **Service** de projet et placez le curseur sur le **déboguer** option de menu contextuel afin que le **démarrer un nouveau Instance** menu contextuel s’affiche.</span><span class="sxs-lookup"><span data-stu-id="3301a-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="3301a-129">Cliquez sur **démarrer une nouvelle Instance**.</span><span class="sxs-lookup"><span data-stu-id="3301a-129">Click **Start New Instance**.</span></span> <span data-ttu-id="3301a-130">Cette opération lance le serveur de développement ASP.NET, qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="3301a-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="3301a-131">Dans les fenêtres de l’Explorateur de solutions, cliquez sur le projet Client et placez le curseur sur le **déboguer** option de menu contextuel pour que le **démarrer une nouvelle Instance** menu contextuel s’affiche.</span><span class="sxs-lookup"><span data-stu-id="3301a-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="3301a-132">Cliquez sur **démarrer une nouvelle Instance**.</span><span class="sxs-lookup"><span data-stu-id="3301a-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="3301a-133">La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.</span><span class="sxs-lookup"><span data-stu-id="3301a-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="3301a-134">Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="3301a-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="3301a-135">Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.</span><span class="sxs-lookup"><span data-stu-id="3301a-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="3301a-136">Appuyez sur une touche quelconque pour arrêter l'application console Client.</span><span class="sxs-lookup"><span data-stu-id="3301a-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="3301a-137">Appuyez sur MAJ+F5 pour arrêter le débogage du service.</span><span class="sxs-lookup"><span data-stu-id="3301a-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="3301a-138">Dans la zone de Notification Windows, cliquez sur l’icône serveur de développement ASP.NET et sélectionnez **arrêter** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="3301a-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3301a-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3301a-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3301a-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3301a-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3301a-141">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3301a-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3301a-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3301a-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
