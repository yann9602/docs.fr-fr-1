---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26ed0c9dd2c895d4a01536a5715c6235ff65df7b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="0e180-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0e180-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="0e180-103">Élément de configuration utilisé pour configurer la liaison <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0e180-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="0e180-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0e180-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e180-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="0e180-105">\<bindings></span></span>  
<span data-ttu-id="0e180-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="0e180-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e180-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e180-107">Syntax</span></span>  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e180-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0e180-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0e180-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0e180-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e180-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0e180-110">Attributes</span></span>  
  
|<span data-ttu-id="0e180-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0e180-111">Attribute</span></span>|<span data-ttu-id="0e180-112">Description</span><span class="sxs-lookup"><span data-stu-id="0e180-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0e180-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0e180-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0e180-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e180-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e180-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e180-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="0e180-116">Valeur entière qui spécifie la longueur d'historique de messages dupliqués.</span><span class="sxs-lookup"><span data-stu-id="0e180-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="0e180-117">Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.</span><span class="sxs-lookup"><span data-stu-id="0e180-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="0e180-118">La valeur par défaut est de 524 288 (0x80000) octets.</span><span class="sxs-lookup"><span data-stu-id="0e180-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="0e180-119">Entier qui spécifie la taille maximale, en octets, d'une mémoire tampon qui stocke des messages pendant qu'ils sont traités pour un point de terminaison configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="0e180-120">La valeur par défaut est de 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0e180-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="0e180-121">Valeur entière qui spécifie le nombre maximal de messages reçus qui n'ont pas encore été supprimés dans la file d'entrée pour une instance de canal individuelle.</span><span class="sxs-lookup"><span data-stu-id="0e180-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="0e180-122">Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d'un message pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0e180-123">L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="0e180-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="0e180-124">Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="0e180-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0e180-125">La valeur par défaut est 65 536 octets.</span><span class="sxs-lookup"><span data-stu-id="0e180-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="0e180-126">Valeur entière qui spécifie le nombre maximal de retransmissions de messages.</span><span class="sxs-lookup"><span data-stu-id="0e180-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="0e180-127">Valeur entière qui spécifie l'ID d'interface de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="0e180-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="0e180-128">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0e180-129">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0e180-130">Chaque liaison porte un `name` et a un attribut `namespace` qui l'identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="0e180-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="0e180-131">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="0e180-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="0e180-132">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="0e180-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0e180-133">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0e180-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0e180-134"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="0e180-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0e180-135">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e180-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e180-136">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e180-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0e180-137"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="0e180-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0e180-138">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e180-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e180-139">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0e180-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0e180-140"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0e180-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0e180-141">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0e180-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e180-142">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0e180-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="0e180-143">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0e180-144">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e180-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e180-145">-BigEndianUnicode : Encodage Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="0e180-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0e180-146">-Unicode : encodage de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="0e180-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0e180-147">-UTF8 : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="0e180-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0e180-148">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="0e180-148">The default is UTF8.</span></span> <span data-ttu-id="0e180-149">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0e180-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="0e180-150">Une valeur de période qui spécifie la durée de vie de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e180-151">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0e180-151">Child Elements</span></span>  
  
|<span data-ttu-id="0e180-152">Élément</span><span class="sxs-lookup"><span data-stu-id="0e180-152">Element</span></span>|<span data-ttu-id="0e180-153">Description</span><span class="sxs-lookup"><span data-stu-id="0e180-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e180-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="0e180-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="0e180-155">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0e180-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0e180-156">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0e180-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e180-157">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0e180-157">Parent Elements</span></span>  
  
|<span data-ttu-id="0e180-158">Élément</span><span class="sxs-lookup"><span data-stu-id="0e180-158">Element</span></span>|<span data-ttu-id="0e180-159">Description</span><span class="sxs-lookup"><span data-stu-id="0e180-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e180-160">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="0e180-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="0e180-161">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0e180-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e180-162">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e180-162">Remarks</span></span>  
 <span data-ttu-id="0e180-163">UdpBinding permet aux services WCF de communiquer sur le transport UDP.</span><span class="sxs-lookup"><span data-stu-id="0e180-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="0e180-164">Il permet des échanges de messages « fire and forget » où un client envoie un message à un service et attend pas de réponse.</span><span class="sxs-lookup"><span data-stu-id="0e180-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e180-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e180-165">Example</span></span>  
 <span data-ttu-id="0e180-166">L'exemple suivant indique comment configurer <xref:System.ServiceModel.UdpBinding> à l'aide de l'élément <`udpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="0e180-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>  
        <binding  closeTimeout="00:10:00"  
                   duplicateMessageHistoryLength="100"  
                   maxBufferPoolSize="100"  
                   maxPendingMessagesTotalSize="100000"  
                   maxReceivedMessageSize="65536"  
                    maxRetransmitCount="10"  
                   multicastInterfaceId="00000"  
                   name="myUdpBinding"  
                   openTimeout="00:10:00"  
                   receiveTimeout="00:10:00"  
                   sendTimeout="00:10:00"  
                   textEncoding="utf-8"  
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e180-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e180-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="0e180-168">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0e180-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0e180-169">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0e180-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0e180-170">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="0e180-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0e180-171">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="0e180-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
