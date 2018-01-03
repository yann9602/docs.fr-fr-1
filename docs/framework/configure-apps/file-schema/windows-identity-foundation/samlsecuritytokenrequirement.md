---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a642a79618329a55afa98dba04e4ac5f419cae7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="b1126-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="b1126-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="b1126-103">Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> (classe), la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée d’un de ces classes.</span><span class="sxs-lookup"><span data-stu-id="b1126-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="b1126-104">Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="b1126-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="b1126-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b1126-105">\<system.identityModel></span></span>  
<span data-ttu-id="b1126-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b1126-106">\<identityConfiguration></span></span>  
<span data-ttu-id="b1126-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b1126-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b1126-108">\<add></span><span class="sxs-lookup"><span data-stu-id="b1126-108">\<add></span></span>  
<span data-ttu-id="b1126-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b1126-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1126-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1126-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1126-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1126-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b1126-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1126-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1126-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1126-113">Attributes</span></span>  
  
|<span data-ttu-id="b1126-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1126-114">Attribute</span></span>|<span data-ttu-id="b1126-115">Description</span><span class="sxs-lookup"><span data-stu-id="b1126-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1126-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="b1126-116">mapToWindows</span></span>|<span data-ttu-id="b1126-117">Spécifie si le Gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="b1126-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="b1126-118">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="b1126-118">The default is "false".</span></span>|  
|<span data-ttu-id="b1126-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="b1126-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="b1126-120">Un <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b1126-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1126-121">La valeur par défaut est « Online ».</span><span class="sxs-lookup"><span data-stu-id="b1126-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="b1126-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b1126-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="b1126-123">Un <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b1126-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1126-124">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="b1126-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="b1126-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b1126-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="b1126-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="b1126-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b1126-127">La valeur par défaut est « Ordinateur_local ».</span><span class="sxs-lookup"><span data-stu-id="b1126-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="b1126-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="b1126-128">issuerCertificateValidator</span></span>|<span data-ttu-id="b1126-129">Un type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="b1126-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="b1126-130">Si le `issuerCertificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation de certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="b1126-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1126-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1126-131">Child Elements</span></span>  
  
|<span data-ttu-id="b1126-132">Élément</span><span class="sxs-lookup"><span data-stu-id="b1126-132">Element</span></span>|<span data-ttu-id="b1126-133">Description</span><span class="sxs-lookup"><span data-stu-id="b1126-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1126-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="b1126-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="b1126-135">Définit le type de revendication qui spécifie le <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b1126-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="b1126-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="b1126-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="b1126-137">Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection de <xref:System.Security.Claims.ClaimsIdentity> objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du Gestionnaire de jeton.</span><span class="sxs-lookup"><span data-stu-id="b1126-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1126-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1126-138">Parent Elements</span></span>  
  
|<span data-ttu-id="b1126-139">Élément</span><span class="sxs-lookup"><span data-stu-id="b1126-139">Element</span></span>|<span data-ttu-id="b1126-140">Description</span><span class="sxs-lookup"><span data-stu-id="b1126-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1126-141">\<add></span><span class="sxs-lookup"><span data-stu-id="b1126-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b1126-142">Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b1126-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1126-143">Notes</span><span class="sxs-lookup"><span data-stu-id="b1126-143">Remarks</span></span>  
 <span data-ttu-id="b1126-144">Le `<samlSecurityTokenRequirement>` élément est représenté par le <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> dans le modèle objet de classe et est utilisé pour configurer le `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="b1126-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1126-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1126-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
