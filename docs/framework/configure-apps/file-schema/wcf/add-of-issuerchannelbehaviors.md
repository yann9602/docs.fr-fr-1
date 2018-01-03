---
title: '&lt;add&gt; de &lt;issuerChannelBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf66b3d3b531ae41329aade6a416c330957d83c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="3d639-102">&lt;add&gt; de &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="3d639-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="3d639-103">Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.</span><span class="sxs-lookup"><span data-stu-id="3d639-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d639-104">Si un comportement de point de terminaison contient un [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) élément, une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="3d639-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="3d639-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3d639-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d639-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="3d639-106">\<behaviors></span></span>  
<span data-ttu-id="3d639-107">section d’endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="3d639-107">endpointBehaviors section</span></span>  
<span data-ttu-id="3d639-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="3d639-108">\<behavior></span></span>  
<span data-ttu-id="3d639-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="3d639-109">\<clientCredentials></span></span>  
<span data-ttu-id="3d639-110">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="3d639-110">\<issuedToken></span></span>  
<span data-ttu-id="3d639-111">\<issuerChannelBehaviors > élément</span><span class="sxs-lookup"><span data-stu-id="3d639-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="3d639-112">\<add></span><span class="sxs-lookup"><span data-stu-id="3d639-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d639-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d639-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d639-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d639-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3d639-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3d639-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d639-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d639-116">Attributes</span></span>  
  
|<span data-ttu-id="3d639-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="3d639-117">Attribute</span></span>|<span data-ttu-id="3d639-118">Description</span><span class="sxs-lookup"><span data-stu-id="3d639-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d639-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="3d639-119">issuerAddress</span></span>|<span data-ttu-id="3d639-120">URI de l'émetteur de jeton de sécurité avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="3d639-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="3d639-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d639-121">behaviorConfiguration</span></span>|<span data-ttu-id="3d639-122">Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3d639-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d639-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d639-123">Child Elements</span></span>  
 <span data-ttu-id="3d639-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d639-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d639-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d639-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3d639-126">Élément</span><span class="sxs-lookup"><span data-stu-id="3d639-126">Element</span></span>|<span data-ttu-id="3d639-127">Description</span><span class="sxs-lookup"><span data-stu-id="3d639-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d639-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3d639-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="3d639-129">Contient une collection de comportements de point de terminaison du client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] à utiliser lors d'une communication avec les services STS spécifiés.</span><span class="sxs-lookup"><span data-stu-id="3d639-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d639-130">Notes</span><span class="sxs-lookup"><span data-stu-id="3d639-130">Remarks</span></span>  
 <span data-ttu-id="3d639-131">`issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer.</span><span class="sxs-lookup"><span data-stu-id="3d639-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="3d639-132">`behaviorConfiguration` pointe vers un comportement de point de terminaison que l'application utilise dans les canaux créés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] pour obtenir les jetons émis depuis les services d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="3d639-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d639-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d639-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="3d639-134">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="3d639-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="3d639-135">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="3d639-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="3d639-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="3d639-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="3d639-137">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3d639-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3d639-138">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="3d639-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="3d639-139">Guide pratique pour créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="3d639-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="3d639-140">Guide pratique pour configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="3d639-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="3d639-141">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="3d639-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="3d639-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3d639-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
