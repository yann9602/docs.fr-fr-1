---
title: "&lt;authentication&gt;, élément de &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb2f567b47f66b378cc6e0a5d5e96441ea65c1ac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="38151-102">&lt;authentication&gt;, élément de &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="38151-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="38151-103">Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="38151-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="38151-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38151-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38151-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="38151-105">\<behaviors></span></span>  
<span data-ttu-id="38151-106">section d’endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="38151-106">endpointBehaviors section</span></span>  
<span data-ttu-id="38151-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="38151-107">\<behavior></span></span>  
<span data-ttu-id="38151-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="38151-108">\<clientCredentials></span></span>  
<span data-ttu-id="38151-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="38151-109">\<serviceCertificate></span></span>  
<span data-ttu-id="38151-110">\<authentification ></span><span class="sxs-lookup"><span data-stu-id="38151-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38151-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38151-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38151-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38151-112">Attributes and Elements</span></span>  
 <span data-ttu-id="38151-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38151-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38151-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="38151-114">Attributes</span></span>  
  
|<span data-ttu-id="38151-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="38151-115">Attribute</span></span>|<span data-ttu-id="38151-116">Description</span><span class="sxs-lookup"><span data-stu-id="38151-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38151-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="38151-117">customCertificateValidatorType</span></span>|<span data-ttu-id="38151-118">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="38151-118">String.</span></span> <span data-ttu-id="38151-119">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="38151-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="38151-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="38151-120">certificateValidationMode</span></span>|<span data-ttu-id="38151-121">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="38151-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="38151-122">S'il est défini à `Custom`, un customCertificateValidator doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="38151-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="38151-123">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="38151-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="38151-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="38151-124">revocationMode</span></span>|<span data-ttu-id="38151-125">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="38151-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="38151-126">La valeur par défaut est `Online`.</span><span class="sxs-lookup"><span data-stu-id="38151-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="38151-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="38151-127">trustedStoreLocation</span></span>|<span data-ttu-id="38151-128">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38151-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="38151-129">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="38151-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="38151-130">La validation est exécutée sur le **personnes** stocker dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="38151-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="38151-131">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="38151-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="38151-132">customCertificateValidator, attribut</span><span class="sxs-lookup"><span data-stu-id="38151-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="38151-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="38151-133">Value</span></span>|<span data-ttu-id="38151-134">Description</span><span class="sxs-lookup"><span data-stu-id="38151-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38151-135">Chaîne</span><span class="sxs-lookup"><span data-stu-id="38151-135">String</span></span>|<span data-ttu-id="38151-136">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="38151-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="38151-137">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="38151-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="38151-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="38151-138">Value</span></span>|<span data-ttu-id="38151-139">Description</span><span class="sxs-lookup"><span data-stu-id="38151-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38151-140">Énumération</span><span class="sxs-lookup"><span data-stu-id="38151-140">Enumeration</span></span>|<span data-ttu-id="38151-141">Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="38151-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="38151-142">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="38151-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="38151-143">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="38151-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="38151-144">Valeur</span><span class="sxs-lookup"><span data-stu-id="38151-144">Value</span></span>|<span data-ttu-id="38151-145">Description</span><span class="sxs-lookup"><span data-stu-id="38151-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38151-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="38151-146">Enumeration</span></span>|<span data-ttu-id="38151-147">Une des valeurs suivantes : NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="38151-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="38151-148">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="38151-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="38151-149">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="38151-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="38151-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="38151-150">Value</span></span>|<span data-ttu-id="38151-151">Description</span><span class="sxs-lookup"><span data-stu-id="38151-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38151-152">Énumération</span><span class="sxs-lookup"><span data-stu-id="38151-152">Enumeration</span></span>|<span data-ttu-id="38151-153">Une des valeurs suivantes : LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="38151-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="38151-154">La valeur par défaut est CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="38151-154">The default is CurrentUser.</span></span> <span data-ttu-id="38151-155">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="38151-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="38151-156">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="38151-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38151-157">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38151-157">Child Elements</span></span>  
 <span data-ttu-id="38151-158">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38151-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38151-159">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38151-159">Parent Elements</span></span>  
  
|<span data-ttu-id="38151-160">Élément</span><span class="sxs-lookup"><span data-stu-id="38151-160">Element</span></span>|<span data-ttu-id="38151-161">Description</span><span class="sxs-lookup"><span data-stu-id="38151-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38151-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="38151-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="38151-163">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="38151-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38151-164">Remarques</span><span class="sxs-lookup"><span data-stu-id="38151-164">Remarks</span></span>  
 <span data-ttu-id="38151-165">L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats.</span><span class="sxs-lookup"><span data-stu-id="38151-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="38151-166">Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="38151-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="38151-167">C'est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="38151-167">This is the most secure mode.</span></span> <span data-ttu-id="38151-168">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="38151-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="38151-169">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="38151-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="38151-170">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="38151-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="38151-171">Vous pouvez également affecter la valeur `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="38151-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="38151-172">Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat.</span><span class="sxs-lookup"><span data-stu-id="38151-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="38151-173">Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite.</span><span class="sxs-lookup"><span data-stu-id="38151-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="38151-174">Pour plus d’informations, consultez [Comment : créer un Service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="38151-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="38151-175">L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer.</span><span class="sxs-lookup"><span data-stu-id="38151-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="38151-176">La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation.</span><span class="sxs-lookup"><span data-stu-id="38151-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="38151-177">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="38151-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38151-178">Exemple</span><span class="sxs-lookup"><span data-stu-id="38151-178">Example</span></span>  
 <span data-ttu-id="38151-179">Dans l’exemple suivant, deux tâches sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="38151-179">The following example does two tasks.</span></span> <span data-ttu-id="38151-180">Premièrement, un certificat de service est spécifié, que le client utilise au cours de communications avec les points de terminaison dont le nom de domaine est www.contoso.com sur le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="38151-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is www.contoso.com over the HTTP protocol.</span></span> <span data-ttu-id="38151-181">Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.</span><span class="sxs-lookup"><span data-stu-id="38151-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38151-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38151-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="38151-183">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="38151-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="38151-184">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="38151-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="38151-185">Comment : créer un Service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="38151-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="38151-186">\<authentification ></span><span class="sxs-lookup"><span data-stu-id="38151-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="38151-187">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="38151-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="38151-188">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="38151-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
