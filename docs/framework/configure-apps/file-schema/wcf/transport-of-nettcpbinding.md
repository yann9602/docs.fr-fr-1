---
title: '&lt;transport&gt; de &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad2271b86d37d9063ac54d9a4e45681d132eb1d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="a95e0-102">&lt;transport&gt; de &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a95e0-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="a95e0-103">Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a95e0-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="a95e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a95e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a95e0-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a95e0-105">\<bindings></span></span>  
<span data-ttu-id="a95e0-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="a95e0-106">\<netTcpBinding></span></span>  
<span data-ttu-id="a95e0-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="a95e0-107">\<binding></span></span>  
<span data-ttu-id="a95e0-108">\<security></span><span class="sxs-lookup"><span data-stu-id="a95e0-108">\<security></span></span>  
<span data-ttu-id="a95e0-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a95e0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95e0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a95e0-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a95e0-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a95e0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a95e0-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a95e0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a95e0-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a95e0-113">Attributes</span></span>  
  
|<span data-ttu-id="a95e0-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a95e0-114">Attribute</span></span>|<span data-ttu-id="a95e0-115">Description</span><span class="sxs-lookup"><span data-stu-id="a95e0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a95e0-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a95e0-116">clientCredentialType</span></span>|<span data-ttu-id="a95e0-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a95e0-117">Optional.</span></span> <span data-ttu-id="a95e0-118">Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="a95e0-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="a95e0-119">-La valeur par défaut est `Windows`.</span><span class="sxs-lookup"><span data-stu-id="a95e0-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="a95e0-120">-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a95e0-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="a95e0-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a95e0-121">protectionLevel</span></span>|<span data-ttu-id="a95e0-122">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a95e0-122">Optional.</span></span> <span data-ttu-id="a95e0-123">Définit la sécurité au niveau du transport TCP.</span><span class="sxs-lookup"><span data-stu-id="a95e0-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="a95e0-124">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="a95e0-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a95e0-125">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="a95e0-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="a95e0-126">La valeur par défaut est `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="a95e0-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="a95e0-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="a95e0-127">sslProtocols</span></span>|<span data-ttu-id="a95e0-128">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a95e0-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="a95e0-129">La valeur par défaut est Tls &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="a95e0-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="a95e0-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="a95e0-130">policyEnforcement</span></span>|<span data-ttu-id="a95e0-131">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="a95e0-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a95e0-132">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="a95e0-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a95e0-133">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="a95e0-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a95e0-134">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="a95e0-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a95e0-135">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="a95e0-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a95e0-136">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a95e0-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a95e0-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="a95e0-137">Value</span></span>|<span data-ttu-id="a95e0-138">Description</span><span class="sxs-lookup"><span data-stu-id="a95e0-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a95e0-139">None</span><span class="sxs-lookup"><span data-stu-id="a95e0-139">None</span></span>|<span data-ttu-id="a95e0-140">Le client est anonyme.</span><span class="sxs-lookup"><span data-stu-id="a95e0-140">The client is anonymous.</span></span> <span data-ttu-id="a95e0-141">Cela requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="a95e0-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="a95e0-142">Windows</span><span class="sxs-lookup"><span data-stu-id="a95e0-142">Windows</span></span>|<span data-ttu-id="a95e0-143">Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).</span><span class="sxs-lookup"><span data-stu-id="a95e0-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="a95e0-144">Certificat</span><span class="sxs-lookup"><span data-stu-id="a95e0-144">Certificate</span></span>|<span data-ttu-id="a95e0-145">Le client est authentifié à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="a95e0-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="a95e0-146">Cette valeur utilise la négociation SSL et requiert un certificat pour le service.</span><span class="sxs-lookup"><span data-stu-id="a95e0-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="a95e0-147">protectionLevel, attribut</span><span class="sxs-lookup"><span data-stu-id="a95e0-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="a95e0-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="a95e0-148">Value</span></span>|<span data-ttu-id="a95e0-149">Description</span><span class="sxs-lookup"><span data-stu-id="a95e0-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a95e0-150">None</span><span class="sxs-lookup"><span data-stu-id="a95e0-150">None</span></span>|<span data-ttu-id="a95e0-151">Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="a95e0-151">No protection.</span></span>|  
|<span data-ttu-id="a95e0-152">Sign</span><span class="sxs-lookup"><span data-stu-id="a95e0-152">Sign</span></span>|<span data-ttu-id="a95e0-153">Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="a95e0-153">Messages are signed.</span></span>|  
|<span data-ttu-id="a95e0-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="a95e0-154">EncryptAndSign</span></span>|<span data-ttu-id="a95e0-155">-Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="a95e0-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a95e0-156">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a95e0-156">Child Elements</span></span>  
 <span data-ttu-id="a95e0-157">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a95e0-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a95e0-158">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a95e0-158">Parent Elements</span></span>  
  
|<span data-ttu-id="a95e0-159">Élément</span><span class="sxs-lookup"><span data-stu-id="a95e0-159">Element</span></span>|<span data-ttu-id="a95e0-160">Description</span><span class="sxs-lookup"><span data-stu-id="a95e0-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a95e0-161">\<security></span><span class="sxs-lookup"><span data-stu-id="a95e0-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="a95e0-162">Spécifie les fonctions de sécurité de le [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a95e0-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a95e0-163">Notes</span><span class="sxs-lookup"><span data-stu-id="a95e0-163">Remarks</span></span>  
 <span data-ttu-id="a95e0-164">Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle.</span><span class="sxs-lookup"><span data-stu-id="a95e0-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="a95e0-165">Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l’aide d’un transport sécurisé et les messages SOAP sont sécurisés à l’aide d’une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.</span><span class="sxs-lookup"><span data-stu-id="a95e0-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95e0-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a95e0-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="a95e0-167">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a95e0-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a95e0-168">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a95e0-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a95e0-169">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a95e0-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a95e0-170">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a95e0-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a95e0-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="a95e0-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
