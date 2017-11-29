---
title: "À propos de l’espace de noms System.Net.PeerToPeer.Collaboration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696b1d3dd7312b52c28f11f64f007c29fb8a94b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a><span data-ttu-id="91d56-102">À propos de l’espace de noms System.Net.PeerToPeer.Collaboration</span><span class="sxs-lookup"><span data-stu-id="91d56-102">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>
<span data-ttu-id="91d56-103">L’espace de noms <xref:System.Net.PeerToPeer.Collaboration> fournit des classes et des API qui sont utilisées pour implémenter les activités de collaboration pair à l’aide de l’infrastructure de collaboration pair à pair.</span><span class="sxs-lookup"><span data-stu-id="91d56-103">The <xref:System.Net.PeerToPeer.Collaboration> namespace provides classes and APIs that are used to implement peer collaboration activities using the Peer-to-Peer Collaboration Infrastructure.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="91d56-104">Classes</span><span class="sxs-lookup"><span data-stu-id="91d56-104">Classes</span></span>  
 <span data-ttu-id="91d56-105">Les principales classes utilisées dans l’implémentation d’une activité de collaboration pair à pair sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="91d56-105">The main classes used in the implementation of a Peer-to-Peer Collaboration activity are:</span></span>  
  
-   <span data-ttu-id="91d56-106">La classe <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, qui peut être utilisée pour stocker les contacts du pair.</span><span class="sxs-lookup"><span data-stu-id="91d56-106">The <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, which can be used to store peer contacts.</span></span>  
  
-   <span data-ttu-id="91d56-107">La classe <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> dans laquelle collaborer, telle qu’un jeu, un client chat ou une solution de conférence.</span><span class="sxs-lookup"><span data-stu-id="91d56-107">The <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> in which to collaborate, such as a game, chat client, or conferencing solution.</span></span>  
  
-   <span data-ttu-id="91d56-108">Les pairs qui vont collaborer à une activité.</span><span class="sxs-lookup"><span data-stu-id="91d56-108">The peers that will be collaborating in an activity.</span></span>  <span data-ttu-id="91d56-109">Ces pairs peuvent être représentés comme des objets <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> ou <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="91d56-109">These peers can be represented as <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, or <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objects.</span></span>  
  
-   <span data-ttu-id="91d56-110">La classe statique <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>, qui spécifie les applications qui sont disponibles et les pairs qui y participent.</span><span class="sxs-lookup"><span data-stu-id="91d56-110">The static <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> class itself, which specifies which applications are available and which peers are participating in them.</span></span>  
  
 <span data-ttu-id="91d56-111">Les méthodes <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> sont utilisées pour inviter les pairs à une session de collaboration.</span><span class="sxs-lookup"><span data-stu-id="91d56-111">The <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> methods are used to invite peers to a collaboration session.</span></span>  <span data-ttu-id="91d56-112">Un pair appelant peut s’abonner aux événements d’un autre pair signalant la mise à jour des données d’application, d’objet ou de présence associées à la session de collaboration.</span><span class="sxs-lookup"><span data-stu-id="91d56-112">A calling peer can subscribe to another peer for events that signal updates to application, object, or presence information affiliated with the collaboration session.</span></span> <span data-ttu-id="91d56-113">Les classes de présence spécifient si un <xref:System.Net.PeerToPeer.Collaboration.Peer> est disponible pour la collaboration, et la classe <xref:System.Net.PeerToPeer.Collaboration.PeerScope> est utilisée pour spécifier le degré de participation autorisé pour un pair : <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> (sous-réseau) ou <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span><span class="sxs-lookup"><span data-stu-id="91d56-113">Presence classes specify whether a <xref:System.Net.PeerToPeer.Collaboration.Peer> is available for collaboration, and the <xref:System.Net.PeerToPeer.Collaboration.PeerScope> class is used to specify how much participation is allowed for a peer:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (subnet) or <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span></span>  
  
 <span data-ttu-id="91d56-114">Une session de collaboration se compose de quatre étapes :</span><span class="sxs-lookup"><span data-stu-id="91d56-114">A collaboration session is comprised of four steps:</span></span>  
  
-   <span data-ttu-id="91d56-115">La détection.</span><span class="sxs-lookup"><span data-stu-id="91d56-115">Discovery.</span></span> <span data-ttu-id="91d56-116">Détectez ou publiez des informations relatives aux applications, aux pairs et à la présence.</span><span class="sxs-lookup"><span data-stu-id="91d56-116">Discover or publish applications, peers, and presence information.</span></span>  <span data-ttu-id="91d56-117">Par exemple, trouvez d’autres personnes sur le sous-réseau local qui ont installé les mêmes jeux que vous.</span><span class="sxs-lookup"><span data-stu-id="91d56-117">For instance, find other people on the local subnet that have the same games installed.</span></span>  
  
-   <span data-ttu-id="91d56-118">L’invitation.</span><span class="sxs-lookup"><span data-stu-id="91d56-118">Invitation.</span></span> <span data-ttu-id="91d56-119">Envoyez des invitations sécurisées aux pairs distants ou acceptez leurs invitations pour démarrer ou rejoindre des sessions <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>.</span><span class="sxs-lookup"><span data-stu-id="91d56-119">Send and accept secure invitations for remote peer(s) to start or join <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sessions.</span></span>  
  
-   <span data-ttu-id="91d56-120">La gestion des contacts.</span><span class="sxs-lookup"><span data-stu-id="91d56-120">Contact Management.</span></span> <span data-ttu-id="91d56-121">Ajoutez les pairs détectés en tant que contacts à un <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span><span class="sxs-lookup"><span data-stu-id="91d56-121">Add discovered peers as a contact to a <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span></span>  
  
-   <span data-ttu-id="91d56-122">La communication.</span><span class="sxs-lookup"><span data-stu-id="91d56-122">Communication.</span></span> <span data-ttu-id="91d56-123">Lorsque la communication est établie, utilisez les API <xref:System.Net>, l’API <xref:System.Net.PeerToPeer> ou les classes de canal pair WCF pour les communications entre plusieurs parties.</span><span class="sxs-lookup"><span data-stu-id="91d56-123">When communication is established, use the <xref:System.Net> APIs, the <xref:System.Net.PeerToPeer> API, or the Windows Communication Foundation Peer Channel classes for multiparty communications.</span></span>  
  
 <span data-ttu-id="91d56-124">Par exemple, le pair hôte démarre une session de collaboration et utilise la méthode <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> pour ajouter un pair distant et l’un de ses pairs locaux au gestionnaire de contacts du pair hôte.</span><span class="sxs-lookup"><span data-stu-id="91d56-124">For example, the host peer starts a collaboration session, and utilizes the <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> method to add a remote peer and one of its local peers to the Contact Manager of the host peer.</span></span>  <span data-ttu-id="91d56-125">Les trois utilisateurs participeront alors à leur propre session collaboration privée.</span><span class="sxs-lookup"><span data-stu-id="91d56-125">The three users will then participate in their own private collaboration session.</span></span>  
  
 <span data-ttu-id="91d56-126">Voici quelques exemples d’applications P2P typiques : téléconférences pour prise de notes collaborative, applications de conversation sans serveur, publicités interactives, sessions de jeux en ligne.</span><span class="sxs-lookup"><span data-stu-id="91d56-126">Typical P2P applications are: conference calls for collaborative note-taking or whiteboarding, serverless chat applications, interactive advertisements, and online gaming sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d56-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91d56-127">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>
