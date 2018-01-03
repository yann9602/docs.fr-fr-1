---
title: '&lt;add&gt; de &lt;baseAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516c615248c95ef3107664b996f457fb80b46373
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="c28a0-102">&lt;add&gt; de &lt;baseAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="c28a0-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="c28a0-103">Représente un élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c28a0-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="c28a0-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c28a0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c28a0-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="c28a0-105">\<client></span></span>  
<span data-ttu-id="c28a0-106">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="c28a0-106">\<endpoint></span></span>  
<span data-ttu-id="c28a0-107">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="c28a0-107">\<host></span></span>  
<span data-ttu-id="c28a0-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="c28a0-108">\<baseAddresses></span></span>  
<span data-ttu-id="c28a0-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="c28a0-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28a0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c28a0-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="c28a0-111">Type</span><span class="sxs-lookup"><span data-stu-id="c28a0-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c28a0-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c28a0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c28a0-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c28a0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c28a0-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="c28a0-114">Attributes</span></span>  
  
|<span data-ttu-id="c28a0-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="c28a0-115">Attribute</span></span>|<span data-ttu-id="c28a0-116">Description</span><span class="sxs-lookup"><span data-stu-id="c28a0-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="c28a0-117">Chaîne indiquant une adresse de base utilisée par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c28a0-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c28a0-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c28a0-118">Child Elements</span></span>  
 <span data-ttu-id="c28a0-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c28a0-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c28a0-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c28a0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c28a0-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c28a0-121">Element</span></span>|<span data-ttu-id="c28a0-122">Description</span><span class="sxs-lookup"><span data-stu-id="c28a0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c28a0-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="c28a0-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="c28a0-124">Collection d'éléments `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="c28a0-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c28a0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c28a0-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="c28a0-126">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="c28a0-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
