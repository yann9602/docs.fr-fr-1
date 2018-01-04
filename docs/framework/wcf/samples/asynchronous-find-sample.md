---
title: Exemple Asynchronous Find
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b0b21e9d75c0145c9bd3fa5edf13913cf43f461
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="f691c-102">Exemple Asynchronous Find</span><span class="sxs-lookup"><span data-stu-id="f691c-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="f691c-103">Cet exemple montre comment utiliser l'opération de recherche asynchrone à partir d'une application cliente.</span><span class="sxs-lookup"><span data-stu-id="f691c-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f691c-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f691c-104">Sample Details</span></span>  
 <span data-ttu-id="f691c-105">L'avantage à suivre ce modèle de conception réside dans le fait que le client reçoit une notification asynchrone lorsque la demande de recherche a situé des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f691c-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="f691c-106">Pour en comprendre le fonctionnement, ouvrez le fichier Client.cs.</span><span class="sxs-lookup"><span data-stu-id="f691c-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="f691c-107">Notez que l'objet <xref:System.ServiceModel.Discovery.DiscoveryClient> a deux délégués attachés à ses gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="f691c-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="f691c-108">Un délégué est appelé lorsqu'un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> est déclenché et un autre est appelé chaque fois qu'un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="f691c-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="f691c-109">L’exemple montre comment vous pouvez utiliser ce modèle dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f691c-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f691c-110">Cet exemple utilise des points de terminaison HTTP et pour l'exécuter, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées.</span><span class="sxs-lookup"><span data-stu-id="f691c-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f691c-111">[Configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="f691c-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="f691c-112">L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="f691c-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="f691c-113">Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle.</span><span class="sxs-lookup"><span data-stu-id="f691c-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f691c-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f691c-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f691c-115">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier AsyncFind.sln.</span><span class="sxs-lookup"><span data-stu-id="f691c-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="f691c-116">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="f691c-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="f691c-117">Ouvrez une invite de commandes [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], accédez au répertoire \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug et exécutez Service.exe.</span><span class="sxs-lookup"><span data-stu-id="f691c-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="f691c-118">Une fois le service démarré, accédez au répertoire \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ou WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug et exécutez Client.exe.</span><span class="sxs-lookup"><span data-stu-id="f691c-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="f691c-119">Notez que le client est en mesure de trouver et d'appeler le service.</span><span class="sxs-lookup"><span data-stu-id="f691c-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f691c-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f691c-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f691c-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f691c-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f691c-122">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f691c-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f691c-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f691c-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="f691c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f691c-124">See Also</span></span>
