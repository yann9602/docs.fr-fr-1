---
title: "Implémentation d'un proxy de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2996eb07c883947210c48471a2c60ba49495566d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="c5a43-102">Implémentation d'un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="c5a43-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="c5a43-103">Cette section décrit les étapes nécessaires pour implémenter un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="c5a43-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="c5a43-104">Un proxy de découverte est un service autonome qui contient un référentiel de services.</span><span class="sxs-lookup"><span data-stu-id="c5a43-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="c5a43-105">Les clients peuvent interroger un proxy de découverte pour trouver les services détectables que le proxy connaît.</span><span class="sxs-lookup"><span data-stu-id="c5a43-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="c5a43-106">La manière dont un proxy est rempli avec des services incombe à l'implémenteur.</span><span class="sxs-lookup"><span data-stu-id="c5a43-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="c5a43-107">Par exemple, un proxy de découverte peut se connecter à un référentiel de services existants et rendre cette information détectable, un administrateur peut utiliser une API de gestion pour ajouter des services détectables à un proxy, ou un proxy de découverte peut utiliser les fonctionnalités d'annonce pour mettre à jour son cache interne.</span><span class="sxs-lookup"><span data-stu-id="c5a43-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="c5a43-108">L'implémentation WCF fournit des classes de base qui vous permettent de générer facilement un proxy.</span><span class="sxs-lookup"><span data-stu-id="c5a43-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="c5a43-109">Vous pouvez utiliser ces API pour générer un en-tête du proxy de découverte sur votre base de données de référentiel existante.</span><span class="sxs-lookup"><span data-stu-id="c5a43-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="c5a43-110">Le proxy de découverte implémenté dans cet exemple est identique à n'importe quel autre service WCF, en ce sens que vous pouvez également rendre le proxy de découverte détectable et faire localiser ses points de terminaison par les clients.</span><span class="sxs-lookup"><span data-stu-id="c5a43-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5a43-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c5a43-111">In This Section</span></span>  
 [<span data-ttu-id="c5a43-112">Guide pratique pour implémenter un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="c5a43-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="c5a43-113">Décrit comment implémenter un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="c5a43-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="c5a43-114">Guide pratique pour implémenter un service détectable qui s’inscrit auprès du proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="c5a43-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="c5a43-115">Décrit comment implémenter un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] détectable qui s'enregistre avec le proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="c5a43-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="c5a43-116">Guide pratique pour implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service</span><span class="sxs-lookup"><span data-stu-id="c5a43-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="c5a43-117">Décrit comment implémenter une application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilise le proxy de découverte pour rechercher un service.</span><span class="sxs-lookup"><span data-stu-id="c5a43-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="c5a43-118">Guide pratique pour tester le proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="c5a43-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="c5a43-119">Décrit comment tester le code écrit dans les trois rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="c5a43-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a43-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5a43-120">See Also</span></span>  
 [<span data-ttu-id="c5a43-121">Découverte WCF</span><span class="sxs-lookup"><span data-stu-id="c5a43-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="c5a43-122">Guide pratique pour ajouter la détectabilité par programmation à un service et un client WCF</span><span class="sxs-lookup"><span data-stu-id="c5a43-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
