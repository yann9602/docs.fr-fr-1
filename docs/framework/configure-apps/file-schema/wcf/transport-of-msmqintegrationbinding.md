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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03cd07681c111f51a4ea02ac46354fa9a19f42d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="eb773-102">&lt;transport&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="eb773-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="eb773-103">Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="eb773-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="eb773-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="eb773-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb773-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="eb773-105">\<bindings></span></span>  
<span data-ttu-id="eb773-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="eb773-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="eb773-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="eb773-107">\<binding></span></span>  
<span data-ttu-id="eb773-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="eb773-108">\<security></span></span>  
<span data-ttu-id="eb773-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="eb773-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb773-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb773-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb773-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eb773-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eb773-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eb773-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb773-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="eb773-113">Attributes</span></span>  
  
|<span data-ttu-id="eb773-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="eb773-114">Attribute</span></span>|<span data-ttu-id="eb773-115">Description</span><span class="sxs-lookup"><span data-stu-id="eb773-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="eb773-116">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eb773-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="eb773-117">S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.</span><span class="sxs-lookup"><span data-stu-id="eb773-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="eb773-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb773-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="eb773-119">-None : Aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="eb773-119">-   None: No authentication.</span></span><br /><span data-ttu-id="eb773-120">-WindowsDomain : Le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X.509 du SID associé au message.</span><span class="sxs-lookup"><span data-stu-id="eb773-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="eb773-121">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="eb773-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="eb773-122">-Certificate : Le canal Obtient le certificat du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="eb773-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="eb773-123">La valeur par défaut est WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="eb773-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="eb773-124">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="eb773-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="eb773-125">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="eb773-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="eb773-126">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb773-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="eb773-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="eb773-127">-   RC4Stream</span></span><br /><span data-ttu-id="eb773-128">-AES</span><span class="sxs-lookup"><span data-stu-id="eb773-128">-   AES</span></span><br /><br /> <span data-ttu-id="eb773-129">La valeur par défaut est RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="eb773-129">The default value is RC4Stream.</span></span> <span data-ttu-id="eb773-130">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="eb773-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="eb773-131">Spécifie le mode de sécurisation du message au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eb773-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="eb773-132">Le chiffrement garantit l'intégrité des messages tandis que EncryptAndSign garantit à la fois l'intégrité des messages et leur non-rejet ; autrement dit, le message vient en effet de l'expéditeur et c'est celui-ci qui se déclare lui-même.</span><span class="sxs-lookup"><span data-stu-id="eb773-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="eb773-133">-Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb773-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="eb773-134">-None : Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="eb773-134">-   None: No protection.</span></span><br /><span data-ttu-id="eb773-135">-Sign : Les Messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="eb773-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="eb773-136">-EncryptAndSign : Les Messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="eb773-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="eb773-137">La valeur par défaut est Sign.</span><span class="sxs-lookup"><span data-stu-id="eb773-137">The default value is Sign.</span></span> <span data-ttu-id="eb773-138">Cet attribut est de type ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="eb773-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="eb773-139">-Spécifie l’algorithme à utiliser pour calculer le digest dans le cadre des signatures.</span><span class="sxs-lookup"><span data-stu-id="eb773-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="eb773-140">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb773-140">Valid values include the following:</span></span><br /><span data-ttu-id="eb773-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="eb773-141">-   MD5</span></span><br /><span data-ttu-id="eb773-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="eb773-142">-   SHA1</span></span><br /><span data-ttu-id="eb773-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="eb773-143">-   SHA256</span></span><br /><span data-ttu-id="eb773-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="eb773-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="eb773-145">La valeur par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="eb773-145">The default value is SHA1.</span></span> <span data-ttu-id="eb773-146">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="eb773-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb773-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eb773-147">Child Elements</span></span>  
 <span data-ttu-id="eb773-148">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eb773-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb773-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eb773-149">Parent Elements</span></span>  
  
|<span data-ttu-id="eb773-150">Élément</span><span class="sxs-lookup"><span data-stu-id="eb773-150">Element</span></span>|<span data-ttu-id="eb773-151">Description</span><span class="sxs-lookup"><span data-stu-id="eb773-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb773-152">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="eb773-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="eb773-153">Définit les paramètres de sécurité pour une liaison MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eb773-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb773-154">Notes</span><span class="sxs-lookup"><span data-stu-id="eb773-154">Remarks</span></span>  
 <span data-ttu-id="eb773-155">Cet élément encapsule les paramètres de sécurité pour le transport d'intégration MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eb773-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="eb773-156">Les paramètres sont les mêmes à la fois pour le transport d'intégration Message Queuing et le transport de mise en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="eb773-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="eb773-157">Cet élément vous permet de définir le mode d'authentification, l'algorithme de chiffrement, l'algorithme de hachage sécurisé et le niveau de protection.</span><span class="sxs-lookup"><span data-stu-id="eb773-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb773-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb773-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="eb773-159">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="eb773-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="eb773-160">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="eb773-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="eb773-161">Liaisons</span><span class="sxs-lookup"><span data-stu-id="eb773-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="eb773-162">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="eb773-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="eb773-163">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="eb773-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="eb773-164">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="eb773-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
