---
title: "&lt;clear&gt;, élément de &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5c3b101c51bcba1c1a579dcf99001c4b8dbab2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="b9a2e-102">&lt;clear&gt;, élément de &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="b9a2e-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="b9a2e-103">Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="b9a2e-104">Cela garantit que la collection est vide au démarrage.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="b9a2e-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9a2e-106">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-106">\<bindings></span></span>  
<span data-ttu-id="b9a2e-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="b9a2e-108">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-108">\<binding></span></span>  
<span data-ttu-id="b9a2e-109">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-109">\<security></span></span>  
<span data-ttu-id="b9a2e-110">\<message ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-110">\<message></span></span>  
<span data-ttu-id="b9a2e-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a2e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9a2e-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9a2e-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b9a2e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b9a2e-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9a2e-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="b9a2e-115">Attributes</span></span>  
 <span data-ttu-id="b9a2e-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="b9a2e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9a2e-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b9a2e-117">Child Elements</span></span>  
 <span data-ttu-id="b9a2e-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9a2e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b9a2e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b9a2e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="b9a2e-120">Element</span></span>|<span data-ttu-id="b9a2e-121">Description</span><span class="sxs-lookup"><span data-stu-id="b9a2e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9a2e-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="b9a2e-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="b9a2e-123">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b9a2e-124">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b9a2e-125">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b9a2e-126">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b9a2e-127">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d’identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b9a2e-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9a2e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9a2e-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
