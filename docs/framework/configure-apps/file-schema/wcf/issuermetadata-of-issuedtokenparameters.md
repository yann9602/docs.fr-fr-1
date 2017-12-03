---
title: '&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccd0417aeebbaf08d28457dd94a4d1698882c79e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="2a608-102">&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2a608-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="2a608-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2a608-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2a608-104">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="2a608-104">\<bindings></span></span>  
<span data-ttu-id="2a608-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2a608-105">\<customBinding></span></span>  
<span data-ttu-id="2a608-106">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="2a608-106">\<binding></span></span>  
<span data-ttu-id="2a608-107">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="2a608-107">\<security></span></span>  
<span data-ttu-id="2a608-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="2a608-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="2a608-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="2a608-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a608-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a608-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a608-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a608-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2a608-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a608-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a608-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a608-113">Attributes</span></span>  
  
|<span data-ttu-id="2a608-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a608-114">Attribute</span></span>|<span data-ttu-id="2a608-115">Description</span><span class="sxs-lookup"><span data-stu-id="2a608-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a608-116">address</span><span class="sxs-lookup"><span data-stu-id="2a608-116">address</span></span>|<span data-ttu-id="2a608-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="2a608-117">Required.</span></span> <span data-ttu-id="2a608-118">Chaîne qui spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2a608-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="2a608-119">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="2a608-119">The address must be an absolute URI.</span></span> <span data-ttu-id="2a608-120">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="2a608-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a608-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a608-121">Child Elements</span></span>  
  
|<span data-ttu-id="2a608-122">Élément</span><span class="sxs-lookup"><span data-stu-id="2a608-122">Element</span></span>|<span data-ttu-id="2a608-123">Description</span><span class="sxs-lookup"><span data-stu-id="2a608-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a608-124">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="2a608-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2a608-125">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="2a608-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="2a608-126">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2a608-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2a608-127">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="2a608-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a608-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a608-128">Parent Elements</span></span>  
  
|<span data-ttu-id="2a608-129">Élément</span><span class="sxs-lookup"><span data-stu-id="2a608-129">Element</span></span>|<span data-ttu-id="2a608-130">Description</span><span class="sxs-lookup"><span data-stu-id="2a608-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a608-131">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="2a608-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="2a608-132">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="2a608-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a608-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a608-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2a608-134">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="2a608-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2a608-135">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2a608-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2a608-136">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2a608-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="2a608-137">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="2a608-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2a608-138">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2a608-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a608-139">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="2a608-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2a608-140">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2a608-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2a608-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2a608-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="2a608-142">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2a608-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="2a608-143">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="2a608-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
