---
title: Exemple SystemWebRouting Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="51d5b-102">Exemple SystemWebRouting Integration</span><span class="sxs-lookup"><span data-stu-id="51d5b-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="51d5b-103">Cet exemple illustre l'intégration de la couche d'hébergement avec les classes de l'espace de noms <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="51d5b-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="51d5b-104">Les classes de l'espace de noms <xref:System.Web.Routing> permettent à une application d'utiliser des URL qui ne correspondent pas directement à une ressource physique.</span><span class="sxs-lookup"><span data-stu-id="51d5b-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="51d5b-105">L'utilisation du routage Web permet au développeur de créer des adresses virtuelles pour HTTP qui sont ensuite remappées aux véritables services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51d5b-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="51d5b-106">Cela peut être utile lorsqu'un service WCF doit être hébergé sans requérir de fichier ou ressource physique, ou lorsque des services doivent être accessibles via des URL qui ne contiennent pas de fichiers tels que .html ou .aspx.</span><span class="sxs-lookup"><span data-stu-id="51d5b-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="51d5b-107">Cet exemple montre comment utiliser la classe <xref:System.Web.Routing.RouteTable> pour créer des URI virtuels qui mappent aux services en cours d'exécution définis dans global.asax.</span><span class="sxs-lookup"><span data-stu-id="51d5b-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="51d5b-108">Pour cet exemple, deux flux RSS sont créés à l'aide de WCF : un flux `movies` et un flux `channels`.</span><span class="sxs-lookup"><span data-stu-id="51d5b-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="51d5b-109">Les URL pour activer les services ne contiennent pas d’extension et sont enregistrés dans le `Application_Start` méthode de la `Global` classe dérivée de la <xref:System.Web.HttpApplication.Application_Start> classe.</span><span class="sxs-lookup"><span data-stu-id="51d5b-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51d5b-110">Les classes de l'espace de noms <xref:System.Web.Routing> ne fonctionnent que pour des services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="51d5b-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51d5b-111">Cet exemple fonctionne uniquement dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)], puisque [!INCLUDE[iis60](../../../../includes/iis60-md.md)] utilise une autre méthode pour la prise en charge des URL sans extension.</span><span class="sxs-lookup"><span data-stu-id="51d5b-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51d5b-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="51d5b-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="51d5b-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="51d5b-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="51d5b-114">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="51d5b-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51d5b-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="51d5b-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="51d5b-116">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="51d5b-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="51d5b-117">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="51d5b-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="51d5b-118">Pour exécuter la solution et démarrer le serveur de développement Web, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="51d5b-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="51d5b-119">Une liste des répertoires de l'exemple s'affiche.</span><span class="sxs-lookup"><span data-stu-id="51d5b-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="51d5b-120">Notez l'absence de fichiers ayant l'extension .svc.</span><span class="sxs-lookup"><span data-stu-id="51d5b-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="51d5b-121">Dans la barre d'adresses, ajoutez `movies` à l'URL, pour obtenir http://localhost:[port]/movies et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="51d5b-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="51d5b-122">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="51d5b-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="51d5b-123">Dans la barre d'adresses, ajoutez `channels` à l'URL, pour obtenir http://localhost:[port]/channels et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="51d5b-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="51d5b-124">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="51d5b-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="51d5b-125">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="51d5b-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="51d5b-126">Si le serveur de développement n’est pas terminé, cliquez sur l’icône de zone de notification et sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="51d5b-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="51d5b-127">Pour utiliser cet exemple avec hébergement dans IIS</span><span class="sxs-lookup"><span data-stu-id="51d5b-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="51d5b-128">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="51d5b-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="51d5b-129">Générez le projet en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="51d5b-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="51d5b-130">Créez une application Web dans le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="51d5b-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="51d5b-131">Dans le Gestionnaire des services Internet, bouton droit sur le **Site Web par défaut** et sélectionnez **ajouter une Application**.</span><span class="sxs-lookup"><span data-stu-id="51d5b-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="51d5b-132">Pour le **alias**, tapez `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="51d5b-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="51d5b-133">Pour le **chemin d’accès physique**, sélectionnez le dossier Service situé dans le projet.</span><span class="sxs-lookup"><span data-stu-id="51d5b-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="51d5b-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="51d5b-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="51d5b-135">Démarrer l’application, en double-cliquant sur l’application Web et en sélectionnant **gérer l’Application** , puis **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="51d5b-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="51d5b-136">Dans la barre d'adresses, ajoutez `movies` à l'URL, pour obtenir http://localhost:[port]/movies et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="51d5b-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="51d5b-137">Le flux movies s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="51d5b-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="51d5b-138">Dans la barre d'adresses, ajoutez `channels` à l'URL, pour obtenir http://localhost:[port]/channels et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="51d5b-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="51d5b-139">Le flux channels s'affiche dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="51d5b-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="51d5b-140">Fermez le navigateur Web en appuyant sur ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="51d5b-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="51d5b-141">Cet exemple montre que la couche d'hébergement est capable de composer avec les classes de l'espace de noms <xref:System.Web.Routing> pour router les requêtes de services hébergés sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="51d5b-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51d5b-142">Mettez à jour le pool d'applications par défaut de sorte qu'il utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] s'il utilise la version 2.</span><span class="sxs-lookup"><span data-stu-id="51d5b-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d5b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51d5b-143">See Also</span></span>  
 [<span data-ttu-id="51d5b-144">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="51d5b-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
