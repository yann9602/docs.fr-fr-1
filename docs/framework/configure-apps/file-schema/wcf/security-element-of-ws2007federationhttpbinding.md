---
title: "&lt;security&gt;, élément de &lt;ws2007FederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 27fedcd8ae7501f484de0aa2f21af8c701990285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="f4916-102">&lt;security&gt;, élément de &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f4916-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="f4916-103">Définit les paramètres de sécurité de le [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="f4916-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="f4916-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f4916-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4916-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="f4916-105">\<bindings></span></span>  
<span data-ttu-id="f4916-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f4916-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="f4916-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f4916-107">\<binding></span></span>  
<span data-ttu-id="f4916-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="f4916-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4916-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4916-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4916-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4916-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f4916-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4916-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4916-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4916-112">Attributes</span></span>  
  
|<span data-ttu-id="f4916-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f4916-113">Attribute</span></span>|<span data-ttu-id="f4916-114">Description</span><span class="sxs-lookup"><span data-stu-id="f4916-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="f4916-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f4916-115">Optional.</span></span> <span data-ttu-id="f4916-116">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="f4916-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f4916-117">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="f4916-117">The default value is `Message`.</span></span> <span data-ttu-id="f4916-118">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f4916-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f4916-119">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="f4916-119">mode Attribute</span></span>  
  
|<span data-ttu-id="f4916-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="f4916-120">Value</span></span>|<span data-ttu-id="f4916-121">Description</span><span class="sxs-lookup"><span data-stu-id="f4916-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4916-122">None</span><span class="sxs-lookup"><span data-stu-id="f4916-122">None</span></span>|<span data-ttu-id="f4916-123">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="f4916-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="f4916-124">Message</span><span class="sxs-lookup"><span data-stu-id="f4916-124">Message</span></span>|<span data-ttu-id="f4916-125">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="f4916-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="f4916-126">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="f4916-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="f4916-127">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="f4916-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="f4916-128">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f4916-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="f4916-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f4916-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="f4916-130">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4916-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="f4916-131">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="f4916-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="f4916-132">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f4916-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4916-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4916-133">Child Elements</span></span>  
  
|<span data-ttu-id="f4916-134">Élément</span><span class="sxs-lookup"><span data-stu-id="f4916-134">Element</span></span>|<span data-ttu-id="f4916-135">Description</span><span class="sxs-lookup"><span data-stu-id="f4916-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4916-136">\<message ></span><span class="sxs-lookup"><span data-stu-id="f4916-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="f4916-137">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="f4916-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="f4916-138">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="f4916-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4916-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4916-139">Parent Elements</span></span>  
  
|<span data-ttu-id="f4916-140">Élément</span><span class="sxs-lookup"><span data-stu-id="f4916-140">Element</span></span>|<span data-ttu-id="f4916-141">Description</span><span class="sxs-lookup"><span data-stu-id="f4916-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4916-142">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f4916-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f4916-143">Définit toutes les fonctions de liaison de la [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f4916-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4916-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4916-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="f4916-145">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f4916-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="f4916-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f4916-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f4916-147">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="f4916-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="f4916-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f4916-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f4916-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f4916-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f4916-150">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f4916-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f4916-151">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="f4916-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
