---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: be98c93452c9c7a37ecad5b03f5160ea08f2c82e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="a1bc8-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="a1bc8-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="a1bc8-103">Fournit la configuration de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="a1bc8-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-104">\<system.identityModel></span></span>  
<span data-ttu-id="a1bc8-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a1bc8-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a1bc8-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1bc8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1bc8-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1bc8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a1bc8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a1bc8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1bc8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a1bc8-111">Attributes</span></span>  
  
|<span data-ttu-id="a1bc8-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a1bc8-112">Attribute</span></span>|<span data-ttu-id="a1bc8-113">Description</span><span class="sxs-lookup"><span data-stu-id="a1bc8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1bc8-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="a1bc8-114">saveBootstrapContext</span></span>|<span data-ttu-id="a1bc8-115">Spécifie si les jetons d’amorçage doivent être inclus dans le jeton de session.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="a1bc8-116">La valeur peut également être définie sur une collection de gestionnaire de jetons en définissant le `saveBootstrapContext` de l’attribut le [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="a1bc8-117">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="a1bc8-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="a1bc8-118">maximumClockSkew</span></span>|<span data-ttu-id="a1bc8-119">Un <xref:System.TimeSpan> qui spécifie l’inclinaison d’horloge maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="a1bc8-120">Contrôle l’inclinaison d’horloge maximale autorisée lorsque vous effectuez des opérations sensibles, telles que la validation de l’heure d’expiration d’une session de connexion.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="a1bc8-121">La valeur par défaut est 5 minutes, « 00 : 05:00 ».</span><span class="sxs-lookup"><span data-stu-id="a1bc8-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="a1bc8-122">Pour plus d’informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, consultez [valeurs Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1bc8-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="a1bc8-123">L’inclinaison d’horloge maximale peut également être définie au niveau du service en définissant le `maximumClockSkew` de l’attribut le [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="a1bc8-124">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1bc8-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a1bc8-125">Child Elements</span></span>  
  
|<span data-ttu-id="a1bc8-126">Élément</span><span class="sxs-lookup"><span data-stu-id="a1bc8-126">Element</span></span>|<span data-ttu-id="a1bc8-127">Description</span><span class="sxs-lookup"><span data-stu-id="a1bc8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1bc8-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="a1bc8-129">Spécifie le jeu d’URI qui sont des identificateurs acceptables de cette partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="a1bc8-130">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-130">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-131">\<met en cache ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="a1bc8-132">Inscrit le met en cache utilisés pour les jetons de session et de la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="a1bc8-133">Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a1bc8-134">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-134">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="a1bc8-136">Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="a1bc8-137">Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a1bc8-138">Ces paramètres sont remplacés si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="a1bc8-139">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-139">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="a1bc8-141">Configure le Registre de nom de l’émetteur qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a1bc8-142">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-142">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="a1bc8-144">Inscrit le résolveur de jeton de l’émetteur qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a1bc8-145">Le programme de résolution de jeton de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrant.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="a1bc8-146">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-146">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="a1bc8-148">Inscrit le résolveur de jeton de service qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a1bc8-149">Le programme de résolution de jeton de service permet de résoudre le jeton de chiffrement sur les jetons et les messages entrant.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="a1bc8-150">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-150">Optional.</span></span>|  
|[<span data-ttu-id="a1bc8-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="a1bc8-152">Active la détection de relecture de jetons et spécifie le délai d’expiration pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="a1bc8-153">Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a1bc8-154">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1bc8-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a1bc8-155">Parent Elements</span></span>  
  
|<span data-ttu-id="a1bc8-156">Élément</span><span class="sxs-lookup"><span data-stu-id="a1bc8-156">Element</span></span>|<span data-ttu-id="a1bc8-157">Description</span><span class="sxs-lookup"><span data-stu-id="a1bc8-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1bc8-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="a1bc8-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="a1bc8-159">Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1bc8-160">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1bc8-160">Remarks</span></span>  
 <span data-ttu-id="a1bc8-161">Cette section fournit des valeurs de propriété d’un <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objet.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="a1bc8-162">Les paramètres configurés dans cette section remplacent ceux configurés sur le service.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="a1bc8-163">Certains de ces paramètres peuvent, à son tour, être remplacée par les paramètres spécifiés quand un gestionnaire est ajouté à la collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a1bc8-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1bc8-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1bc8-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
