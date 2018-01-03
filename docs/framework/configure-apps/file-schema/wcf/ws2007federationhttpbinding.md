---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28e4cc9189c144404bcfe2b7f8e255a74eef76c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="f3553-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f3553-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="f3553-103">Une liaison sécurisée et interopérable qui dérive de [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et prend en charge la sécurité fédérée.</span><span class="sxs-lookup"><span data-stu-id="f3553-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="f3553-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f3553-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3553-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="f3553-105">\<bindings></span></span>  
<span data-ttu-id="f3553-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f3553-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3553-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3553-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3553-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f3553-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3553-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f3553-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3553-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f3553-110">Attributes</span></span>  
  
|<span data-ttu-id="f3553-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f3553-111">Attribute</span></span>|<span data-ttu-id="f3553-112">Description</span><span class="sxs-lookup"><span data-stu-id="f3553-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="f3553-113">Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="f3553-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f3553-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f3553-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="f3553-115"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="f3553-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f3553-116">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f3553-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f3553-117">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f3553-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="f3553-118">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="f3553-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f3553-119">Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="f3553-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f3553-120">La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="f3553-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f3553-121">Taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f3553-122">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="f3553-122">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="f3553-123">De nombreux éléments de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="f3553-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="f3553-124">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="f3553-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f3553-125">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="f3553-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f3553-126">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="f3553-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f3553-127">Taille maximale du message (en octets), en-têtes compris, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f3553-128">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="f3553-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="f3553-129">Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="f3553-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f3553-130">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="f3553-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="f3553-131">Définit l'encodeur utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="f3553-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="f3553-132">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3553-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f3553-133">-Text : Utiliser un encodeur de message texte.</span><span class="sxs-lookup"><span data-stu-id="f3553-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f3553-134">-Mtom : Utiliser un encodeur Message Transmission Organization Mechanism 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f3553-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="f3553-135">La valeur par défaut est Text.</span><span class="sxs-lookup"><span data-stu-id="f3553-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="f3553-136">Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f3553-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="f3553-137">Nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-137">The configuration name of the binding.</span></span> <span data-ttu-id="f3553-138">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f3553-139">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="f3553-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f3553-140">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f3553-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f3553-141"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="f3553-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f3553-142">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f3553-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f3553-143">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f3553-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="f3553-144">URI d'emplacement de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="f3553-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="f3553-145">Numéro de version de l'avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="f3553-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="f3553-146">URI qui spécifie l'adresse du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3553-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="f3553-147">Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="f3553-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="f3553-148">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="f3553-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f3553-149"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="f3553-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f3553-150">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f3553-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f3553-151">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f3553-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f3553-152"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f3553-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f3553-153">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f3553-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f3553-154">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f3553-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="f3553-155">Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f3553-156">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3553-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f3553-157">-BigEndianUnicode : Encodage Unicode Big Endian.</span><span class="sxs-lookup"><span data-stu-id="f3553-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="f3553-158">-Unicode : encodage de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="f3553-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f3553-159">-Encodage UTF-8 : 8 bits.</span><span class="sxs-lookup"><span data-stu-id="f3553-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="f3553-160">La valeur par défaut est UTF8.</span><span class="sxs-lookup"><span data-stu-id="f3553-160">The default is UTF8.</span></span> <span data-ttu-id="f3553-161">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f3553-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="f3553-162">Valeur indiquant si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="f3553-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f3553-163">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f3553-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="f3553-164">Valeur indiquant si le proxy HTTP du système configuré automatiquement est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f3553-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="f3553-165">L'adresse proxy doit être `null` (autrement dit, pas de jeu) si cet attribut est `true`.</span><span class="sxs-lookup"><span data-stu-id="f3553-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="f3553-166">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="f3553-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3553-167">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f3553-167">Child Elements</span></span>  
  
|<span data-ttu-id="f3553-168">Élément</span><span class="sxs-lookup"><span data-stu-id="f3553-168">Element</span></span>|<span data-ttu-id="f3553-169">Description</span><span class="sxs-lookup"><span data-stu-id="f3553-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3553-170">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="f3553-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="f3553-171">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="f3553-171">Defines the security settings for the message.</span></span> <span data-ttu-id="f3553-172">Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f3553-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="f3553-173">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="f3553-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f3553-174">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="f3553-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f3553-175">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f3553-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f3553-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="f3553-176">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="f3553-177">Indique si des sessions fiables sont établies entre les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="f3553-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3553-178">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f3553-178">Parent Elements</span></span>  
  
|<span data-ttu-id="f3553-179">Élément</span><span class="sxs-lookup"><span data-stu-id="f3553-179">Element</span></span>|<span data-ttu-id="f3553-180">Description</span><span class="sxs-lookup"><span data-stu-id="f3553-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3553-181">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="f3553-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="f3553-182">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f3553-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3553-183">Notes</span><span class="sxs-lookup"><span data-stu-id="f3553-183">Remarks</span></span>  
 <span data-ttu-id="f3553-184">La fédération est la capacité à partager des identités entre plusieurs entreprises ou domaines approuvés à des fins d'authentification et d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="f3553-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="f3553-185">Elle utilise le protocole WS-Trust pour mapper la représentation d'identité entre domaines approuvés.</span><span class="sxs-lookup"><span data-stu-id="f3553-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="f3553-186">Une liaison HTTP fédérée prend en charge la sécurité SOAP ainsi que la sécurité en mode mixte, mais pas la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="f3553-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="f3553-187">Les services configurés avec cette liaison doivent utiliser le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3553-187">Services configured with this binding must use the HTTP transport.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="f3553-188">[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f3553-188"> [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3553-189">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3553-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3553-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3553-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="f3553-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f3553-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="f3553-192">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f3553-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f3553-193">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f3553-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f3553-194">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f3553-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f3553-195">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f3553-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
