---
title: "Contrôle des versions de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9a332e9b0aeec74a8cfd87622ce3be7bbffe3c9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-versioning"></a><span data-ttu-id="c4109-102">Contrôle des versions de découverte</span><span class="sxs-lookup"><span data-stu-id="c4109-102">Discovery Versioning</span></span>
<span data-ttu-id="c4109-103">Cette rubrique donne une rapide vue d’ensemble de l’implémentation de nouvelles fonctionnalités de découverte.</span><span class="sxs-lookup"><span data-stu-id="c4109-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="c4109-104">Elle donne également une vue d'ensemble de la manière de sélectionner la version de découverte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c4109-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="c4109-105">Contrôle des versions de découverte</span><span class="sxs-lookup"><span data-stu-id="c4109-105">Discovery Versioning</span></span>  
 <span data-ttu-id="c4109-106">La fonctionnalité de découverte inclut la prise en charge de trois versions du protocole WS_Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="c4109-107">Les API de découverte vous permettent de sélectionner la version du protocole que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="c4109-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="c4109-108">Ce document décrit brièvement les paramètres liés au contrôle des versions.</span><span class="sxs-lookup"><span data-stu-id="c4109-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="c4109-109">Les classes de découverte suivantes ont désormais une propriété <xref:System.ServiceModel.Discovery.DiscoveryVersion> et prennent un argument <xref:System.ServiceModel.Discovery.DiscoveryVersion> dans leurs constructeurs :</span><span class="sxs-lookup"><span data-stu-id="c4109-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="c4109-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="c4109-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="c4109-111">Fournissant <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> en tant que constructeur paramètre utilise l’implémentation de la version d’avril 2005 du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="c4109-112">Cette version correspond à la version publiée de la spécification du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="c4109-113">Cette version doit être utilisée pour interopérer avec une application héritée utilisant la version de WS-Discovery d'avril 2005.</span><span class="sxs-lookup"><span data-stu-id="c4109-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="c4109-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="c4109-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="c4109-115">La version de découverte par défaut utilisée par les API est <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="c4109-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="c4109-116">C'est la version standardisée actuelle du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="c4109-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="c4109-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="c4109-118">Si vous spécifiez <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> comme paramètre de constructeur, l'implémentation utilise la version Committee Draft 1 du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="c4109-119">Cette version du protocole doit être utilisée pour interopérer avec les implémentations exécutant la version CD1 du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c4109-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="c4109-120">Prise en charge de plusieurs points de terminaison de découverte UDP pour différentes versions de découverte sur un hôte de service unique</span><span class="sxs-lookup"><span data-stu-id="c4109-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="c4109-121">Vous pouvez exposer plusieurs points de terminaison de découverte UDP pour différentes versions de découverte sur un hôte de service unique.</span><span class="sxs-lookup"><span data-stu-id="c4109-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="c4109-122">Pour ce faire, vous devez spécifier une adresse unique pour chaque point de terminaison de découverte UDP.</span><span class="sxs-lookup"><span data-stu-id="c4109-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="c4109-123">L'exemple suivant montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="c4109-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
