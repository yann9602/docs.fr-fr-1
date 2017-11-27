---
title: '&lt;security&gt; of &lt;netHttpBinding'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63d65ea50babd0cd4aa7ee92cdd6d2b281dcbc26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="72fde-102">&lt;security&gt; of &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="72fde-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="72fde-103">Définit les fonctionnalités de sécurité le [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72fde-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="72fde-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="72fde-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72fde-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="72fde-105">\<bindings></span></span>  
<span data-ttu-id="72fde-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="72fde-106">\<netHttpBinding></span></span>  
<span data-ttu-id="72fde-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="72fde-107">\<binding></span></span>  
<span data-ttu-id="72fde-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="72fde-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fde-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72fde-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72fde-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="72fde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="72fde-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="72fde-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72fde-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="72fde-112">Attributes</span></span>  
  
|<span data-ttu-id="72fde-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="72fde-113">Attribute</span></span>|<span data-ttu-id="72fde-114">Description</span><span class="sxs-lookup"><span data-stu-id="72fde-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72fde-115">mode</span><span class="sxs-lookup"><span data-stu-id="72fde-115">mode</span></span>|<span data-ttu-id="72fde-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="72fde-116">Optional.</span></span> <span data-ttu-id="72fde-117">Spécifie le type de sécurité qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="72fde-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="72fde-118">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="72fde-118">The default is `None`.</span></span> <span data-ttu-id="72fde-119">Cet attribut est de type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="72fde-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="72fde-120">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="72fde-120">mode Attribute</span></span>  
  
|<span data-ttu-id="72fde-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="72fde-121">Value</span></span>|<span data-ttu-id="72fde-122">Description</span><span class="sxs-lookup"><span data-stu-id="72fde-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72fde-123">Aucune</span><span class="sxs-lookup"><span data-stu-id="72fde-123">None</span></span>|<span data-ttu-id="72fde-124">-Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="72fde-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="72fde-125">Transport</span><span class="sxs-lookup"><span data-stu-id="72fde-125">Transport</span></span>|<span data-ttu-id="72fde-126">La sécurité est fournie à l'aide du transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="72fde-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="72fde-127">Les messages SOAP sont sécurisés par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="72fde-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="72fde-128">Le service est authentifié auprès du client à l'aide du certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="72fde-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="72fde-129">Le client est authentifié à l'aide du ClientCredentialType fourni.</span><span class="sxs-lookup"><span data-stu-id="72fde-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="72fde-130">Message</span><span class="sxs-lookup"><span data-stu-id="72fde-130">Message</span></span>|<span data-ttu-id="72fde-131">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="72fde-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="72fde-132">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="72fde-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="72fde-133">Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.</span><span class="sxs-lookup"><span data-stu-id="72fde-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="72fde-134">Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="72fde-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="72fde-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="72fde-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="72fde-136">L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="72fde-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="72fde-137">L'authentification du client est fournie au moyen de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="72fde-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="72fde-138">Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.</span><span class="sxs-lookup"><span data-stu-id="72fde-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="72fde-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="72fde-139">TransportCredentialOnly</span></span>|<span data-ttu-id="72fde-140">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="72fde-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="72fde-141">Il fournit l'authentification du client basée sur http.</span><span class="sxs-lookup"><span data-stu-id="72fde-141">It provides http-based client authentication.</span></span> <span data-ttu-id="72fde-142">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="72fde-142">This mode should be used with caution.</span></span> <span data-ttu-id="72fde-143">Il doit être utilisé dans les environnements où la sécurité de transport est fournie par d'autres moyens (tels que IPSec) et où seule l'authentification du client est fournie par l'infrastructure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72fde-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72fde-144">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="72fde-144">Child Elements</span></span>  
  
|<span data-ttu-id="72fde-145">Élément</span><span class="sxs-lookup"><span data-stu-id="72fde-145">Element</span></span>|<span data-ttu-id="72fde-146">Description</span><span class="sxs-lookup"><span data-stu-id="72fde-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72fde-147">\<transport ></span><span class="sxs-lookup"><span data-stu-id="72fde-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="72fde-148">Définit les paramètres de sécurité de transport pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="72fde-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="72fde-149">Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="72fde-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="72fde-150">\<message ></span><span class="sxs-lookup"><span data-stu-id="72fde-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="72fde-151">Définit les paramètres de sécurité de message pour un service HTTP de base.</span><span class="sxs-lookup"><span data-stu-id="72fde-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="72fde-152">Cet élément correspond à <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="72fde-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72fde-153">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="72fde-153">Parent Elements</span></span>  
  
|<span data-ttu-id="72fde-154">Élément</span><span class="sxs-lookup"><span data-stu-id="72fde-154">Element</span></span>|<span data-ttu-id="72fde-155">Description</span><span class="sxs-lookup"><span data-stu-id="72fde-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72fde-156">liaison</span><span class="sxs-lookup"><span data-stu-id="72fde-156">binding</span></span>|<span data-ttu-id="72fde-157">L’élément de liaison de la [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="72fde-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72fde-158">Remarques</span><span class="sxs-lookup"><span data-stu-id="72fde-158">Remarks</span></span>  
 <span data-ttu-id="72fde-159">Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="72fde-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="72fde-160">Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `netHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="72fde-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fde-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72fde-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="72fde-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="72fde-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="72fde-163">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="72fde-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="72fde-164">Sélection d’un Type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="72fde-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="72fde-165">Liaisons</span><span class="sxs-lookup"><span data-stu-id="72fde-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72fde-166">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="72fde-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="72fde-167">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="72fde-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="72fde-168">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="72fde-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
