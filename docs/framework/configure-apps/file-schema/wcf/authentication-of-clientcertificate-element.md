---
title: "Élément &lt;authentication&gt;, de &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bebbc8b5cc315e92645cbbf0321de53122c7b1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="7018e-102">Élément &lt;authentication&gt;, de &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="7018e-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="7018e-103">Spécifie les comportements d'authentification des certificats clients utilisés par un service.</span><span class="sxs-lookup"><span data-stu-id="7018e-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="7018e-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7018e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7018e-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="7018e-105">\<behaviors></span></span>  
<span data-ttu-id="7018e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7018e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7018e-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="7018e-107">\<behavior></span></span>  
<span data-ttu-id="7018e-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7018e-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7018e-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="7018e-109">\<clientCertificate></span></span>  
<span data-ttu-id="7018e-110">\<authentification ></span><span class="sxs-lookup"><span data-stu-id="7018e-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7018e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7018e-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7018e-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7018e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7018e-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7018e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7018e-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="7018e-114">Attributes</span></span>  
  
|<span data-ttu-id="7018e-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="7018e-115">Attribute</span></span>|<span data-ttu-id="7018e-116">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7018e-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="7018e-117">customCertificateValidatorType</span></span>|<span data-ttu-id="7018e-118">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="7018e-118">Optional string.</span></span> <span data-ttu-id="7018e-119">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7018e-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7018e-120">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7018e-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="7018e-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7018e-121">certificateValidationMode</span></span>|<span data-ttu-id="7018e-122">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="7018e-122">Optional enumeration.</span></span> <span data-ttu-id="7018e-123">Spécifie l'un des modes utilisés pour valider les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="7018e-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="7018e-124">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="7018e-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="7018e-125">S'il est défini à <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="7018e-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="7018e-126">La valeur par défaut est <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7018e-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="7018e-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="7018e-127">includeWindowsGroups</span></span>|<span data-ttu-id="7018e-128">Valeur booléenne facultative.</span><span class="sxs-lookup"><span data-stu-id="7018e-128">Optional Boolean.</span></span> <span data-ttu-id="7018e-129">Spécifie si des groupes Windows sont inclus dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7018e-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="7018e-130">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait que cela provoque une expansion de groupe complète.</span><span class="sxs-lookup"><span data-stu-id="7018e-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="7018e-131">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7018e-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="7018e-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="7018e-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="7018e-133">Propriété booléenne.</span><span class="sxs-lookup"><span data-stu-id="7018e-133">Boolean.</span></span> <span data-ttu-id="7018e-134">Spécifie si le client peut être mappé à une identité Windows à l'aide du certificat.</span><span class="sxs-lookup"><span data-stu-id="7018e-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="7018e-135">Active Directory doit être activé pour cela.</span><span class="sxs-lookup"><span data-stu-id="7018e-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="7018e-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7018e-136">revocationMode</span></span>|<span data-ttu-id="7018e-137">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="7018e-137">Optional enumeration.</span></span> <span data-ttu-id="7018e-138">Un des modes utilisés pour vérifier des listes de certificats révoqués (RCL).</span><span class="sxs-lookup"><span data-stu-id="7018e-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="7018e-139">La valeur par défaut est `Online`.</span><span class="sxs-lookup"><span data-stu-id="7018e-139">The default is `Online`.</span></span> <span data-ttu-id="7018e-140">Cette valeur est ignorée lors de l'utilisation de la sécurité de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="7018e-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="7018e-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7018e-141">trustedStoreLocation</span></span>|<span data-ttu-id="7018e-142">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="7018e-142">Optional enumeration.</span></span> <span data-ttu-id="7018e-143">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7018e-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7018e-144">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="7018e-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7018e-145">La validation est exécutée sur le **personnes** stocker dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="7018e-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="7018e-146">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7018e-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="7018e-147">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="7018e-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="7018e-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="7018e-148">Value</span></span>|<span data-ttu-id="7018e-149">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7018e-150">Chaîne</span><span class="sxs-lookup"><span data-stu-id="7018e-150">String</span></span>|<span data-ttu-id="7018e-151">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="7018e-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7018e-152">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="7018e-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7018e-153">Valeur</span><span class="sxs-lookup"><span data-stu-id="7018e-153">Value</span></span>|<span data-ttu-id="7018e-154">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7018e-155">Énumération</span><span class="sxs-lookup"><span data-stu-id="7018e-155">Enumeration</span></span>|<span data-ttu-id="7018e-156">Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="7018e-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="7018e-157">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7018e-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7018e-158">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="7018e-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7018e-159">Valeur</span><span class="sxs-lookup"><span data-stu-id="7018e-159">Value</span></span>|<span data-ttu-id="7018e-160">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7018e-161">Énumération</span><span class="sxs-lookup"><span data-stu-id="7018e-161">Enumeration</span></span>|<span data-ttu-id="7018e-162">Une des valeurs suivantes : NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="7018e-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="7018e-163">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7018e-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7018e-164">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="7018e-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7018e-165">Valeur</span><span class="sxs-lookup"><span data-stu-id="7018e-165">Value</span></span>|<span data-ttu-id="7018e-166">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7018e-167">Énumération</span><span class="sxs-lookup"><span data-stu-id="7018e-167">Enumeration</span></span>|<span data-ttu-id="7018e-168">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7018e-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7018e-169">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7018e-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="7018e-170">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="7018e-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="7018e-171">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7018e-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7018e-172">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7018e-172">Child Elements</span></span>  
 <span data-ttu-id="7018e-173">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7018e-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7018e-174">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7018e-174">Parent Elements</span></span>  
  
|<span data-ttu-id="7018e-175">Élément</span><span class="sxs-lookup"><span data-stu-id="7018e-175">Element</span></span>|<span data-ttu-id="7018e-176">Description</span><span class="sxs-lookup"><span data-stu-id="7018e-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7018e-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="7018e-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="7018e-178">Définit un certificat X.509 utilisé pour authentifier un client à un service.</span><span class="sxs-lookup"><span data-stu-id="7018e-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7018e-179">Remarques</span><span class="sxs-lookup"><span data-stu-id="7018e-179">Remarks</span></span>  
 <span data-ttu-id="7018e-180">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="7018e-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="7018e-181">Il vous permet de personnaliser la manière dont les clients sont authentifiés.</span><span class="sxs-lookup"><span data-stu-id="7018e-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="7018e-182">Vous pouvez affecter `certificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7018e-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="7018e-183">Par défaut, le niveau est défini sur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant par un *autorité racine* en haut de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="7018e-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="7018e-184">C’est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="7018e-184">This is the most secure mode.</span></span> <span data-ttu-id="7018e-185">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="7018e-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="7018e-186">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="7018e-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="7018e-187">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7018e-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="7018e-188">Vous pouvez également utiliser `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7018e-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="7018e-189">Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `customCertificateValidatorType`.</span><span class="sxs-lookup"><span data-stu-id="7018e-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="7018e-190">Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.</span><span class="sxs-lookup"><span data-stu-id="7018e-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="7018e-191">Pour plus d’informations, consultez [Comment : créer un Service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="7018e-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7018e-192">Exemple</span><span class="sxs-lookup"><span data-stu-id="7018e-192">Example</span></span>  
 <span data-ttu-id="7018e-193">Le code suivant spécifie un certificat X.509 et un type de validation personnalisé dans l'élément `<authentication>`.</span><span class="sxs-lookup"><span data-stu-id="7018e-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7018e-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7018e-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="7018e-195">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="7018e-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7018e-196">Comment : créer un Service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="7018e-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="7018e-197">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="7018e-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
