---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 165bf4cd1c0c5c1a6adae91650d38984bc47ef6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="83e4e-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="83e4e-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="83e4e-103">Spécifie l'encodage de message sous forme de flux d'octets, avec l'option permettant de spécifier l'encodage de caractères.</span><span class="sxs-lookup"><span data-stu-id="83e4e-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="83e4e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="83e4e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="83e4e-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="83e4e-105">\<bindings></span></span>  
<span data-ttu-id="83e4e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83e4e-106">\<customBinding></span></span>  
<span data-ttu-id="83e4e-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="83e4e-107">\<binding></span></span>  
<span data-ttu-id="83e4e-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="83e4e-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e4e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e4e-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83e4e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="83e4e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83e4e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="83e4e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83e4e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="83e4e-112">Attributes</span></span>  
  
|<span data-ttu-id="83e4e-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="83e4e-113">Attribute</span></span>|<span data-ttu-id="83e4e-114">Description</span><span class="sxs-lookup"><span data-stu-id="83e4e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83e4e-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="83e4e-115">messageVersion</span></span>|<span data-ttu-id="83e4e-116">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="83e4e-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="83e4e-117">Cette propriété ne peut être affectée que de la valeur de version de message <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="83e4e-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="83e4e-118">L'encodeur de message en flux d'octets ne prend pas en charge d'autres versions de message.</span><span class="sxs-lookup"><span data-stu-id="83e4e-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="83e4e-119">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="83e4e-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83e4e-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="83e4e-120">Child Elements</span></span>  
  
|<span data-ttu-id="83e4e-121">Élément</span><span class="sxs-lookup"><span data-stu-id="83e4e-121">Element</span></span>|<span data-ttu-id="83e4e-122">Description</span><span class="sxs-lookup"><span data-stu-id="83e4e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83e4e-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="83e4e-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="83e4e-124">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="83e4e-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="83e4e-125">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="83e4e-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83e4e-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="83e4e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="83e4e-127">Élément</span><span class="sxs-lookup"><span data-stu-id="83e4e-127">Element</span></span>|<span data-ttu-id="83e4e-128">Description</span><span class="sxs-lookup"><span data-stu-id="83e4e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83e4e-129">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="83e4e-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="83e4e-130">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="83e4e-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83e4e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83e4e-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="83e4e-132">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="83e4e-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="83e4e-133">Choix d’un encodeur de Message</span><span class="sxs-lookup"><span data-stu-id="83e4e-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="83e4e-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="83e4e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="83e4e-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="83e4e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="83e4e-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="83e4e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="83e4e-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83e4e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
