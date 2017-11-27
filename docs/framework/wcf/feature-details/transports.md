---
title: Transports dans Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="5ac76-102">Transports dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5ac76-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="5ac76-103">La couche de transport se situe au niveau le plus bas de la pile des canaux.</span><span class="sxs-lookup"><span data-stu-id="5ac76-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="5ac76-104">Les principaux transports utilisés dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont HTTP, HTTPS, TCP ainsi que les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="5ac76-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="5ac76-105">Les rubriques de cette section contiennent des conseils et des instructions permettant de savoir quel protocole choisir, de le configurer et de définir les propriétés de réglage afférentes.</span><span class="sxs-lookup"><span data-stu-id="5ac76-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5ac76-106"> comporte des transports supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5ac76-106"> includes additional transports.</span></span> <span data-ttu-id="5ac76-107">Pour plus d’informations sur le transport Message Queuing (également appelé MSMQ), consultez [les files d’attente et les Sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="5ac76-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="5ac76-108">Pour plus d’informations sur le transport d’homologue à homologue, consultez [mise en réseau pair à pair](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5ac76-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ac76-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ac76-109">In This Section</span></span>  
 [<span data-ttu-id="5ac76-110">Choix d’un Transport</span><span class="sxs-lookup"><span data-stu-id="5ac76-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="5ac76-111">Présente les trois transports principaux et aborde les différents points à prendre en considération lors de leur sélection.</span><span class="sxs-lookup"><span data-stu-id="5ac76-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="5ac76-112">Choix d’un encodeur de Message</span><span class="sxs-lookup"><span data-stu-id="5ac76-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="5ac76-113">Aborde les facteurs à prendre en considération lors de la sélection d’un élément de liaison d’encodage de message.</span><span class="sxs-lookup"><span data-stu-id="5ac76-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="5ac76-114">Transfert de messages en continu</span><span class="sxs-lookup"><span data-stu-id="5ac76-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="5ac76-115">Contient des instructions permettant de configurer la couche de transport pour une diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="5ac76-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="5ac76-116">Configuration de HTTP et HTTPS</span><span class="sxs-lookup"><span data-stu-id="5ac76-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="5ac76-117">Contient des instructions permettant de configurer les éléments de liaison de transport HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5ac76-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="5ac76-118">Comment : remplacer la réservation d’URL WCF par une réservation restreinte</span><span class="sxs-lookup"><span data-stu-id="5ac76-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="5ac76-119">Décrit comment utiliser les réservations restreintes de l'URL de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ac76-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="5ac76-120">Quotas de transport</span><span class="sxs-lookup"><span data-stu-id="5ac76-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="5ac76-121">Aborde les points à prendre en considération lors de la définition de quotas pour la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="5ac76-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="5ac76-122">Utilisation des NAT et pare-feu</span><span class="sxs-lookup"><span data-stu-id="5ac76-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="5ac76-123">Contient des instructions permettant de configurer la couche de transport lorsque les messages envoyés ou reçus rencontrent un pare-feu ou lorsqu'un traducteur d'adresses réseau (NAT) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5ac76-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="5ac76-124">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5ac76-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="5ac76-125">Contient des instructions permettant d'utiliser le partage de port Net.TCP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ac76-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ac76-126">Référence</span><span class="sxs-lookup"><span data-stu-id="5ac76-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="5ac76-127">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="5ac76-127">Related Sections</span></span>  
 [<span data-ttu-id="5ac76-128">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5ac76-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="5ac76-129">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="5ac76-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
