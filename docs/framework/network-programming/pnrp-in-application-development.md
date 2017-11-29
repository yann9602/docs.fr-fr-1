---
title: "PNRP dans le développement d’applications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 752b354df897fa37bc45c1bbd1969cf93aac87ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="34ec4-102">PNRP dans le développement d’applications</span><span class="sxs-lookup"><span data-stu-id="34ec4-102">PNRP in Application Development</span></span>
<span data-ttu-id="34ec4-103">Dans Windows Vista, les applications réseau peuvent accéder aux fonctions de résolution et de publication des noms via une API PNRP simplifiée.</span><span class="sxs-lookup"><span data-stu-id="34ec4-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="34ec4-104">Implémentation du protocole PNRP</span><span class="sxs-lookup"><span data-stu-id="34ec4-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="34ec4-105">Avec l’API PNRP simplifiée, les clouds ne sont pas explicitement spécifiés pour inscrire des noms et des adresses. Le composant PNRP détermine automatiquement les clouds qu’il est possible de rejoindre, ainsi que les adresses à publier dans les clouds.</span><span class="sxs-lookup"><span data-stu-id="34ec4-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="34ec4-106">Pour une résolution beaucoup plus simple des noms PNRP dans Windows Vista, ceux-ci sont désormais intégrés dans la fonction getaddrinfo() de Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="34ec4-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="34ec4-107">Pour utiliser PNRP afin de résoudre un nom en une adresse IPv6, les applications peuvent utiliser la fonction getaddrinfo() pour résoudre le nom de domaine complet (FQDN) « nom.prnp.net », où « nom » correspond au nom de pair en cours de résolution.</span><span class="sxs-lookup"><span data-stu-id="34ec4-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="34ec4-108">Le domaine pnrp.net est un domaine réservé dans Windows Vista pour la résolution de noms PNRP.</span><span class="sxs-lookup"><span data-stu-id="34ec4-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="34ec4-109">La transmission de messages entre applications PeerToPeer est toujours gérée par des architectures sous-jacentes telles que PeerChannel et WCF. [Données volumineuses et streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="34ec4-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ec4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34ec4-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
