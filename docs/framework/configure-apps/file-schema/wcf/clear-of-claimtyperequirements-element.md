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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 69752480a7f399a202d497e12a783ffa091dd4b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="1a488-102">&lt;clear&gt;, élément de &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="1a488-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="1a488-103">Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="1a488-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="1a488-104">Cela garantit que la collection est vide au démarrage.</span><span class="sxs-lookup"><span data-stu-id="1a488-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="1a488-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a488-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a488-106">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="1a488-106">\<bindings></span></span>  
<span data-ttu-id="1a488-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="1a488-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="1a488-108">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="1a488-108">\<binding></span></span>  
<span data-ttu-id="1a488-109">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="1a488-109">\<security></span></span>  
<span data-ttu-id="1a488-110">\<message ></span><span class="sxs-lookup"><span data-stu-id="1a488-110">\<message></span></span>  
<span data-ttu-id="1a488-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="1a488-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a488-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a488-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a488-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1a488-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1a488-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1a488-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a488-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="1a488-115">Attributes</span></span>  
 <span data-ttu-id="1a488-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="1a488-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a488-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1a488-117">Child Elements</span></span>  
 <span data-ttu-id="1a488-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1a488-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a488-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1a488-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a488-120">Élément</span><span class="sxs-lookup"><span data-stu-id="1a488-120">Element</span></span>|<span data-ttu-id="1a488-121">Description</span><span class="sxs-lookup"><span data-stu-id="1a488-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a488-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="1a488-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="1a488-123">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="1a488-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="1a488-124">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="1a488-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="1a488-125">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="1a488-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1a488-126">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="1a488-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1a488-127">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d’identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="1a488-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a488-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a488-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
