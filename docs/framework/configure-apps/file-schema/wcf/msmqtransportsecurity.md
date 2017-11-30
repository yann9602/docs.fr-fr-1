---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: eee2cb916d79bf3b79e882cd757b10344121f6b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="c9d8c-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="c9d8c-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="c9d8c-103">Spécifie des paramètres de sécurité de transport MSMQ pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="c9d8c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c9d8c-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-105">\<bindings></span></span>  
<span data-ttu-id="c9d8c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-106">\<customBinding></span></span>  
<span data-ttu-id="c9d8c-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-107">\<binding></span></span>  
<span data-ttu-id="c9d8c-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-108">\<msmqIntegration></span></span>  
<span data-ttu-id="c9d8c-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d8c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d8c-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9d8c-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c9d8c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9d8c-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9d8c-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c9d8c-113">Attributes</span></span>  
  
|<span data-ttu-id="c9d8c-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="c9d8c-114">Attribute</span></span>|<span data-ttu-id="c9d8c-115">Description</span><span class="sxs-lookup"><span data-stu-id="c9d8c-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="c9d8c-116">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="c9d8c-117">S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="c9d8c-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9d8c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9d8c-119">-None : Aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-119">-   None: No authentication.</span></span><br /><span data-ttu-id="c9d8c-120">-Windows : Le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X.509 du SID associé au message.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="c9d8c-121">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="c9d8c-122">-Certificate : Le canal Obtient le certificat du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="c9d8c-123">La valeur par défaut est Windows.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-123">The default value is Windows.</span></span> <span data-ttu-id="c9d8c-124">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="c9d8c-125">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="c9d8c-126">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9d8c-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9d8c-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="c9d8c-127">-   RC4Stream</span></span><br /><span data-ttu-id="c9d8c-128">-AES</span><span class="sxs-lookup"><span data-stu-id="c9d8c-128">-   AES</span></span><br /><br /> <span data-ttu-id="c9d8c-129">La valeur par défaut est RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-129">The default value is RC4Stream.</span></span> <span data-ttu-id="c9d8c-130">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="c9d8c-131">Spécifie le mode de sécurisation du message au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="c9d8c-132">Le chiffrement garantit l'intégrité des messages tandis que EncryptAndSign garantit à la fois l'intégrité des messages et leur non-rejet ; autrement dit, le message vient en effet de l'expéditeur et c'est celui-ci qui se déclare lui-même.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="c9d8c-133">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9d8c-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9d8c-134">-None : Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-134">-   None: No protection.</span></span><br /><span data-ttu-id="c9d8c-135">-Sign : Les Messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="c9d8c-136">-EncryptAndSign : Les Messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="c9d8c-137">La valeur par défaut est Sign.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-137">The default value is Sign.</span></span> <span data-ttu-id="c9d8c-138">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="c9d8c-139">Spécifie l'algorithme à utiliser pour calculer le message condensé dans le cadre des signatures.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="c9d8c-140">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9d8c-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9d8c-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="c9d8c-141">-   MD5</span></span><br /><span data-ttu-id="c9d8c-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="c9d8c-142">-   SHA1</span></span><br /><span data-ttu-id="c9d8c-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="c9d8c-143">-   SHA256</span></span><br /><span data-ttu-id="c9d8c-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="c9d8c-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="c9d8c-145">La valeur par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-145">The default value is SHA1.</span></span> <span data-ttu-id="c9d8c-146">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9d8c-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c9d8c-147">Child Elements</span></span>  
 <span data-ttu-id="c9d8c-148">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9d8c-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c9d8c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="c9d8c-150">Élément</span><span class="sxs-lookup"><span data-stu-id="c9d8c-150">Element</span></span>|<span data-ttu-id="c9d8c-151">Description</span><span class="sxs-lookup"><span data-stu-id="c9d8c-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9d8c-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="c9d8c-153">Spécifie des paramètres requis pour l'interaction avec un expéditeur ou un récepteur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="c9d8c-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="c9d8c-155">Spécifie les propriétés de communication mises en file d'attente pour un service Windows Communication Foundation (WCF) qui utilise le protocole MSMQ natif.</span><span class="sxs-lookup"><span data-stu-id="c9d8c-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9d8c-156">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9d8c-156">Remarks</span></span>  
 <span data-ttu-id="c9d8c-157">Pour plus d’informations sur la sécurité de transport, consultez [sécurité du Transport](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="c9d8c-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d8c-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d8c-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c9d8c-159">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="c9d8c-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="c9d8c-160">Transports</span><span class="sxs-lookup"><span data-stu-id="c9d8c-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="c9d8c-161">Choix d’un Transport</span><span class="sxs-lookup"><span data-stu-id="c9d8c-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="c9d8c-162">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c9d8c-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c9d8c-163">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="c9d8c-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c9d8c-164">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c9d8c-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c9d8c-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c9d8c-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="c9d8c-166">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="c9d8c-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
