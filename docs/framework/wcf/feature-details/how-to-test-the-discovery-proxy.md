---
title: "Procédure : tester le proxy de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6494a96f5e7e3a420c8443eff767b0e86d3bc25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="3df45-102">Procédure : tester le proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="3df45-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="3df45-103">Cette rubrique est la quatrième d'une série quatre qui expliquent comment implémenter un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="3df45-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="3df45-104">Dans la rubrique précédente, [Comment : implémenter une Application cliente qui utilise le Proxy de découverte pour rechercher un Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), vous implémenté un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application cliente qui utilise le proxy de découverte pour rechercher un service, puis appelle la service.</span><span class="sxs-lookup"><span data-stu-id="3df45-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="3df45-105">Cette rubrique explique comment vérifier si le proxy de découverte, le service et l'application cliente fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="3df45-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="3df45-106">Exécuter le proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="3df45-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="3df45-107">Ouvrez une invite de commandes en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3df45-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="3df45-108">Une boîte de dialogue s’affiche éventuellement, indiquant : le Pare-feu Windows a bloqué certaines fonctionnalités de ce programme.</span><span class="sxs-lookup"><span data-stu-id="3df45-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="3df45-109">Si vous voyez ce message, cliquez sur le **Unblock** bouton.</span><span class="sxs-lookup"><span data-stu-id="3df45-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="3df45-110">Dans l'invite de commandes, exécutez le proxy de découverte, DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="3df45-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="3df45-111">L'application doit afficher le texte suivant : `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="3df45-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="3df45-112">Exécuter le service détectable</span><span class="sxs-lookup"><span data-stu-id="3df45-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="3df45-113">Ouvrez une invite de commandes en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3df45-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="3df45-114">Dans l'invite de commandes, exécutez le service détectable service.exe.</span><span class="sxs-lookup"><span data-stu-id="3df45-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="3df45-115">Le DiscoveryProxy.exe doit afficher le texte suivant : `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="3df45-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="3df45-116">Exécuter l'application cliente</span><span class="sxs-lookup"><span data-stu-id="3df45-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="3df45-117">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3df45-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="3df45-118">Dans l'invite de commandes, exécutez l'application client.exe.</span><span class="sxs-lookup"><span data-stu-id="3df45-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="3df45-119">Au bout de quelques secondes l'application cliente affiche le texte suivant : connexion au [point de terminaison de service].</span><span class="sxs-lookup"><span data-stu-id="3df45-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="3df45-120">Le service.exe doit ensuite afficher le texte suivant : message de salutation reçu, je vais répondre.</span><span class="sxs-lookup"><span data-stu-id="3df45-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="3df45-121">Le client.exe doit ensuite afficher le texte suivant : Bonjour client !</span><span class="sxs-lookup"><span data-stu-id="3df45-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="3df45-122">Arrêter les applications</span><span class="sxs-lookup"><span data-stu-id="3df45-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="3df45-123">Arrêtez l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="3df45-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="3df45-124">Arrêtez le service.</span><span class="sxs-lookup"><span data-stu-id="3df45-124">Shut down the service.</span></span> <span data-ttu-id="3df45-125">Le proxy de découverte affiche le texte suivant : `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="3df45-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="3df45-126">Arrêtez le proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="3df45-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df45-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3df45-127">See Also</span></span>  
 [<span data-ttu-id="3df45-128">Vue d’ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="3df45-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="3df45-129">Guide pratique pour implémenter un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="3df45-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="3df45-130">Guide pratique pour implémenter un service détectable qui s’inscrit auprès du proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="3df45-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="3df45-131">Guide pratique pour implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service</span><span class="sxs-lookup"><span data-stu-id="3df45-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
