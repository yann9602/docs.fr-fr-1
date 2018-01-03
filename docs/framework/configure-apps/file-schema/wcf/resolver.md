---
title: "&lt;programme de résolution&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc6e919600fbea15937a61eaa65299b3a372caaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltresolvergt"></a><span data-ttu-id="c243d-102">&lt;programme de résolution&gt;</span><span class="sxs-lookup"><span data-stu-id="c243d-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="c243d-103">Spécifie un programme de résolution d'homologue utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds d'homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="c243d-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="c243d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c243d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c243d-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="c243d-105">\<bindings></span></span>  
<span data-ttu-id="c243d-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="c243d-106">\<netPeerBinding></span></span>  
<span data-ttu-id="c243d-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="c243d-107">\<binding></span></span>  
<span data-ttu-id="c243d-108">\<programme de résolution ></span><span class="sxs-lookup"><span data-stu-id="c243d-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c243d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c243d-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c243d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c243d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c243d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c243d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c243d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c243d-112">Attributes</span></span>  
  
|<span data-ttu-id="c243d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="c243d-113">Attribute</span></span>|<span data-ttu-id="c243d-114">Description</span><span class="sxs-lookup"><span data-stu-id="c243d-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="c243d-115">Chaîne qui spécifie si l'instance du programme de résolution d'homologue associée à ce service est spécifique au PNRP, à un programme de résolution personnalisé ou si elle est déterminée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c243d-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="c243d-116">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="c243d-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="c243d-117">Chaîne qui spécifie la manière dont les références sont partagées parmi des homologues.</span><span class="sxs-lookup"><span data-stu-id="c243d-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="c243d-118">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="c243d-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c243d-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c243d-119">Child Elements</span></span>  
  
|<span data-ttu-id="c243d-120">Élément</span><span class="sxs-lookup"><span data-stu-id="c243d-120">Element</span></span>|<span data-ttu-id="c243d-121">Description</span><span class="sxs-lookup"><span data-stu-id="c243d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c243d-122">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="c243d-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="c243d-123">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c243d-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c243d-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c243d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c243d-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c243d-125">Element</span></span>|<span data-ttu-id="c243d-126">Description</span><span class="sxs-lookup"><span data-stu-id="c243d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c243d-127">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="c243d-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c243d-128">Définit toutes les fonctions de liaison de la [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c243d-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c243d-129">Notes</span><span class="sxs-lookup"><span data-stu-id="c243d-129">Remarks</span></span>  
 <span data-ttu-id="c243d-130">Un programme de résolution de nom d'homologue est un service de découverte utilisé par les canaux homologues afin de rechercher des nœuds d'homologues faisant partie d'une maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="c243d-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="c243d-131">Il est également utilisé pour « inscrire » un nœud avec un maillage d'homologue, le mécanisme par lequel le nœud homologue est connu et disponible à partir du maillage d'homologue.</span><span class="sxs-lookup"><span data-stu-id="c243d-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="c243d-132">Pour plus d’informations sur les programmes de résolution d’homologue, consultez [programmes de résolution d’homologue](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="c243d-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c243d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c243d-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="c243d-134">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="c243d-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="c243d-135">Ajout d’un programme de résolution personnalisé à une Application PeerChannel</span><span class="sxs-lookup"><span data-stu-id="c243d-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
