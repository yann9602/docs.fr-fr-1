---
title: '&lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fdb110302de05fd7dac3c318b8cd4bf83c0155b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="ac159-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ac159-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="ac159-103">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="ac159-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="ac159-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ac159-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ac159-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="ac159-105">\<bindings></span></span>  
<span data-ttu-id="ac159-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ac159-106">\<customBinding></span></span>  
<span data-ttu-id="ac159-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="ac159-107">\<binding></span></span>  
<span data-ttu-id="ac159-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="ac159-108">\<security></span></span>  
<span data-ttu-id="ac159-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ac159-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac159-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac159-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="ac159-111">Type</span><span class="sxs-lookup"><span data-stu-id="ac159-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac159-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac159-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ac159-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ac159-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac159-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac159-114">Attributes</span></span>  
  
|<span data-ttu-id="ac159-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac159-115">Attribute</span></span>|<span data-ttu-id="ac159-116">Description</span><span class="sxs-lookup"><span data-stu-id="ac159-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac159-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ac159-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="ac159-118">Spécifie les versions des caractéristiques de sécurité (WS-Security, WS-Trust, WS-Secure Conversation et WS-Security Policy) devant être prises en charge par la liaison.</span><span class="sxs-lookup"><span data-stu-id="ac159-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="ac159-119">Cette valeur est de type <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="ac159-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="ac159-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="ac159-120">inclusionMode</span></span>|<span data-ttu-id="ac159-121">Indique les spécifications d'inclusion de jeton.</span><span class="sxs-lookup"><span data-stu-id="ac159-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="ac159-122">Cet attribut est de type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="ac159-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="ac159-123">keySize</span><span class="sxs-lookup"><span data-stu-id="ac159-123">keySize</span></span>|<span data-ttu-id="ac159-124">Entier qui spécifie la taille de clé de jeton.</span><span class="sxs-lookup"><span data-stu-id="ac159-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="ac159-125">La valeur par défaut est 256.</span><span class="sxs-lookup"><span data-stu-id="ac159-125">The default value is 256.</span></span>|  
|<span data-ttu-id="ac159-126">keyType</span><span class="sxs-lookup"><span data-stu-id="ac159-126">keyType</span></span>|<span data-ttu-id="ac159-127">Valeur correcte de <xref:System.IdentityModel.Tokens.SecurityKeyType> indiquant le type de clé.</span><span class="sxs-lookup"><span data-stu-id="ac159-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="ac159-128">La valeur par défaut est `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="ac159-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="ac159-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="ac159-129">tokenType</span></span>|<span data-ttu-id="ac159-130">Chaîne indiquant le type de jeton.</span><span class="sxs-lookup"><span data-stu-id="ac159-130">A string that specifies the token type.</span></span> <span data-ttu-id="ac159-131">La valeur par défaut est « http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML ».</span><span class="sxs-lookup"><span data-stu-id="ac159-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac159-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac159-132">Child Elements</span></span>  
  
|<span data-ttu-id="ac159-133">Élément</span><span class="sxs-lookup"><span data-stu-id="ac159-133">Element</span></span>|<span data-ttu-id="ac159-134">Description</span><span class="sxs-lookup"><span data-stu-id="ac159-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac159-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="ac159-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="ac159-136">Collection d’éléments de configuration indiquant des paramètres de demande supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ac159-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="ac159-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="ac159-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="ac159-138">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="ac159-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="ac159-139">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="ac159-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ac159-140">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="ac159-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ac159-141">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d’identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="ac159-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="ac159-142">\<l’émetteur ></span><span class="sxs-lookup"><span data-stu-id="ac159-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="ac159-143">Élément de configuration qui spécifie le point de terminaison émettant le jeton actuel.</span><span class="sxs-lookup"><span data-stu-id="ac159-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="ac159-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="ac159-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="ac159-145">Élément de configuration qui spécifie l'adresse de point de terminaison correspondant aux métadonnées de l'émetteur de jeton.</span><span class="sxs-lookup"><span data-stu-id="ac159-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac159-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac159-146">Parent Elements</span></span>  
  
|<span data-ttu-id="ac159-147">Élément</span><span class="sxs-lookup"><span data-stu-id="ac159-147">Element</span></span>|<span data-ttu-id="ac159-148">Description</span><span class="sxs-lookup"><span data-stu-id="ac159-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac159-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="ac159-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="ac159-150">Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="ac159-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="ac159-151">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="ac159-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="ac159-152">Spécifie les options de sécurité d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ac159-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac159-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac159-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="ac159-154">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ac159-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ac159-155">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="ac159-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ac159-156">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ac159-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ac159-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ac159-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="ac159-158">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac159-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="ac159-159">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="ac159-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="ac159-160">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="ac159-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ac159-161">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ac159-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ac159-162">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ac159-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="ac159-163">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="ac159-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
