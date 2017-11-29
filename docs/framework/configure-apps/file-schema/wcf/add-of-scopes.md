---
title: '&lt;add&gt; de &lt;scopes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="5aa60-102">&lt;add&gt; de &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="5aa60-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="5aa60-103">Ajoute un URI de portée personnalisé qui permet de filtrer les points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="5aa60-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="5aa60-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5aa60-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5aa60-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="5aa60-105">\<behaviors></span></span>  
<span data-ttu-id="5aa60-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5aa60-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5aa60-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="5aa60-107">\<behavior></span></span>  
<span data-ttu-id="5aa60-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="5aa60-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="5aa60-109">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="5aa60-109">\<scopes></span></span>  
<span data-ttu-id="5aa60-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5aa60-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa60-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa60-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa60-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5aa60-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5aa60-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5aa60-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa60-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5aa60-114">Attributes</span></span>  
  
|<span data-ttu-id="5aa60-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="5aa60-115">Attribute</span></span>|<span data-ttu-id="5aa60-116">Description</span><span class="sxs-lookup"><span data-stu-id="5aa60-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5aa60-117">portée</span><span class="sxs-lookup"><span data-stu-id="5aa60-117">scope</span></span>|<span data-ttu-id="5aa60-118">URI qui contient les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="5aa60-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa60-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5aa60-119">Child Elements</span></span>  
 <span data-ttu-id="5aa60-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5aa60-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5aa60-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5aa60-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5aa60-122">Élément</span><span class="sxs-lookup"><span data-stu-id="5aa60-122">Element</span></span>|<span data-ttu-id="5aa60-123">Description</span><span class="sxs-lookup"><span data-stu-id="5aa60-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aa60-124">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="5aa60-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="5aa60-125">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="5aa60-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5aa60-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aa60-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
