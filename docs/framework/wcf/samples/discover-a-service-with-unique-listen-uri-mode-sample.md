---
title: "Découvrir un service avec Unique Listen Uri Mode Sample"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48b49def3f8f009eeb4ffa0204e9c616b5acfec7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="ec12c-102">Découvrir un service avec Unique Listen Uri Mode Sample</span><span class="sxs-lookup"><span data-stu-id="ec12c-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="ec12c-103">Cet exemple montre comment découvrir un service dont la propriété <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> a la valeur <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="ec12c-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="ec12c-104">Lorsque la propriété <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> a la valeur <xref:System.ServiceModel.Description.ListenUriMode.Unique>, le caractère unique de ListenUri peut être garanti soit en définissant le port de sorte qu'il soit unique, soit en ajoutant un GUID pour que le chemin d'accès soit unique.</span><span class="sxs-lookup"><span data-stu-id="ec12c-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="ec12c-105">Caractéristiques sur le service</span><span class="sxs-lookup"><span data-stu-id="ec12c-105">Features on the Service</span></span>  
 <span data-ttu-id="ec12c-106">La propriété <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> a la valeur <xref:System.ServiceModel.Description.ListenUriMode.Unique> pour le point de terminaison TCP.</span><span class="sxs-lookup"><span data-stu-id="ec12c-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="ec12c-107">Le service est alors rendu détectable sur un point de terminaison <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="ec12c-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="ec12c-108">Caractéristiques sur le client</span><span class="sxs-lookup"><span data-stu-id="ec12c-108">Features on the Client</span></span>  
 <span data-ttu-id="ec12c-109">Ce client se connecte au service à l'aide du `Via.Uri` en utilisant la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec12c-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="ec12c-110">Le <xref:System.ServiceModel.Discovery.FindResponse> retourné par la méthode est alors interrogé pour déterminer s'il contient un <xref:System.ServiceModel.Endpoint.ListenUri%2A> valide et s'il est différent d'`Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="ec12c-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="ec12c-111">Les informations appropriées sont ensuite passées à la méthode `InvokeCalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ec12c-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="ec12c-112">Dans la méthode `InvokeCalculatorService`, l'appelant passe <xref:System.ServiceModel.Endpoint.ListenUri%2A>, suite à quoi un `ClientViaBehavior` avec le `Via.Uri` correct est ajouté au point de terminaison du client.</span><span class="sxs-lookup"><span data-stu-id="ec12c-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="ec12c-113">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="ec12c-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="ec12c-114">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez UniqueListenUriMode.sln.</span><span class="sxs-lookup"><span data-stu-id="ec12c-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="ec12c-115">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="ec12c-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ec12c-116">Exécutez l'application du service, générée dans le dossier [répertoire de base de la solution]\service\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="ec12c-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="ec12c-117">Exécutez l'application du client, générée dans le dossier [répertoire de base de la solution]\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="ec12c-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="ec12c-118">Le client trouve le service en cours d'exécution et écrit dans la console les métadonnées publiées par le point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="ec12c-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ec12c-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ec12c-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ec12c-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ec12c-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ec12c-121">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ec12c-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ec12c-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ec12c-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="ec12c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec12c-123">See Also</span></span>
