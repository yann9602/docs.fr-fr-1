---
title: '&lt;transport&gt; de &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9def7fbd0082cc7fa9d9f18388604383cb71f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="f2ee3-102">&lt;transport&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f2ee3-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="f2ee3-103">Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="f2ee3-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2ee3-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-105">\<bindings></span></span>  
<span data-ttu-id="f2ee3-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="f2ee3-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="f2ee3-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-107">\<binding></span></span>  
<span data-ttu-id="f2ee3-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-108">\<security></span></span>  
<span data-ttu-id="f2ee3-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ee3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ee3-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2ee3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f2ee3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f2ee3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2ee3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f2ee3-113">Attributes</span></span>  
  
|<span data-ttu-id="f2ee3-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="f2ee3-114">Attribute</span></span>|<span data-ttu-id="f2ee3-115">Description</span><span class="sxs-lookup"><span data-stu-id="f2ee3-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="f2ee3-116">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="f2ee3-117">S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="f2ee3-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2ee3-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f2ee3-119">-None : Aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-119">-   None: No authentication.</span></span><br /><span data-ttu-id="f2ee3-120">-WindowsDomain : Le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X.509 du SID associé au message.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="f2ee3-121">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="f2ee3-122">-Certificate : Le canal Obtient le certificat du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="f2ee3-123">La valeur par défaut est WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="f2ee3-124">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="f2ee3-125">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="f2ee3-126">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2ee3-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f2ee3-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="f2ee3-127">-   RC4Stream</span></span><br /><span data-ttu-id="f2ee3-128">-AES</span><span class="sxs-lookup"><span data-stu-id="f2ee3-128">-   AES</span></span><br /><br /> <span data-ttu-id="f2ee3-129">La valeur par défaut est RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-129">The default value is RC4Stream.</span></span> <span data-ttu-id="f2ee3-130">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="f2ee3-131">Spécifie le mode de sécurisation du message au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="f2ee3-132">Le chiffrement garantit l'intégrité des messages tandis que EncryptAndSign garantit à la fois l'intégrité des messages et leur non-rejet ; autrement dit, le message vient en effet de l'expéditeur et c'est celui-ci qui se déclare lui-même.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="f2ee3-133">-Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2ee3-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="f2ee3-134">-None : Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-134">-   None: No protection.</span></span><br /><span data-ttu-id="f2ee3-135">-Sign : Les Messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f2ee3-136">-EncryptAndSign : Les Messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f2ee3-137">La valeur par défaut est Sign.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-137">The default value is Sign.</span></span> <span data-ttu-id="f2ee3-138">Cet attribut est de type ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="f2ee3-139">-Spécifie l’algorithme à utiliser pour calculer le digest dans le cadre des signatures.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="f2ee3-140">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2ee3-140">Valid values include the following:</span></span><br /><span data-ttu-id="f2ee3-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="f2ee3-141">-   MD5</span></span><br /><span data-ttu-id="f2ee3-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="f2ee3-142">-   SHA1</span></span><br /><span data-ttu-id="f2ee3-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="f2ee3-143">-   SHA256</span></span><br /><span data-ttu-id="f2ee3-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="f2ee3-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="f2ee3-145">La valeur par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-145">The default value is SHA1.</span></span> <span data-ttu-id="f2ee3-146">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2ee3-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f2ee3-147">Child Elements</span></span>  
 <span data-ttu-id="f2ee3-148">None</span><span class="sxs-lookup"><span data-stu-id="f2ee3-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2ee3-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f2ee3-149">Parent Elements</span></span>  
  
|<span data-ttu-id="f2ee3-150">Élément</span><span class="sxs-lookup"><span data-stu-id="f2ee3-150">Element</span></span>|<span data-ttu-id="f2ee3-151">Description</span><span class="sxs-lookup"><span data-stu-id="f2ee3-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2ee3-152">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="f2ee3-153">Définit les paramètres de sécurité pour une liaison MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2ee3-154">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2ee3-154">Remarks</span></span>  
 <span data-ttu-id="f2ee3-155">Cet élément encapsule les paramètres de sécurité pour le transport d'intégration MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f2ee3-156">Les paramètres sont les mêmes à la fois pour le transport d'intégration Message Queuing et le transport de mise en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="f2ee3-157">Cet élément vous permet de définir le mode d'authentification, l'algorithme de chiffrement, l'algorithme de hachage sécurisé et le niveau de protection.</span><span class="sxs-lookup"><span data-stu-id="f2ee3-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ee3-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ee3-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="f2ee3-159">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="f2ee3-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f2ee3-160">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="f2ee3-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f2ee3-161">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f2ee3-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f2ee3-162">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f2ee3-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f2ee3-163">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f2ee3-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f2ee3-164">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f2ee3-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
