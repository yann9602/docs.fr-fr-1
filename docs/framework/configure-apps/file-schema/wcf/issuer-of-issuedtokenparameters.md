---
title: '&lt;issuer&gt; de &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1eae3b472e33d4d0504ba487c8c871165af8cdf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="2b5f8-102">&lt;issuer&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2b5f8-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="2b5f8-103">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="2b5f8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2b5f8-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-105">\<bindings></span></span>  
<span data-ttu-id="2b5f8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-106">\<customBinding></span></span>  
<span data-ttu-id="2b5f8-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-107">\<binding></span></span>  
<span data-ttu-id="2b5f8-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-108">\<security></span></span>  
<span data-ttu-id="2b5f8-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="2b5f8-110">\<l’émetteur ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5f8-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b5f8-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b5f8-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2b5f8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2b5f8-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b5f8-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="2b5f8-114">Attributes</span></span>  
  
|<span data-ttu-id="2b5f8-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="2b5f8-115">Attribute</span></span>|<span data-ttu-id="2b5f8-116">Description</span><span class="sxs-lookup"><span data-stu-id="2b5f8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b5f8-117">address</span><span class="sxs-lookup"><span data-stu-id="2b5f8-117">address</span></span>|<span data-ttu-id="2b5f8-118">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-118">Required string.</span></span> <span data-ttu-id="2b5f8-119">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b5f8-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2b5f8-120">Child Elements</span></span>  
  
|<span data-ttu-id="2b5f8-121">Élément</span><span class="sxs-lookup"><span data-stu-id="2b5f8-121">Element</span></span>|<span data-ttu-id="2b5f8-122">Description</span><span class="sxs-lookup"><span data-stu-id="2b5f8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5f8-123">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2b5f8-124">Collection d’en-têtes d’adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="2b5f8-125">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2b5f8-126">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b5f8-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2b5f8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="2b5f8-128">Élément</span><span class="sxs-lookup"><span data-stu-id="2b5f8-128">Element</span></span>|<span data-ttu-id="2b5f8-129">Description</span><span class="sxs-lookup"><span data-stu-id="2b5f8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5f8-130">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="2b5f8-131">Spécifie le jeton émis en cours.</span><span class="sxs-lookup"><span data-stu-id="2b5f8-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b5f8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b5f8-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2b5f8-133">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="2b5f8-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2b5f8-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2b5f8-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2b5f8-135">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2b5f8-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="2b5f8-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2b5f8-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2b5f8-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2b5f8-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2b5f8-138">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="2b5f8-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2b5f8-139">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2b5f8-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2b5f8-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b5f8-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="2b5f8-141">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b5f8-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="2b5f8-142">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="2b5f8-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
