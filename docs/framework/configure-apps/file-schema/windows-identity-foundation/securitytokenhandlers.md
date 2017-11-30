---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="b31ef-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="b31ef-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="b31ef-103">Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b31ef-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="b31ef-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b31ef-104">\<system.identityModel></span></span>  
<span data-ttu-id="b31ef-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b31ef-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b31ef-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b31ef-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31ef-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b31ef-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b31ef-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b31ef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b31ef-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b31ef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b31ef-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b31ef-110">Attributes</span></span>  
  
|<span data-ttu-id="b31ef-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b31ef-111">Attribute</span></span>|<span data-ttu-id="b31ef-112">Description</span><span class="sxs-lookup"><span data-stu-id="b31ef-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b31ef-113">name</span><span class="sxs-lookup"><span data-stu-id="b31ef-113">name</span></span>|<span data-ttu-id="b31ef-114">Spécifie le nom d’une collection de gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="b31ef-115">Les seules valeurs reconnues par l’infrastructure sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="b31ef-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b31ef-116">Si les collections de gestionnaire de jetons sont spécifiées avec une de ces noms, la collection sera utilisée lors du traitement de ActAs ou OnBehalfOf respectivement de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b31ef-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b31ef-117">Child Elements</span></span>  
  
|<span data-ttu-id="b31ef-118">Élément</span><span class="sxs-lookup"><span data-stu-id="b31ef-118">Element</span></span>|<span data-ttu-id="b31ef-119">Description</span><span class="sxs-lookup"><span data-stu-id="b31ef-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b31ef-120">\<add></span><span class="sxs-lookup"><span data-stu-id="b31ef-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b31ef-121">Ajoute un gestionnaire de jetons de sécurité à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="b31ef-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="b31ef-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="b31ef-123">Efface tous les gestionnaires de jetons de sécurité à partir de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="b31ef-124">\<remove></span><span class="sxs-lookup"><span data-stu-id="b31ef-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="b31ef-125">Supprime un gestionnaire de jetons de sécurité de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="b31ef-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b31ef-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b31ef-127">Fournit la configuration de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b31ef-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b31ef-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b31ef-129">Élément</span><span class="sxs-lookup"><span data-stu-id="b31ef-129">Element</span></span>|<span data-ttu-id="b31ef-130">Description</span><span class="sxs-lookup"><span data-stu-id="b31ef-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b31ef-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b31ef-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="b31ef-132">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="b31ef-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b31ef-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="b31ef-133">Remarks</span></span>  
 <span data-ttu-id="b31ef-134">Vous pouvez spécifier une ou plusieurs collections nommées de gestionnaires de jetons de sécurité dans une configuration de service.</span><span class="sxs-lookup"><span data-stu-id="b31ef-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="b31ef-135">Vous pouvez spécifier un nom pour une collection en utilisant la `name` attribut.</span><span class="sxs-lookup"><span data-stu-id="b31ef-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="b31ef-136">Le framework gère les seuls noms sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="b31ef-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b31ef-137">Si les gestionnaires d’existent dans ces collections, elles sont utilisées par un service de jeton de sécurité (STS) au lieu des gestionnaires par défaut lors du traitement de `ActAs` et `OnBehalfOf` jetons.</span><span class="sxs-lookup"><span data-stu-id="b31ef-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="b31ef-138">Par défaut, la collection est remplie avec les types de gestionnaires suivants : <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, et <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="b31ef-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="b31ef-139">Vous pouvez modifier la collection à l’aide de la `<add>`, `<remove>`, et `<clear>` éléments.</span><span class="sxs-lookup"><span data-stu-id="b31ef-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="b31ef-140">Vous devez vous assurer qu’uniquement un seul gestionnaire d’un type particulier existe dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b31ef-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="b31ef-141">Par exemple, si vous dérivez un gestionnaire à partir de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, soit votre gestionnaire ou le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> peut être configuré dans une collection unique, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="b31ef-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="b31ef-142">Utilisez le `<securityTokenHandlerConfiguration>` élément pour spécifier les paramètres de configuration pour les gestionnaires de la collection.</span><span class="sxs-lookup"><span data-stu-id="b31ef-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="b31ef-143">Paramètres spécifiés par cet élément remplacent celles spécifiées sur le service via la [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="b31ef-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="b31ef-144">Certains gestionnaires (y compris les différents types de gestionnaire intégré) peuvent prendre en charge une configuration supplémentaire via un élément enfant de le `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="b31ef-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="b31ef-145">Les paramètres spécifiés sur un gestionnaire remplacent les paramètres équivalents spécifiés dans la collection ou le service.</span><span class="sxs-lookup"><span data-stu-id="b31ef-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
