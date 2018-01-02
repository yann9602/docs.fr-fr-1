---
title: '&lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1007abbb91787ed7be4fe3a7f8c1b0173191d60e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="73404-102">&lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="73404-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="73404-103">Indique un jeton personnalisé émis en tant qu'informations d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="73404-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="73404-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73404-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73404-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="73404-105">\<behaviors></span></span>  
<span data-ttu-id="73404-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="73404-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="73404-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="73404-107">\<behavior></span></span>  
<span data-ttu-id="73404-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="73404-108">\<serviceCredentials></span></span>  
<span data-ttu-id="73404-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="73404-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73404-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73404-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73404-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="73404-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73404-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="73404-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73404-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="73404-113">Attributes</span></span>  
  
|<span data-ttu-id="73404-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="73404-114">Attribute</span></span>|<span data-ttu-id="73404-115">Description</span><span class="sxs-lookup"><span data-stu-id="73404-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="73404-116">Obtient le jeu d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="73404-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="73404-117">Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="73404-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="73404-118">Valeur booléenne indiquant si les émetteurs de certificats RSA non fiables sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="73404-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="73404-119">Les certificats sont signés par des autorités de certification (CA) pour en assurer l'authenticité.</span><span class="sxs-lookup"><span data-stu-id="73404-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="73404-120">Un émetteur non fiable est une autorité de certification qui n'est pas spécifiée comme étant approuvée pour signer des certificats.</span><span class="sxs-lookup"><span data-stu-id="73404-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="73404-121">Obtient une valeur indiquant si le <xref:System.IdentityModel.Tokens.SamlSecurityToken> du jeton de sécurité <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> doit être validé.</span><span class="sxs-lookup"><span data-stu-id="73404-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="73404-122">Cette valeur est de type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="73404-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="73404-123">Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="73404-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="73404-124">Définit le mode de validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="73404-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="73404-125">L'une des valeurs valides du <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="73404-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="73404-126">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="73404-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="73404-127">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="73404-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="73404-128">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="73404-128">Optional string.</span></span> <span data-ttu-id="73404-129">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="73404-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="73404-130">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="73404-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="73404-131">Définit le mode de révocation qui spécifie si un contrôle de révocation a lieu et s'il est effectué en ligne ou hors connexion.</span><span class="sxs-lookup"><span data-stu-id="73404-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="73404-132">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="73404-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="73404-133">Attribut de chaîne facultatif indiquant le type de SamlSerializer utilisé pour les informations d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="73404-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="73404-134">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="73404-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="73404-135">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="73404-135">Optional enumeration.</span></span> <span data-ttu-id="73404-136">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="73404-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73404-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="73404-137">Child Elements</span></span>  
  
|<span data-ttu-id="73404-138">Élément</span><span class="sxs-lookup"><span data-stu-id="73404-138">Element</span></span>|<span data-ttu-id="73404-139">Description</span><span class="sxs-lookup"><span data-stu-id="73404-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="73404-140">Indique une collection d'éléments <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> qui spécifient des émetteurs approuvés au niveau des informations d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="73404-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73404-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="73404-141">Parent Elements</span></span>  
  
|<span data-ttu-id="73404-142">Élément</span><span class="sxs-lookup"><span data-stu-id="73404-142">Element</span></span>|<span data-ttu-id="73404-143">Description</span><span class="sxs-lookup"><span data-stu-id="73404-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73404-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="73404-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="73404-145">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="73404-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73404-146">Notes</span><span class="sxs-lookup"><span data-stu-id="73404-146">Remarks</span></span>  
 <span data-ttu-id="73404-147">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="73404-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="73404-148">Dans la première phase, un client tente d’accéder à un service est appelée un *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="73404-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="73404-149">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="73404-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="73404-150">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="73404-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="73404-151">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="73404-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="73404-152">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="73404-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="73404-153">Cet élément est le référentiel pour les certificats de service d'émission de jeton sécurisé de ce type.</span><span class="sxs-lookup"><span data-stu-id="73404-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="73404-154">Pour ajouter des certificats, utilisez le [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="73404-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="73404-155">Insérer un [ \<Ajouter >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="73404-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="73404-156">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="73404-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="73404-157">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="73404-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="73404-158">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer les informations d’identification sur un Service de fédération](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="73404-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73404-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73404-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="73404-160">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="73404-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="73404-161">Guide pratique pour configurer des informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="73404-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
