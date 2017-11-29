---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b11f5cbf2d70b4fff607ac42c2c98af7fb9542b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="4911b-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="4911b-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="4911b-103">Spécifie l’adresse et la liaison de l’émetteur local à utiliser pour obtenir un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4911b-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="4911b-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4911b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4911b-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="4911b-105">\<behaviors></span></span>  
<span data-ttu-id="4911b-106">section d’endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="4911b-106">endpointBehaviors section</span></span>  
<span data-ttu-id="4911b-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4911b-107">\<behavior></span></span>  
<span data-ttu-id="4911b-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4911b-108">\<clientCredentials></span></span>  
<span data-ttu-id="4911b-109">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="4911b-109">\<issuedToken></span></span>  
<span data-ttu-id="4911b-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="4911b-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4911b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4911b-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4911b-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4911b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4911b-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4911b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4911b-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="4911b-114">Attributes</span></span>  
  
|<span data-ttu-id="4911b-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="4911b-115">Attribute</span></span>|<span data-ttu-id="4911b-116">Description</span><span class="sxs-lookup"><span data-stu-id="4911b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4911b-117">address</span><span class="sxs-lookup"><span data-stu-id="4911b-117">address</span></span>|<span data-ttu-id="4911b-118">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="4911b-118">Required string.</span></span> <span data-ttu-id="4911b-119">Spécifie l'URI de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="4911b-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="4911b-120">liaison</span><span class="sxs-lookup"><span data-stu-id="4911b-120">binding</span></span>|<span data-ttu-id="4911b-121">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="4911b-121">Optional string.</span></span> <span data-ttu-id="4911b-122">Une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="4911b-122">One of the system-provided bindings.</span></span> <span data-ttu-id="4911b-123">Pour obtenir la liste, consultez [les liaisons fournies](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="4911b-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="4911b-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4911b-124">bindingConfiguration</span></span>|<span data-ttu-id="4911b-125">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="4911b-125">Optional string.</span></span> <span data-ttu-id="4911b-126">Spécifie une configuration de liaison recherchée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4911b-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4911b-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4911b-127">Child Elements</span></span>  
  
|<span data-ttu-id="4911b-128">Élément</span><span class="sxs-lookup"><span data-stu-id="4911b-128">Element</span></span>|<span data-ttu-id="4911b-129">Description</span><span class="sxs-lookup"><span data-stu-id="4911b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4911b-130">\<identité ></span><span class="sxs-lookup"><span data-stu-id="4911b-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4911b-131">Spécifie les informations d'identité de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="4911b-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="4911b-132">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="4911b-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="4911b-133">Collection d’en-têtes d’adresse requis pour adresser correctement l’émetteur local.</span><span class="sxs-lookup"><span data-stu-id="4911b-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="4911b-134">Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.</span><span class="sxs-lookup"><span data-stu-id="4911b-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4911b-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4911b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4911b-136">Élément</span><span class="sxs-lookup"><span data-stu-id="4911b-136">Element</span></span>|<span data-ttu-id="4911b-137">Description</span><span class="sxs-lookup"><span data-stu-id="4911b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4911b-138">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="4911b-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="4911b-139">Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="4911b-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4911b-140">Remarques</span><span class="sxs-lookup"><span data-stu-id="4911b-140">Remarks</span></span>  
 <span data-ttu-id="4911b-141">Lors de l’obtention d’un jeton émis depuis un service d’émission de jeton de sécurité (STS), l’application cliente doit être configurée avec l’adresse et la liaison à utiliser pour pouvoir communiquer avec le STS.</span><span class="sxs-lookup"><span data-stu-id="4911b-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="4911b-142">Lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d'URL pour le service d'émission de jeton de sécurité ou lorsque l'adresse de l'émetteur d'une liaison fédérée est http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`, le canal [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] du client utilise les valeurs spécifiées par `address` et `binding` afin de communiquer avec le STS pour obtenir le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="4911b-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="4911b-143">Pour plus d’informations sur la configuration d’un émetteur local, consultez [Comment : configurer un émetteur Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="4911b-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4911b-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="4911b-144">Example</span></span>  
 <span data-ttu-id="4911b-145">L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.</span><span class="sxs-lookup"><span data-stu-id="4911b-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4911b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4911b-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="4911b-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="4911b-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4911b-148">Comment : configurer un émetteur Local</span><span class="sxs-lookup"><span data-stu-id="4911b-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="4911b-149">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="4911b-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4911b-150">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="4911b-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4911b-151">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="4911b-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="4911b-152">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="4911b-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="4911b-153">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="4911b-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="4911b-154">Comment : créer un Client fédéré</span><span class="sxs-lookup"><span data-stu-id="4911b-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="4911b-155">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="4911b-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
