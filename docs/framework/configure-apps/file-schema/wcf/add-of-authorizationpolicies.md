---
title: '&lt;add&gt; de &lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="7538e-102">&lt;add&gt; de &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="7538e-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="7538e-103">Spécifie une stratégie d'autorisation pour la transformation de revendications.</span><span class="sxs-lookup"><span data-stu-id="7538e-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="7538e-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7538e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7538e-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="7538e-105">\<behaviors></span></span>  
<span data-ttu-id="7538e-106">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="7538e-106">\<behavior></span></span>  
<span data-ttu-id="7538e-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="7538e-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="7538e-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="7538e-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="7538e-109">\<add></span><span class="sxs-lookup"><span data-stu-id="7538e-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7538e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7538e-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="7538e-111">Type</span><span class="sxs-lookup"><span data-stu-id="7538e-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7538e-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7538e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7538e-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7538e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7538e-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="7538e-114">Attributes</span></span>  
  
|<span data-ttu-id="7538e-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="7538e-115">Attribute</span></span>|<span data-ttu-id="7538e-116">Description</span><span class="sxs-lookup"><span data-stu-id="7538e-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="7538e-117">Attribut String requis.</span><span class="sxs-lookup"><span data-stu-id="7538e-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="7538e-118">Le modèle de contrôle d'accès de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] prend en charge la configuration d'un ensemble de stratégies d'autorisation en tant que types.</span><span class="sxs-lookup"><span data-stu-id="7538e-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="7538e-119">Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="7538e-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7538e-120">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="7538e-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7538e-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7538e-121">Child Elements</span></span>  
 <span data-ttu-id="7538e-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7538e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7538e-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7538e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7538e-124">Élément</span><span class="sxs-lookup"><span data-stu-id="7538e-124">Element</span></span>|<span data-ttu-id="7538e-125">Description</span><span class="sxs-lookup"><span data-stu-id="7538e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7538e-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="7538e-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="7538e-127">Indique une collection de types de stratégie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7538e-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7538e-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="7538e-128">Remarks</span></span>  
 <span data-ttu-id="7538e-129">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="7538e-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="7538e-130">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="7538e-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7538e-131">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="7538e-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="7538e-132">Pour plus d’informations sur le fonctionne d’une stratégie d’autorisation, consultez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et [stratégie d’autorisation](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="7538e-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7538e-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7538e-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="7538e-134">Autoriser l’accès aux opérations de Service</span><span class="sxs-lookup"><span data-stu-id="7538e-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="7538e-135">Comment : créer un gestionnaire d’autorisation personnalisé pour un Service</span><span class="sxs-lookup"><span data-stu-id="7538e-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="7538e-136">\<add></span><span class="sxs-lookup"><span data-stu-id="7538e-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="7538e-137">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="7538e-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
