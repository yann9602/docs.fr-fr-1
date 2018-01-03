---
title: '&lt;nameClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2c53886458b4c6e2867e1f9fddd4ab50b199c660
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="6e5a7-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="6e5a7-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="6e5a7-103">Définit le type de revendication qui spécifie le <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6e5a7-104">Le type de revendication est utilisé pour rechercher un <xref:System.Security.Claims.Claim> dans la collection de <xref:System.Security.Claims.ClaimsIdentity> objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="6e5a7-105">La valeur de la revendication correspondante est alors définie comme le nom de la <xref:System.Security.Principal.IIdentity> généré à partir de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="6e5a7-106">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-106">\<system.identityModel></span></span>  
<span data-ttu-id="6e5a7-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-107">\<identityConfiguration></span></span>  
<span data-ttu-id="6e5a7-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6e5a7-109">\<add></span><span class="sxs-lookup"><span data-stu-id="6e5a7-109">\<add></span></span>  
<span data-ttu-id="6e5a7-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="6e5a7-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5a7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e5a7-112">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e5a7-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6e5a7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6e5a7-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e5a7-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="6e5a7-115">Attributes</span></span>  
  
|<span data-ttu-id="6e5a7-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="6e5a7-116">Attribute</span></span>|<span data-ttu-id="6e5a7-117">Description</span><span class="sxs-lookup"><span data-stu-id="6e5a7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e5a7-118">par défaut</span><span class="sxs-lookup"><span data-stu-id="6e5a7-118">value</span></span>|<span data-ttu-id="6e5a7-119">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour le <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6e5a7-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e5a7-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6e5a7-121">Child Elements</span></span>  
 <span data-ttu-id="6e5a7-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e5a7-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6e5a7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e5a7-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6e5a7-124">Element</span></span>|<span data-ttu-id="6e5a7-125">Description</span><span class="sxs-lookup"><span data-stu-id="6e5a7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e5a7-126">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6e5a7-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="6e5a7-127">Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> (classe), la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée d’un de ces classes.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e5a7-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6e5a7-128">Remarks</span></span>  
 <span data-ttu-id="6e5a7-129">Le `<nameClaimType>` ensembles d’éléments le <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e5a7-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e5a7-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e5a7-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e5a7-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
