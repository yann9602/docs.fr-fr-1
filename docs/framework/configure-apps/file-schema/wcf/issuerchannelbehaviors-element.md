---
title: "&lt;issuerChannelBehaviors&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="40dfd-102">&lt;issuerChannelBehaviors&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="40dfd-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="40dfd-103">Contient une collection de comportements de point de terminaison client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (définis dans la configuration) à utiliser lors de la communication avec les services d'émission de jeton de sécurité spécifiés.</span><span class="sxs-lookup"><span data-stu-id="40dfd-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="40dfd-104">Les comportements définis ne peut pas inclure les caractères [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="40dfd-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="40dfd-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40dfd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="40dfd-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="40dfd-106">\<behaviors></span></span>  
<span data-ttu-id="40dfd-107">section d’endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="40dfd-107">endpointBehaviors section</span></span>  
<span data-ttu-id="40dfd-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="40dfd-108">\<behavior></span></span>  
<span data-ttu-id="40dfd-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="40dfd-109">\<clientCredentials></span></span>  
<span data-ttu-id="40dfd-110">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="40dfd-110">\<issuedToken></span></span>  
<span data-ttu-id="40dfd-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40dfd-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40dfd-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40dfd-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40dfd-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40dfd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40dfd-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40dfd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40dfd-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="40dfd-115">Attributes</span></span>  
 <span data-ttu-id="40dfd-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="40dfd-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40dfd-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40dfd-117">Child Elements</span></span>  
  
|<span data-ttu-id="40dfd-118">Élément</span><span class="sxs-lookup"><span data-stu-id="40dfd-118">Element</span></span>|<span data-ttu-id="40dfd-119">Description</span><span class="sxs-lookup"><span data-stu-id="40dfd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40dfd-120">\<add></span><span class="sxs-lookup"><span data-stu-id="40dfd-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="40dfd-121">Ajoute un comportement à la collection.</span><span class="sxs-lookup"><span data-stu-id="40dfd-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40dfd-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40dfd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="40dfd-123">Élément</span><span class="sxs-lookup"><span data-stu-id="40dfd-123">Element</span></span>|<span data-ttu-id="40dfd-124">Description</span><span class="sxs-lookup"><span data-stu-id="40dfd-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40dfd-125">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="40dfd-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="40dfd-126">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="40dfd-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40dfd-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="40dfd-127">Remarks</span></span>  
 <span data-ttu-id="40dfd-128">Utilisez cet élément lorsque des comportements (autres que ceux qui contiennent des éléments `<clientCredentials>`) doivent être utilisés pour communiquer avec un service.</span><span class="sxs-lookup"><span data-stu-id="40dfd-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="40dfd-129">Par exemple, si un [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) élément de comportement doit être inclus.</span><span class="sxs-lookup"><span data-stu-id="40dfd-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dfd-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40dfd-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="40dfd-131">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="40dfd-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="40dfd-132">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="40dfd-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="40dfd-133">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="40dfd-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="40dfd-134">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="40dfd-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="40dfd-135">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="40dfd-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="40dfd-136">Comment : créer un Client fédéré</span><span class="sxs-lookup"><span data-stu-id="40dfd-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="40dfd-137">Comment : configurer un émetteur Local</span><span class="sxs-lookup"><span data-stu-id="40dfd-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="40dfd-138">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="40dfd-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
