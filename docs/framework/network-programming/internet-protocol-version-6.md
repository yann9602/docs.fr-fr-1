---
title: Protocole Internet version 6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 333fbb452cb1f24b5e62d1106eff4560b26267b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="a55d1-102">Protocole Internet version 6</span><span class="sxs-lookup"><span data-stu-id="a55d1-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="a55d1-103">Le protocole IPv6 (protocole Internet version 6) est une nouvelle suite de protocoles standard conçus pour la couche réseau d’Internet.</span><span class="sxs-lookup"><span data-stu-id="a55d1-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="a55d1-104">IPv6 est destiné à résoudre bon nombre des problèmes de l’actuelle version de la suite de protocoles (appelée IPv4), notamment ceux liés à l’épuisement des adresses, la sécurité, la configuration automatique, l’extensibilité, etc.</span><span class="sxs-lookup"><span data-stu-id="a55d1-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="a55d1-105">IPv6 étend les capacités d’Internet à de nouveaux types d’applications, comme les applications pair à pair (P2P) et les applications mobiles.</span><span class="sxs-lookup"><span data-stu-id="a55d1-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="a55d1-106">Voici les principaux problèmes du protocole IPv4 actuel :</span><span class="sxs-lookup"><span data-stu-id="a55d1-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="a55d1-107">Épuisement rapide de l’espace d’adressage.</span><span class="sxs-lookup"><span data-stu-id="a55d1-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="a55d1-108">Cela a conduit à l’utilisation de NAT (Network Address Translator) pour mapper plusieurs adresses privées à une seule adresse IP publique.</span><span class="sxs-lookup"><span data-stu-id="a55d1-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="a55d1-109">Les principaux problèmes de ce mécanisme sont la surcharge de traitement et l’absence de connectivité de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="a55d1-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="a55d1-110">Prise en charge hiérarchique insuffisante.</span><span class="sxs-lookup"><span data-stu-id="a55d1-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="a55d1-111">En raison de son organisation inhérente en classes prédéfinies, IPv4 n’offre pas de véritable prise en charge hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="a55d1-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="a55d1-112">Il est impossible d’organiser les adresses IP en les mappant parfaitement à la topologie du réseau.</span><span class="sxs-lookup"><span data-stu-id="a55d1-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="a55d1-113">Ce défaut de conception majeur impose l’utilisation de tables de routage de grande taille pour la remise des paquets IPv4 sur Internet.</span><span class="sxs-lookup"><span data-stu-id="a55d1-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="a55d1-114">Configuration complexe du réseau.</span><span class="sxs-lookup"><span data-stu-id="a55d1-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="a55d1-115">Avec IPv4, les adresses doivent être assignées de façon statique ou à l’aide d’un protocole de configuration tel que DHCP.</span><span class="sxs-lookup"><span data-stu-id="a55d1-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="a55d1-116">Dans l’idéal, les ordinateurs hôtes ne devraient pas avoir à s’appuyer sur l’administration d’une infrastructure DHCP.</span><span class="sxs-lookup"><span data-stu-id="a55d1-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="a55d1-117">Ils devraient pouvoir effectuer la configuration eux-mêmes en fonction du segment réseau où ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="a55d1-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="a55d1-118">Absence de mécanismes d’authentification et de confidentialité intégrés.</span><span class="sxs-lookup"><span data-stu-id="a55d1-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="a55d1-119">IPv4 ne nécessite pas la prise en charge d’un mécanisme qui fournit l’authentification ou le chiffrement des données échangées.</span><span class="sxs-lookup"><span data-stu-id="a55d1-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="a55d1-120">Cela n’est plus le cas avec IPv6.</span><span class="sxs-lookup"><span data-stu-id="a55d1-120">This changes with IPv6.</span></span> <span data-ttu-id="a55d1-121">La sécurité du protocole Internet (IPsec) est une exigence de prise en charge d’IPv6.</span><span class="sxs-lookup"><span data-stu-id="a55d1-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="a55d1-122">Une nouvelle suite de protocoles doit répondre aux exigences de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="a55d1-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="a55d1-123">Routage et adressage à grande échelle, avec une faible surcharge.</span><span class="sxs-lookup"><span data-stu-id="a55d1-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="a55d1-124">Configuration automatique pour diverses situations de connexion.</span><span class="sxs-lookup"><span data-stu-id="a55d1-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="a55d1-125">Authentification et confidentialité intégrées.</span><span class="sxs-lookup"><span data-stu-id="a55d1-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="a55d1-126">Pour plus d’informations, consultez [Adressage IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [Routage IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [Configuration automatique IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Activation et désactivation d’IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md) et [Guide pratique pour modifier le fichier de configuration de l’ordinateur en vue de la prise en charge d’IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="a55d1-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="a55d1-127">Références</span><span class="sxs-lookup"><span data-stu-id="a55d1-127">References</span></span>  
 <span data-ttu-id="a55d1-128">Voici une sélection de normes RFC que vous pouvez consulter sur le site Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)) :</span><span class="sxs-lookup"><span data-stu-id="a55d1-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="a55d1-129">RFC 1287 : Towards the Future Internet Architecture.</span><span class="sxs-lookup"><span data-stu-id="a55d1-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="a55d1-130">RFC 1454 : Comparison of Proposals for Next Version of IP.</span><span class="sxs-lookup"><span data-stu-id="a55d1-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="a55d1-131">RFC 2373 : IP Version 6 Addressing Architecture.</span><span class="sxs-lookup"><span data-stu-id="a55d1-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="a55d1-132">RFC 2374 : An IPv6 Aggregatable Global Unicast Address Format.</span><span class="sxs-lookup"><span data-stu-id="a55d1-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="a55d1-133">Vous pouvez également trouver des informations concernant IPv6 dans la [section IPv6 sur Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span><span class="sxs-lookup"><span data-stu-id="a55d1-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55d1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a55d1-134">See Also</span></span>  
 [<span data-ttu-id="a55d1-135">Exemple de sockets IPv6</span><span class="sxs-lookup"><span data-stu-id="a55d1-135">IPv6 Sockets Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [<span data-ttu-id="a55d1-136">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="a55d1-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="a55d1-137">Sockets</span><span class="sxs-lookup"><span data-stu-id="a55d1-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
