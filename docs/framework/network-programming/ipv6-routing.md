---
title: Routage IPv6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7bfb79c5ab5406793a27f653b7e6a1abf2b2859
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-routing"></a><span data-ttu-id="a7fb0-102">Routage IPv6</span><span class="sxs-lookup"><span data-stu-id="a7fb0-102">IPv6 Routing</span></span>
<span data-ttu-id="a7fb0-103">Le protocole IPv6 comprend un mécanisme de routage souple.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="a7fb0-104">En raison de la façon dont les ID réseau IPv4 sont alloués, les tables de routage volumineuses doivent être gérées par les routeurs Internet principaux.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="a7fb0-105">Ces routeurs doivent connaître tous les itinéraires afin de transmettre les paquets qui sont susceptibles d’être dirigés vers des nœuds Internet.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="a7fb0-106">Grâce à sa capacité de regrouper des adresses, IPv6 permet un adressage souple et réduit considérablement la taille des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="a7fb0-107">Dans cette nouvelle architecture d’adressage, les routeurs intermédiaires doivent uniquement effectuer le suivi de la partie locale de leur réseau afin de transmettre les messages de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="a7fb0-108">Découverte de voisin</span><span class="sxs-lookup"><span data-stu-id="a7fb0-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="a7fb0-109">Voici certaines des fonctionnalités fournies par la découverte de voisin :</span><span class="sxs-lookup"><span data-stu-id="a7fb0-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="a7fb0-110">La découverte de routeurs.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-110">Router discovery.</span></span> <span data-ttu-id="a7fb0-111">Elle permet aux hôtes d’identifier les routeurs locaux.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="a7fb0-112">La résolution d’adresse.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-112">Address resolution.</span></span> <span data-ttu-id="a7fb0-113">Elle permet aux nœuds de résoudre une adresse link-layer pour l’adresse correspondante du tronçon suivant (en remplacement du protocole ARP).</span><span class="sxs-lookup"><span data-stu-id="a7fb0-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="a7fb0-114">La configuration automatique des adresses.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-114">Address auto-configuration.</span></span> <span data-ttu-id="a7fb0-115">Elle permet aux hôtes de configurer automatiquement les adresses locales et globales.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="a7fb0-116">La découverte de voisin utilise le protocole IPv6 (ICMPv6) pour les types de messages suivants :</span><span class="sxs-lookup"><span data-stu-id="a7fb0-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="a7fb0-117">Annonces de routeur.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-117">Router advertisement.</span></span> <span data-ttu-id="a7fb0-118">Envoyées par un routeur à intervalles réguliers ou en réponse à une sollicitation de routeur.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="a7fb0-119">Les routeurs IPv6 utilisent des annonces de routeur pour annoncer leur disponibilité, leurs préfixes d’adresse et autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="a7fb0-120">Sollicitations de routeur.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-120">Router solicitation.</span></span> <span data-ttu-id="a7fb0-121">Envoyées par un hôte pour demander que les routeurs présents sur la liaison envoient immédiatement une annonce de routeur.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="a7fb0-122">Sollicitations de voisin.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-122">Neighbor solicitation.</span></span> <span data-ttu-id="a7fb0-123">Envoyées par les nœuds pour la résolution d’adresse, la détection d’adresses en double et la vérification de disponibilité d’un voisin.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="a7fb0-124">Annonces de voisin.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-124">Neighbor advertisement.</span></span> <span data-ttu-id="a7fb0-125">Envoyées par les nœuds pour répondre à une sollicitation de voisin ou pour avertir les voisins d’un changement d’adresse link-layer.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="a7fb0-126">Redirections.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-126">Redirect.</span></span> <span data-ttu-id="a7fb0-127">Envoyées par les routeurs pour indiquer une meilleure adresse de tronçon suivant à une destination particulière pour un nœud expéditeur.</span><span class="sxs-lookup"><span data-stu-id="a7fb0-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7fb0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7fb0-128">See Also</span></span>  
 [<span data-ttu-id="a7fb0-129">Protocole IPv6</span><span class="sxs-lookup"><span data-stu-id="a7fb0-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="a7fb0-130">Sockets</span><span class="sxs-lookup"><span data-stu-id="a7fb0-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
