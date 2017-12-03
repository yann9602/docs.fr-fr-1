---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b4a68204d8ae5d2a338d60498522810a557e575
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="5dd2b-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="5dd2b-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="5dd2b-103">Cet exemple montre comment insérer des métadonnées XML personnalisées dans les métadonnées de découverte pour un point de terminaison détectable exposé par un service.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="5dd2b-104">Il montre ensuite comment un client peut rechercher le service et extraire ces données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="5dd2b-105">Cet exemple se compose de deux projets : service et client.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5dd2b-106">Service</span><span class="sxs-lookup"><span data-stu-id="5dd2b-106">Service</span></span>  
 <span data-ttu-id="5dd2b-107">Dans la méthode `main`, l'exemple montre qu'un objet de type <xref:System.Xml.Linq.XElement> est rempli avec les champs voulus et ajouté au <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="5dd2b-108">Ce <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est ajouté à un point de terminaison particulier.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="5dd2b-109">Lorsque ce point de terminaison particulier est découvert, les métadonnées de découverte contiennent les données personnalisées ajoutées ici.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="5dd2b-110">Client</span><span class="sxs-lookup"><span data-stu-id="5dd2b-110">Client</span></span>  
 <span data-ttu-id="5dd2b-111">L'exemple illustre la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> qui est appelée sur un <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="5dd2b-112">Le <xref:System.ServiceModel.Discovery.FindResponse> obtenu est alors interrogé pour déterminer s'il contient les éléments XML appropriés et attendus.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="5dd2b-113">Ces éléments sont ensuite affichés dans la console.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5dd2b-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="5dd2b-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="5dd2b-115">Chargez la solution du projet dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] et générez le projet.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="5dd2b-116">Exécutez d'abord l'application Service, générée dans [répertoire de base de la solution]\service\bin\debug, puis l'application Client, générée dans [répertoire de base de la solution]\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="5dd2b-117">Notez que le service est mis en ligne, et que le client trouve le service et imprime les métadonnées publiées dans le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5dd2b-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5dd2b-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5dd2b-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5dd2b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5dd2b-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5dd2b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="5dd2b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dd2b-122">See Also</span></span>
