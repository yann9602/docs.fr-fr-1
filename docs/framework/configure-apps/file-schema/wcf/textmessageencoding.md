---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ac17ead3c7054f0125527e3992fe865624770a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="dbcdd-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="dbcdd-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="dbcdd-103">Spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML textuels.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="dbcdd-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dbcdd-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-105">\<bindings></span></span>  
<span data-ttu-id="dbcdd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-106">\<customBinding></span></span>  
<span data-ttu-id="dbcdd-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-107">\<binding></span></span>  
<span data-ttu-id="dbcdd-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbcdd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbcdd-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbcdd-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dbcdd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbcdd-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbcdd-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dbcdd-112">Attributes</span></span>  
  
|<span data-ttu-id="dbcdd-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="dbcdd-113">Attribute</span></span>|<span data-ttu-id="dbcdd-114">Description</span><span class="sxs-lookup"><span data-stu-id="dbcdd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbcdd-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="dbcdd-115">maxReadPoolSize</span></span>|<span data-ttu-id="dbcdd-116">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="dbcdd-117">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dbcdd-118">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-118">The default is 64.</span></span>|  
|<span data-ttu-id="dbcdd-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="dbcdd-119">maxWritePoolSize</span></span>|<span data-ttu-id="dbcdd-120">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="dbcdd-121">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dbcdd-122">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-122">The default is 16.</span></span>|  
|<span data-ttu-id="dbcdd-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="dbcdd-123">messageVersion</span></span>|<span data-ttu-id="dbcdd-124">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="dbcdd-125">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="dbcdd-125">Valid values are</span></span><br /><br /> <span data-ttu-id="dbcdd-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="dbcdd-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="dbcdd-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="dbcdd-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="dbcdd-128">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="dbcdd-129">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="dbcdd-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="dbcdd-130">writeEncoding</span></span>|<span data-ttu-id="dbcdd-131">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="dbcdd-132">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="dbcdd-132">Valid values are</span></span><br /><br /> <span data-ttu-id="dbcdd-133">-UnicodeFffeTextEncoding : Unicode BigEndian encodage</span><span class="sxs-lookup"><span data-stu-id="dbcdd-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="dbcdd-134">-Utf16TextEncoding : L’encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="dbcdd-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="dbcdd-135">-Utf8TextEncoding : encodage de 8 bits</span><span class="sxs-lookup"><span data-stu-id="dbcdd-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="dbcdd-136">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="dbcdd-137">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbcdd-138">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dbcdd-138">Child Elements</span></span>  
  
|<span data-ttu-id="dbcdd-139">Élément</span><span class="sxs-lookup"><span data-stu-id="dbcdd-139">Element</span></span>|<span data-ttu-id="dbcdd-140">Description</span><span class="sxs-lookup"><span data-stu-id="dbcdd-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbcdd-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="dbcdd-142">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dbcdd-143">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbcdd-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dbcdd-144">Parent Elements</span></span>  
  
|<span data-ttu-id="dbcdd-145">Élément</span><span class="sxs-lookup"><span data-stu-id="dbcdd-145">Element</span></span>|<span data-ttu-id="dbcdd-146">Description</span><span class="sxs-lookup"><span data-stu-id="dbcdd-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbcdd-147">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="dbcdd-148">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbcdd-149">Notes</span><span class="sxs-lookup"><span data-stu-id="dbcdd-149">Remarks</span></span>  
 <span data-ttu-id="dbcdd-150">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="dbcdd-151">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-151">Decoding is the reverse process.</span></span> <span data-ttu-id="dbcdd-152">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="dbcdd-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="dbcdd-153">L'encodage de texte représenté par l'élément `textMessageEncoding` est l'encodeur le plus interopérable, mais le moins efficace pour les messages XML.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="dbcdd-154">L'encodeur de texte crée des messages textuels sur le câble.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="dbcdd-155">Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-*.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="dbcdd-156">Les services Web ou les clients de ces services comprennent généralement le XML textuel.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="dbcdd-157">Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbcdd-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbcdd-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbcdd-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbcdd-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="dbcdd-160">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="dbcdd-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="dbcdd-161">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="dbcdd-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="dbcdd-162">Liaisons</span><span class="sxs-lookup"><span data-stu-id="dbcdd-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dbcdd-163">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="dbcdd-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="dbcdd-164">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="dbcdd-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="dbcdd-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dbcdd-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
