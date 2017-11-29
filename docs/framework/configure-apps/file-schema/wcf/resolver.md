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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5734a985c4941a12be5032c254a75987f2074da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltresolvergt"></a><span data-ttu-id="335a8-102">&lt;programme de résolution&gt;</span><span class="sxs-lookup"><span data-stu-id="335a8-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="335a8-103">Spécifie un programme de résolution d'homologue utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds d'homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="335a8-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="335a8-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="335a8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="335a8-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="335a8-105">\<bindings></span></span>  
<span data-ttu-id="335a8-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="335a8-106">\<netPeerBinding></span></span>  
<span data-ttu-id="335a8-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="335a8-107">\<binding></span></span>  
<span data-ttu-id="335a8-108">\<programme de résolution ></span><span class="sxs-lookup"><span data-stu-id="335a8-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335a8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="335a8-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="335a8-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="335a8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="335a8-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="335a8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="335a8-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="335a8-112">Attributes</span></span>  
  
|<span data-ttu-id="335a8-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="335a8-113">Attribute</span></span>|<span data-ttu-id="335a8-114">Description</span><span class="sxs-lookup"><span data-stu-id="335a8-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="335a8-115">Chaîne qui spécifie si l'instance du programme de résolution d'homologue associée à ce service est spécifique au PNRP, à un programme de résolution personnalisé ou si elle est déterminée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="335a8-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="335a8-116">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="335a8-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="335a8-117">Chaîne qui spécifie la manière dont les références sont partagées parmi des homologues.</span><span class="sxs-lookup"><span data-stu-id="335a8-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="335a8-118">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="335a8-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="335a8-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="335a8-119">Child Elements</span></span>  
  
|<span data-ttu-id="335a8-120">Élément</span><span class="sxs-lookup"><span data-stu-id="335a8-120">Element</span></span>|<span data-ttu-id="335a8-121">Description</span><span class="sxs-lookup"><span data-stu-id="335a8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="335a8-122">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="335a8-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="335a8-123">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="335a8-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="335a8-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="335a8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="335a8-125">Élément</span><span class="sxs-lookup"><span data-stu-id="335a8-125">Element</span></span>|<span data-ttu-id="335a8-126">Description</span><span class="sxs-lookup"><span data-stu-id="335a8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="335a8-127">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="335a8-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="335a8-128">Définit toutes les fonctions de liaison de la [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="335a8-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="335a8-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="335a8-129">Remarks</span></span>  
 <span data-ttu-id="335a8-130">Un programme de résolution de nom d'homologue est un service de découverte utilisé par les canaux homologues afin de rechercher des nœuds d'homologues faisant partie d'une maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="335a8-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="335a8-131">Il est également utilisé pour « inscrire » un nœud avec un maillage d'homologue, le mécanisme par lequel le nœud homologue est connu et disponible à partir du maillage d'homologue.</span><span class="sxs-lookup"><span data-stu-id="335a8-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="335a8-132">Pour plus d’informations sur les programmes de résolution d’homologue, consultez [programmes de résolution d’homologue](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="335a8-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335a8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="335a8-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="335a8-134">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="335a8-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="335a8-135">Ajout d’un programme de résolution personnalisé à une Application PeerChannel</span><span class="sxs-lookup"><span data-stu-id="335a8-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
