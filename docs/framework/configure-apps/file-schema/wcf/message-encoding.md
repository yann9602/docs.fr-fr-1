---
title: Encodage de message
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b0147049a988a8fa2d0721da39f1d9c37278803
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="message-encoding"></a><span data-ttu-id="b9d24-102">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="b9d24-102">Message Encoding</span></span>
<span data-ttu-id="b9d24-103">L'encodage est le processus de transformation d'un jeu de caractères Unicode en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="b9d24-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="b9d24-104">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="b9d24-104">Decoding is the reverse process.</span></span> <span data-ttu-id="b9d24-105">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b9d24-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b9d24-106">La section de configuration `binaryMessageEncoding` spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML binaires.</span><span class="sxs-lookup"><span data-stu-id="b9d24-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="b9d24-107">L'encodeur de message binaire encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="b9d24-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="b9d24-108">Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS-* est perdue.</span><span class="sxs-lookup"><span data-stu-id="b9d24-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
 <span data-ttu-id="b9d24-109">La section de configuration `mtomMessageEncoding` spécifie l'encodage de caractères et le suivi des versions de message utilisés pour un message employant un encodage MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b9d24-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="b9d24-110">MTOM est une technologie efficace pour la transmission de données binaires dans les messages de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b9d24-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="b9d24-111">L'encodeur MTOM tente de parvenir à un équilibre entre rendement et interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="b9d24-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="b9d24-112">L'encodage MTOM transmet la plupart du XML sous forme textuelle, mais optimise les grands blocs de données binaires en les transmettant tels quels, sans conversion en texte.</span><span class="sxs-lookup"><span data-stu-id="b9d24-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="b9d24-113">La section de configuration `textMessageEncoding` spécifie un encodeur de texte utilisé pour créer des messages textuels sur le câble.</span><span class="sxs-lookup"><span data-stu-id="b9d24-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="b9d24-114">Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-*.</span><span class="sxs-lookup"><span data-stu-id="b9d24-114">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="b9d24-115">Les services Web ou les clients de ces services comprennent généralement le XML textuel.</span><span class="sxs-lookup"><span data-stu-id="b9d24-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="b9d24-116">Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.</span><span class="sxs-lookup"><span data-stu-id="b9d24-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d24-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9d24-117">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [<span data-ttu-id="b9d24-118">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b9d24-118">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b9d24-119">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="b9d24-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b9d24-120">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="b9d24-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b9d24-121">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b9d24-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b9d24-122">Choix d’un encodeur de Message</span><span class="sxs-lookup"><span data-stu-id="b9d24-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
