---
title: "&lt;personnalisé&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bcab1e8361448abfe14db8ac38a924c656b9065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="39f99-102">&lt;personnalisé&gt;</span><span class="sxs-lookup"><span data-stu-id="39f99-102">&lt;custom&gt;</span></span>
<span data-ttu-id="39f99-103">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39f99-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="39f99-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="39f99-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39f99-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="39f99-105">\<bindings></span></span>  
<span data-ttu-id="39f99-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="39f99-106">\<netPeerBinding></span></span>  
<span data-ttu-id="39f99-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="39f99-107">\<binding></span></span>  
<span data-ttu-id="39f99-108">\<programme de résolution ></span><span class="sxs-lookup"><span data-stu-id="39f99-108">\<resolver></span></span>  
<span data-ttu-id="39f99-109">\<personnalisé ></span><span class="sxs-lookup"><span data-stu-id="39f99-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f99-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39f99-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f99-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="39f99-111">Attributes and Elements</span></span>  
 <span data-ttu-id="39f99-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="39f99-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f99-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="39f99-113">Attributes</span></span>  
  
|<span data-ttu-id="39f99-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="39f99-114">Attribute</span></span>|<span data-ttu-id="39f99-115">Description</span><span class="sxs-lookup"><span data-stu-id="39f99-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="39f99-116">URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39f99-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="39f99-117">Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39f99-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39f99-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="39f99-118">Child Elements</span></span>  
  
|<span data-ttu-id="39f99-119">Élément</span><span class="sxs-lookup"><span data-stu-id="39f99-119">Element</span></span>|<span data-ttu-id="39f99-120">Description</span><span class="sxs-lookup"><span data-stu-id="39f99-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f99-121">\<identité ></span><span class="sxs-lookup"><span data-stu-id="39f99-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="39f99-122">Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément.</span><span class="sxs-lookup"><span data-stu-id="39f99-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="39f99-123">Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="39f99-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="39f99-124">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="39f99-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="39f99-125">Collection d’en-têtes d’adresse utilisée pour les messages SOAP gérés par le programme de résolution d’homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39f99-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39f99-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="39f99-126">Parent Elements</span></span>  
  
|<span data-ttu-id="39f99-127">Élément</span><span class="sxs-lookup"><span data-stu-id="39f99-127">Element</span></span>|<span data-ttu-id="39f99-128">Description</span><span class="sxs-lookup"><span data-stu-id="39f99-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f99-129">\<programme de résolution ></span><span class="sxs-lookup"><span data-stu-id="39f99-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="39f99-130">Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="39f99-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f99-131">Notes</span><span class="sxs-lookup"><span data-stu-id="39f99-131">Remarks</span></span>  
 <span data-ttu-id="39f99-132">Cet élément définit les paramètres de base pour un service de programme de résolution d’homologue personnalisé, y compris l’adresse de point de terminaison de l’homologue qui héberge le service et tous les paramètres de liaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="39f99-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="39f99-133">Pour plus d’informations sur la création d’un programme de résolution personnalisé, consultez [Ajout d’un programme de résolution personnalisé à une Application PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="39f99-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f99-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39f99-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="39f99-135">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="39f99-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="39f99-136">Ajout d’un programme de résolution personnalisé à une Application PeerChannel</span><span class="sxs-lookup"><span data-stu-id="39f99-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
