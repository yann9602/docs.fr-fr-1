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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 012d86297f75874b57231d7c347c7412ad04aa1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="c14de-102">&lt;add&gt; de &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="c14de-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="c14de-103">Ajoute un URI de portée personnalisé qui permet de filtrer les points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="c14de-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="c14de-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c14de-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c14de-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="c14de-105">\<behaviors></span></span>  
<span data-ttu-id="c14de-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c14de-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c14de-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c14de-107">\<behavior></span></span>  
<span data-ttu-id="c14de-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c14de-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="c14de-109">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="c14de-109">\<scopes></span></span>  
<span data-ttu-id="c14de-110">\<add></span><span class="sxs-lookup"><span data-stu-id="c14de-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14de-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c14de-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c14de-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c14de-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c14de-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c14de-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c14de-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="c14de-114">Attributes</span></span>  
  
|<span data-ttu-id="c14de-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="c14de-115">Attribute</span></span>|<span data-ttu-id="c14de-116">Description</span><span class="sxs-lookup"><span data-stu-id="c14de-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c14de-117">portée</span><span class="sxs-lookup"><span data-stu-id="c14de-117">scope</span></span>|<span data-ttu-id="c14de-118">URI qui contient les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="c14de-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c14de-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c14de-119">Child Elements</span></span>  
 <span data-ttu-id="c14de-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c14de-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c14de-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c14de-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c14de-122">Élément</span><span class="sxs-lookup"><span data-stu-id="c14de-122">Element</span></span>|<span data-ttu-id="c14de-123">Description</span><span class="sxs-lookup"><span data-stu-id="c14de-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c14de-124">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="c14de-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="c14de-125">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="c14de-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c14de-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c14de-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
