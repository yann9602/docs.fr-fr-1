---
title: "&lt;remove&gt;, élément de &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 96155ed805d99a3678c5d20d83a490efb9811815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d821f-102">&lt;remove&gt;, élément de &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="d821f-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d821f-103">Spécifie les types de revendications à supprimer dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="d821f-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d821f-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d821f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d821f-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="d821f-105">\<bindings></span></span>  
<span data-ttu-id="d821f-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="d821f-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d821f-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="d821f-107">\<binding></span></span>  
<span data-ttu-id="d821f-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="d821f-108">\<security></span></span>  
<span data-ttu-id="d821f-109">\<message ></span><span class="sxs-lookup"><span data-stu-id="d821f-109">\<message></span></span>  
<span data-ttu-id="d821f-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d821f-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d821f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d821f-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d821f-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d821f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d821f-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d821f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d821f-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d821f-114">Attributes</span></span>  
  
|<span data-ttu-id="d821f-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d821f-115">Attribute</span></span>|<span data-ttu-id="d821f-116">Description</span><span class="sxs-lookup"><span data-stu-id="d821f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d821f-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d821f-117">claimType</span></span>|<span data-ttu-id="d821f-118">URI qui définit le type de revendication à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d821f-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d821f-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d821f-119">Child Elements</span></span>  
 <span data-ttu-id="d821f-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d821f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d821f-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d821f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d821f-122">Élément</span><span class="sxs-lookup"><span data-stu-id="d821f-122">Element</span></span>|<span data-ttu-id="d821f-123">Description</span><span class="sxs-lookup"><span data-stu-id="d821f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d821f-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d821f-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="d821f-125">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="d821f-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d821f-126">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d821f-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d821f-127">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="d821f-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d821f-128">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="d821f-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d821f-129">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d’identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="d821f-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d821f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d821f-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
