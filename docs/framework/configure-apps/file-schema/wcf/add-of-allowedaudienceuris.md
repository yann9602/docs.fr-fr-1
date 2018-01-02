---
title: '&lt;add&gt; de &lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b10a0ef5718197464ffa40126f0a013d82256dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="ee9d5-102">&lt;add&gt; de &lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="ee9d5-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="ee9d5-103">Ajoute un URI cible pour lequel le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="ee9d5-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee9d5-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-105">\<behaviors></span></span>  
<span data-ttu-id="ee9d5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ee9d5-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-107">\<behavior></span></span>  
<span data-ttu-id="ee9d5-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ee9d5-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="ee9d5-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="ee9d5-111">\<Ajouter >, élément pour \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee9d5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee9d5-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee9d5-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee9d5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ee9d5-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee9d5-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee9d5-115">Attributes</span></span>  
  
|<span data-ttu-id="ee9d5-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee9d5-116">Attribute</span></span>|<span data-ttu-id="ee9d5-117">Description</span><span class="sxs-lookup"><span data-stu-id="ee9d5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee9d5-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="ee9d5-118">allowedAudienceUri</span></span>|<span data-ttu-id="ee9d5-119">Chaîne qui contient un URI cible pour lequel le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee9d5-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee9d5-120">Child Elements</span></span>  
 <span data-ttu-id="ee9d5-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee9d5-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee9d5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ee9d5-123">Élément</span><span class="sxs-lookup"><span data-stu-id="ee9d5-123">Element</span></span>|<span data-ttu-id="ee9d5-124">Description</span><span class="sxs-lookup"><span data-stu-id="ee9d5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee9d5-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="ee9d5-126">Représente une collection d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee9d5-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ee9d5-127">Remarks</span></span>  
 <span data-ttu-id="ee9d5-128">Vous devez utiliser cette collection dans une application fédérée qui utilise un service de jeton de sécurité (STS) qui émet des jetons de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="ee9d5-129">Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> au jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="ee9d5-130">Cela permet au <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee9d5-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="ee9d5-131">Affectez à l'attribut `audienceUriMode` de `<issuedTokenAuthentication>` la valeur <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="ee9d5-132">Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="ee9d5-133">Pour plus d'informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="ee9d5-134">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer les informations d’identification sur un Service de fédération](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ee9d5-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9d5-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee9d5-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="ee9d5-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="ee9d5-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ee9d5-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="ee9d5-138">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="ee9d5-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="ee9d5-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ee9d5-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ee9d5-140">Guide pratique pour configurer des informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="ee9d5-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
