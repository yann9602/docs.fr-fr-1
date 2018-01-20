---
title: '&lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a890243ee12202efa9743a6151255525c7f78be2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="0cd7b-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0cd7b-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="0cd7b-103">Définit une liaison pour la messagerie TCP spécifique au canal homologue.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="0cd7b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0cd7b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0cd7b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0cd7b-105">\<bindings></span></span>  
<span data-ttu-id="0cd7b-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0cd7b-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd7b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cd7b-107">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cd7b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0cd7b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0cd7b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cd7b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cd7b-110">Attributes</span></span>  
  
|<span data-ttu-id="0cd7b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0cd7b-111">Attribute</span></span>|<span data-ttu-id="0cd7b-112">Description</span><span class="sxs-lookup"><span data-stu-id="0cd7b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cd7b-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0cd7b-113">closeTimeout</span></span>|<span data-ttu-id="0cd7b-114"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0cd7b-115">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0cd7b-116">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0cd7b-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="0cd7b-117">listenIPAddress</span></span>|<span data-ttu-id="0cd7b-118">Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="0cd7b-119">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-119">The default is `null`.</span></span>|  
|<span data-ttu-id="0cd7b-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0cd7b-120">maxBufferPoolSize</span></span>|<span data-ttu-id="0cd7b-121">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0cd7b-122">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="0cd7b-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0cd7b-123">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0cd7b-124">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0cd7b-125">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0cd7b-126">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0cd7b-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0cd7b-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="0cd7b-128">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0cd7b-129">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0cd7b-130">Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0cd7b-131">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-131">The default is 65536.</span></span>|  
|<span data-ttu-id="0cd7b-132">name</span><span class="sxs-lookup"><span data-stu-id="0cd7b-132">name</span></span>|<span data-ttu-id="0cd7b-133">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0cd7b-134">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0cd7b-135">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0cd7b-136">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0cd7b-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="0cd7b-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0cd7b-137">openTimeout</span></span>|<span data-ttu-id="0cd7b-138"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0cd7b-139">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0cd7b-140">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0cd7b-141">port</span><span class="sxs-lookup"><span data-stu-id="0cd7b-141">port</span></span>|<span data-ttu-id="0cd7b-142">Entier indiquant le port d'interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="0cd7b-143">Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="0cd7b-144">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-144">The default is 0.</span></span>|  
|<span data-ttu-id="0cd7b-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0cd7b-145">receiveTimeout</span></span>|<span data-ttu-id="0cd7b-146"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0cd7b-147">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0cd7b-148">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="0cd7b-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="0cd7b-149">sendTimeout</span></span>|<span data-ttu-id="0cd7b-150"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0cd7b-151">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0cd7b-152">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cd7b-153">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cd7b-153">Child Elements</span></span>  
  
|<span data-ttu-id="0cd7b-154">Élément</span><span class="sxs-lookup"><span data-stu-id="0cd7b-154">Element</span></span>|<span data-ttu-id="0cd7b-155">Description</span><span class="sxs-lookup"><span data-stu-id="0cd7b-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cd7b-156">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="0cd7b-156">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="0cd7b-157">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0cd7b-158">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="0cd7b-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="0cd7b-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="0cd7b-160">Spécifie un programme de résolution d’homologue utilisé par cette liaison pour résoudre un ID de maille d’homologues en adresses IP de point de terminaison de nœuds dans la maille d’homologues.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="0cd7b-161">\<security></span><span class="sxs-lookup"><span data-stu-id="0cd7b-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="0cd7b-162">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-162">Defines the security settings for the message.</span></span> <span data-ttu-id="0cd7b-163">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0cd7b-164">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0cd7b-164">Parent Elements</span></span>  
  
|<span data-ttu-id="0cd7b-165">Élément</span><span class="sxs-lookup"><span data-stu-id="0cd7b-165">Element</span></span>|<span data-ttu-id="0cd7b-166">Description</span><span class="sxs-lookup"><span data-stu-id="0cd7b-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cd7b-167">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0cd7b-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="0cd7b-168">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cd7b-169">Notes</span><span class="sxs-lookup"><span data-stu-id="0cd7b-169">Remarks</span></span>  
 <span data-ttu-id="0cd7b-170">Cette liaison assure la prise en charge de la création d’applications d’égal à égal ou entre plusieurs parties utilisant le transport d’homologue sur TCP.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="0cd7b-171">Chaque nœud homologue peut héberger plusieurs canaux homologues définis avec ce type de liaison.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cd7b-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cd7b-172">Example</span></span>  
 <span data-ttu-id="0cd7b-173">L’exemple suivant montre l’utilisation de la liaison NetPeerTcpBinding, qui fournit la communication pluripartite à l’aide d’un canal homologue.</span><span class="sxs-lookup"><span data-stu-id="0cd7b-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="0cd7b-174">Pour un scénario détaillé de l’utilisation de cette liaison, consultez [Net homologue TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="0cd7b-174">For a detailed scenario of using this binding, see [Net Peer TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cd7b-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cd7b-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="0cd7b-176">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0cd7b-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0cd7b-177">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0cd7b-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0cd7b-178">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="0cd7b-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0cd7b-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="0cd7b-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="0cd7b-180">NET homologue TCP</span><span class="sxs-lookup"><span data-stu-id="0cd7b-180">Net Peer TCP</span></span>](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="0cd7b-181">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="0cd7b-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
