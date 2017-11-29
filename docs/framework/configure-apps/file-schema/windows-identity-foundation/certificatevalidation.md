---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 778088f2e0508f5a80c29ae027b2442a80286795
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="8fc9a-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="8fc9a-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="8fc9a-103">Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="8fc9a-104">Ces paramètres sont remplacés si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="8fc9a-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-105">\<system.identityModel></span></span>  
<span data-ttu-id="8fc9a-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-106">\<identityConfiguration></span></span>  
<span data-ttu-id="8fc9a-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc9a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc9a-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fc9a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8fc9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8fc9a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fc9a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8fc9a-111">Attributes</span></span>  
  
|<span data-ttu-id="8fc9a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="8fc9a-112">Attribute</span></span>|<span data-ttu-id="8fc9a-113">Description</span><span class="sxs-lookup"><span data-stu-id="8fc9a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fc9a-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="8fc9a-114">certificateValidationMode</span></span>|<span data-ttu-id="8fc9a-115">Un <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="8fc9a-116">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="8fc9a-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="8fc9a-117">Pour spécifier un validateur personnalisé, définissez cet attribut à « Custom » et le programme de validation à l’aide de la [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) élément.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="8fc9a-118">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-118">Optional.</span></span>|  
|<span data-ttu-id="8fc9a-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="8fc9a-119">revocationMode</span></span>|<span data-ttu-id="8fc9a-120">Un <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="8fc9a-121">La valeur par défaut est « Online ».</span><span class="sxs-lookup"><span data-stu-id="8fc9a-121">The default value is "Online".</span></span> <span data-ttu-id="8fc9a-122">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-122">Optional.</span></span>|  
|<span data-ttu-id="8fc9a-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="8fc9a-123">trustedStoreLocation</span></span>|<span data-ttu-id="8fc9a-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="8fc9a-125">La valeur par défaut est « Ordinateur_local ».</span><span class="sxs-lookup"><span data-stu-id="8fc9a-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="8fc9a-126">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fc9a-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8fc9a-127">Child Elements</span></span>  
  
|<span data-ttu-id="8fc9a-128">Élément</span><span class="sxs-lookup"><span data-stu-id="8fc9a-128">Element</span></span>|<span data-ttu-id="8fc9a-129">Description</span><span class="sxs-lookup"><span data-stu-id="8fc9a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fc9a-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="8fc9a-131">Spécifie un type personnalisé pour la validation de certificat.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="8fc9a-132">Ce type est utilisé uniquement si la `certificateValidationMode` attribut de la [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="8fc9a-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fc9a-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8fc9a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="8fc9a-134">Élément</span><span class="sxs-lookup"><span data-stu-id="8fc9a-134">Element</span></span>|<span data-ttu-id="8fc9a-135">Description</span><span class="sxs-lookup"><span data-stu-id="8fc9a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fc9a-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="8fc9a-137">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8fc9a-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8fc9a-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="8fc9a-139">Fournit des gestionnaires de jetons de configuration pour une collection de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fc9a-140">Remarques</span><span class="sxs-lookup"><span data-stu-id="8fc9a-140">Remarks</span></span>  
 <span data-ttu-id="8fc9a-141">A `<certificateValidation>` élément peut être spécifié au niveau du service sous le `<identityConfiguration>` élément ou sur le niveau de regroupement de gestionnaire de jetons de sécurité sous le `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8fc9a-142">Paramètres sur une collection de gestionnaire de jetons remplacent celles spécifiées sur le service.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="8fc9a-143">Certains gestionnaires de jetons permettent de spécifier les paramètres de validation de certificat dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="8fc9a-144">Paramètres sur les gestionnaires de jetons individuels remplacent celles spécifiées à la fois au niveau du service et sur la collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8fc9a-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc9a-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="8fc9a-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
