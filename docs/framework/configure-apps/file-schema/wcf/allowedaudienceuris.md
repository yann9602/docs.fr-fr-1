---
title: '&lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd3b197ffe771f72544dc3e61f49583c08fa5821
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="7606d-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="7606d-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="7606d-103">Représente une collection d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7606d-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="7606d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7606d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7606d-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="7606d-105">\<behaviors></span></span>  
<span data-ttu-id="7606d-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7606d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7606d-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="7606d-107">\<behavior></span></span>  
<span data-ttu-id="7606d-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7606d-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7606d-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7606d-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="7606d-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="7606d-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7606d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7606d-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7606d-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7606d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7606d-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7606d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7606d-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="7606d-114">Attributes</span></span>  
 <span data-ttu-id="7606d-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7606d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7606d-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7606d-116">Child Elements</span></span>  
  
|<span data-ttu-id="7606d-117">Élément</span><span class="sxs-lookup"><span data-stu-id="7606d-117">Element</span></span>|<span data-ttu-id="7606d-118">Description</span><span class="sxs-lookup"><span data-stu-id="7606d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7606d-119">\<add></span><span class="sxs-lookup"><span data-stu-id="7606d-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="7606d-120">Ajoute un URI cible pour lequel le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7606d-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7606d-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7606d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7606d-122">Élément</span><span class="sxs-lookup"><span data-stu-id="7606d-122">Element</span></span>|<span data-ttu-id="7606d-123">Description</span><span class="sxs-lookup"><span data-stu-id="7606d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7606d-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7606d-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="7606d-125">Spécifie un jeton émis en guise d'information d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="7606d-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7606d-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7606d-126">Remarks</span></span>  
 <span data-ttu-id="7606d-127">Vous devez utiliser cette collection dans une application fédérée qui utilise un service de jeton de sécurité (STS) qui émet des jetons de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="7606d-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="7606d-128">Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> au jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7606d-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="7606d-129">Cela permet au <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7606d-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="7606d-130">Affectez à l'attribut `audienceUriMode` de `<issuedTokenAuthentication>` la valeur <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="7606d-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="7606d-131">Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection.</span><span class="sxs-lookup"><span data-stu-id="7606d-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="7606d-132">Pour plus d'informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7606d-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="7606d-133">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer les informations d’identification sur un Service de fédération](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="7606d-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7606d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7606d-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="7606d-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7606d-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="7606d-136">\<add></span><span class="sxs-lookup"><span data-stu-id="7606d-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="7606d-137">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="7606d-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7606d-138">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7606d-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7606d-139">Guide pratique pour configurer des informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="7606d-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
