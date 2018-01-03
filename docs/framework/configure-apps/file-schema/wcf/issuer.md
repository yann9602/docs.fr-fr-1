---
title: "&lt;émetteur&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e034b3ed0813d621ed86c2c3e86bb901ab39e40b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="5243d-102">&lt;émetteur&gt;</span><span class="sxs-lookup"><span data-stu-id="5243d-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="5243d-103">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5243d-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="5243d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5243d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5243d-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="5243d-105">\<bindings></span></span>  
<span data-ttu-id="5243d-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5243d-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="5243d-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="5243d-107">\<binding></span></span>  
<span data-ttu-id="5243d-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="5243d-108">\<security></span></span>  
<span data-ttu-id="5243d-109">\<message ></span><span class="sxs-lookup"><span data-stu-id="5243d-109">\<message></span></span>  
<span data-ttu-id="5243d-110">\<l’émetteur ></span><span class="sxs-lookup"><span data-stu-id="5243d-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5243d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5243d-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5243d-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5243d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5243d-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5243d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5243d-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5243d-114">Attributes</span></span>  
  
|<span data-ttu-id="5243d-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="5243d-115">Attribute</span></span>|<span data-ttu-id="5243d-116">Description</span><span class="sxs-lookup"><span data-stu-id="5243d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5243d-117">address</span><span class="sxs-lookup"><span data-stu-id="5243d-117">address</span></span>|<span data-ttu-id="5243d-118">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="5243d-118">Required string.</span></span> <span data-ttu-id="5243d-119">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="5243d-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5243d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5243d-120">Child Elements</span></span>  
  
|<span data-ttu-id="5243d-121">Élément</span><span class="sxs-lookup"><span data-stu-id="5243d-121">Element</span></span>|<span data-ttu-id="5243d-122">Description</span><span class="sxs-lookup"><span data-stu-id="5243d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5243d-123">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="5243d-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="5243d-124">Collection d’en-têtes d’adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="5243d-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="5243d-125">\<identité ></span><span class="sxs-lookup"><span data-stu-id="5243d-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5243d-126">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="5243d-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5243d-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5243d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5243d-128">Élément</span><span class="sxs-lookup"><span data-stu-id="5243d-128">Element</span></span>|<span data-ttu-id="5243d-129">Description</span><span class="sxs-lookup"><span data-stu-id="5243d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5243d-130">\<message ></span><span class="sxs-lookup"><span data-stu-id="5243d-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="5243d-131">Définit les paramètres de la sécurité au niveau du message pour le [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="5243d-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5243d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5243d-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="5243d-133">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="5243d-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5243d-134">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="5243d-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="5243d-135">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="5243d-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5243d-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="5243d-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="5243d-137">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="5243d-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="5243d-138">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="5243d-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
