---
title: "Réseaux homologues"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e66a2f87d69ddba1676ed5e210859edfb5d8e41
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="dcb1a-102">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="dcb1a-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="dcb1a-103">Le canal homologue est une technologie de communication P2P (peer-to-peer) entre plusieurs parties de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcb1a-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="dcb1a-104">Elle fournit un canal de communication P2P basé sur des messages sécurisé et évolutif pour les développeurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="dcb1a-105">Un exemple courant d'application entre plusieurs parties pouvant bénéficier du canal homologue concerne une application collaborative telle que la conversation, dans le cadre de laquelle un groupe de personnes discutent les unes avec les autres d'égal à égal sans qu'un serveur soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="dcb1a-106">Le canal homologue permet la collaboration P2P, la distribution de contenu, l'équilibrage de charge et le traitement distribué des scénarios consommateur et d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="dcb1a-107">Le canal homologue est activé par défaut sur [!INCLUDE[wv](../../../../includes/wv-md.md)], comme l'ensemble d'[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcb1a-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="dcb1a-108">Pour accéder aux classes du canal homologue, ajoutez des références à System.ServiceModel.dll dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="dcb1a-109">Les sections suivantes contiennent des informations sur les réseaux homologues et l'utilisation des classes du canal homologue pour créer des applications réseau adaptées aux homologues.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcb1a-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dcb1a-110">In This Section</span></span>  
 <span data-ttu-id="dcb1a-111">[Scénarios de canal homologue](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): décrit les scénarios de développement pris en charge par les API de canal homologue, telles que la messagerie, collaboration, publication/abonnement distribué de traitement et de jeu.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="dcb1a-112">[Concepts relatifs au canal de l’homologue](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): décrit des mailles homologues, nœuds homologues, sécurité de canal homologue et les programmes de résolution d’homologue.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="dcb1a-113">[Création d’une Application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): fournit des conseils sur le développement d’applications de canal homologue.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="dcb1a-114">Exemples de code de canal homologue</span><span class="sxs-lookup"><span data-stu-id="dcb1a-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="dcb1a-115">Programme de résolution d’homologue personnalisé canal homologue</span><span class="sxs-lookup"><span data-stu-id="dcb1a-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="dcb1a-116">Peer Channel Team Blog</span><span class="sxs-lookup"><span data-stu-id="dcb1a-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="dcb1a-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="dcb1a-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>
