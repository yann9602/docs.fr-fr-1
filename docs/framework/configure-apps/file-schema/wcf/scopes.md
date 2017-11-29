---
title: "&lt;étendues&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b35696cbecb0badf397d6d48e7c97aae3d0232e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="845ca-102">&lt;étendues&gt;</span><span class="sxs-lookup"><span data-stu-id="845ca-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="845ca-103">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="845ca-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="845ca-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="845ca-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="845ca-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="845ca-105">\<behaviors></span></span>  
<span data-ttu-id="845ca-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="845ca-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="845ca-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="845ca-107">\<behavior></span></span>  
<span data-ttu-id="845ca-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="845ca-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="845ca-109">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="845ca-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="845ca-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="845ca-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="845ca-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="845ca-111">Attributes and Elements</span></span>  
 <span data-ttu-id="845ca-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="845ca-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="845ca-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="845ca-113">Attributes</span></span>  
 <span data-ttu-id="845ca-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="845ca-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="845ca-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="845ca-115">Child Elements</span></span>  
  
|<span data-ttu-id="845ca-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="845ca-116">Attribute</span></span>|<span data-ttu-id="845ca-117">Description</span><span class="sxs-lookup"><span data-stu-id="845ca-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="845ca-118">\<add></span><span class="sxs-lookup"><span data-stu-id="845ca-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="845ca-119">Ajoute les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="845ca-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="845ca-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="845ca-120">Parent Elements</span></span>  
  
|<span data-ttu-id="845ca-121">Élément</span><span class="sxs-lookup"><span data-stu-id="845ca-121">Element</span></span>|<span data-ttu-id="845ca-122">Description</span><span class="sxs-lookup"><span data-stu-id="845ca-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="845ca-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="845ca-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="845ca-124">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="845ca-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="845ca-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="845ca-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
