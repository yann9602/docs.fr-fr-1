---
title: '&lt;transport&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2df5bf18605fcf20b253212cb0f9a62b4719b0ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="9deb8-102">&lt;transport&gt; de &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9deb8-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="9deb8-103">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="9deb8-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="9deb8-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9deb8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9deb8-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="9deb8-105">\<bindings></span></span>  
<span data-ttu-id="9deb8-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="9deb8-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="9deb8-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="9deb8-107">\<binding></span></span>  
<span data-ttu-id="9deb8-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="9deb8-108">\<security></span></span>  
<span data-ttu-id="9deb8-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="9deb8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9deb8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9deb8-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9deb8-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9deb8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9deb8-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9deb8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9deb8-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9deb8-113">Attributes</span></span>  
  
|<span data-ttu-id="9deb8-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="9deb8-114">Attribute</span></span>|<span data-ttu-id="9deb8-115">Description</span><span class="sxs-lookup"><span data-stu-id="9deb8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9deb8-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="9deb8-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="9deb8-117">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9deb8-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="9deb8-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9deb8-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9deb8-119">-None : Aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="9deb8-119">-   None: No authentication.</span></span><br /><span data-ttu-id="9deb8-120">-WindowsDomain : Le mécanisme d’authentification utilise Active Directory pour récupérer le certificat X.509 pour l’identificateur de sécurité associé au message.</span><span class="sxs-lookup"><span data-stu-id="9deb8-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="9deb8-121">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation en écriture dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9deb8-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="9deb8-122">-Certificate : Le canal extrait le certificat du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="9deb8-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="9deb8-123">La valeur par défaut est `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="9deb8-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="9deb8-124">Si cet attribut a la valeur `None`, l'attribut `msmqProtectionLevel` doit également être défini à `None`.</span><span class="sxs-lookup"><span data-stu-id="9deb8-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="9deb8-125">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="9deb8-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="9deb8-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="9deb8-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="9deb8-127">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="9deb8-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="9deb8-128">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9deb8-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9deb8-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="9deb8-129">-   RC4Stream</span></span><br /><span data-ttu-id="9deb8-130">-AES</span><span class="sxs-lookup"><span data-stu-id="9deb8-130">-   AES</span></span><br /><span data-ttu-id="9deb8-131">-La valeur par défaut est `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="9deb8-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="9deb8-132">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="9deb8-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="9deb8-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="9deb8-133">msmqProtectionLevel</span></span>|<span data-ttu-id="9deb8-134">Spécifie la façon dont les messages sont sécurisés au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9deb8-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="9deb8-135">Le chiffrement garantit l'intégrité des messages, tandis que la signature et le chiffrement garantissent à la fois l'intégrité et le non-rejet des messages.</span><span class="sxs-lookup"><span data-stu-id="9deb8-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="9deb8-136">Autrement dit, le message a été effectivement envoyé par l'expéditeur et l'expéditeur est celui qu'il prétend.</span><span class="sxs-lookup"><span data-stu-id="9deb8-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="9deb8-137">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9deb8-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9deb8-138">-None : Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="9deb8-138">-   None: No protection.</span></span><br /><span data-ttu-id="9deb8-139">-Sign : Les Messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="9deb8-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="9deb8-140">-EncryptAndSign : Les Messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="9deb8-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="9deb8-141">-La valeur par défaut est `Sign`.</span><span class="sxs-lookup"><span data-stu-id="9deb8-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="9deb8-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="9deb8-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="9deb8-143">Spécifie l'algorithme de hachage à utiliser pour calculer le résumé de message.</span><span class="sxs-lookup"><span data-stu-id="9deb8-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="9deb8-144">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9deb8-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9deb8-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="9deb8-145">-   MD5</span></span><br /><span data-ttu-id="9deb8-146">-SHA1</span><span class="sxs-lookup"><span data-stu-id="9deb8-146">-   SHA1</span></span><br /><span data-ttu-id="9deb8-147">-SHA256</span><span class="sxs-lookup"><span data-stu-id="9deb8-147">-   SHA256</span></span><br /><span data-ttu-id="9deb8-148">-SHA512</span><span class="sxs-lookup"><span data-stu-id="9deb8-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="9deb8-149">La valeur par défaut est `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="9deb8-149">The default is `SHA1`.</span></span> <span data-ttu-id="9deb8-150">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="9deb8-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9deb8-151">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9deb8-151">Child Elements</span></span>  
 <span data-ttu-id="9deb8-152">None</span><span class="sxs-lookup"><span data-stu-id="9deb8-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9deb8-153">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9deb8-153">Parent Elements</span></span>  
  
|<span data-ttu-id="9deb8-154">Élément</span><span class="sxs-lookup"><span data-stu-id="9deb8-154">Element</span></span>|<span data-ttu-id="9deb8-155">Description</span><span class="sxs-lookup"><span data-stu-id="9deb8-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9deb8-156">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="9deb8-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="9deb8-157">Définit les paramètres de sécurité de transport pour les transports de mise en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9deb8-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9deb8-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9deb8-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="9deb8-159">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="9deb8-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="9deb8-160">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="9deb8-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9deb8-161">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9deb8-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9deb8-162">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="9deb8-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9deb8-163">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9deb8-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9deb8-164">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="9deb8-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
