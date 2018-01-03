---
title: '&lt;roleClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: eb46585561ca8a2ab7c69f09d073d38bc1b60646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="75a4b-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="75a4b-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="75a4b-103">Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection de <xref:System.Security.Claims.ClaimsIdentity> objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du Gestionnaire de jeton.</span><span class="sxs-lookup"><span data-stu-id="75a4b-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="75a4b-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="75a4b-104">\<system.identityModel></span></span>  
<span data-ttu-id="75a4b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="75a4b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="75a4b-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="75a4b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="75a4b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="75a4b-107">\<add></span></span>  
<span data-ttu-id="75a4b-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="75a4b-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="75a4b-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="75a4b-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a4b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75a4b-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75a4b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75a4b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75a4b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75a4b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75a4b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="75a4b-113">Attributes</span></span>  
  
|<span data-ttu-id="75a4b-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="75a4b-114">Attribute</span></span>|<span data-ttu-id="75a4b-115">Description</span><span class="sxs-lookup"><span data-stu-id="75a4b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75a4b-116">par défaut</span><span class="sxs-lookup"><span data-stu-id="75a4b-116">value</span></span>|<span data-ttu-id="75a4b-117">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour le type de revendication de rôle.</span><span class="sxs-lookup"><span data-stu-id="75a4b-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75a4b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75a4b-118">Child Elements</span></span>  
 <span data-ttu-id="75a4b-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75a4b-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75a4b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75a4b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="75a4b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="75a4b-121">Element</span></span>|<span data-ttu-id="75a4b-122">Description</span><span class="sxs-lookup"><span data-stu-id="75a4b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75a4b-123">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="75a4b-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="75a4b-124">Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> (classe), la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée d’un de ces classes.</span><span class="sxs-lookup"><span data-stu-id="75a4b-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75a4b-125">Notes</span><span class="sxs-lookup"><span data-stu-id="75a4b-125">Remarks</span></span>  
 <span data-ttu-id="75a4b-126">Le `<roleClaimType>` ensembles d’éléments le <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="75a4b-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a4b-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="75a4b-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75a4b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75a4b-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
