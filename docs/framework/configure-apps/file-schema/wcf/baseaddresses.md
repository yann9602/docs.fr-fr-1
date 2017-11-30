---
title: '&lt;adresses de base&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bf698b64b528b0ea109223a2d94e6725c8ce6b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="e13b4-102">&lt;adresses de base&gt;</span><span class="sxs-lookup"><span data-stu-id="e13b4-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="e13b4-103">Représente une collection d'éléments `baseAddress`, qui sont les adresses de base d'un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="e13b4-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="e13b4-104">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="e13b4-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="e13b4-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e13b4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e13b4-106">\<client ></span><span class="sxs-lookup"><span data-stu-id="e13b4-106">\<client></span></span>  
<span data-ttu-id="e13b4-107">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="e13b4-107">\<endpoint></span></span>  
<span data-ttu-id="e13b4-108">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="e13b4-108">\<host></span></span>  
<span data-ttu-id="e13b4-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e13b4-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13b4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e13b4-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="e13b4-111">Type</span><span class="sxs-lookup"><span data-stu-id="e13b4-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e13b4-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e13b4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e13b4-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e13b4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e13b4-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="e13b4-114">Attributes</span></span>  
 <span data-ttu-id="e13b4-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="e13b4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e13b4-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e13b4-116">Child Elements</span></span>  
  
|<span data-ttu-id="e13b4-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e13b4-117">Element</span></span>|<span data-ttu-id="e13b4-118">Description</span><span class="sxs-lookup"><span data-stu-id="e13b4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e13b4-119">\<add></span><span class="sxs-lookup"><span data-stu-id="e13b4-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="e13b4-120">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e13b4-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e13b4-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e13b4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e13b4-122">Élément</span><span class="sxs-lookup"><span data-stu-id="e13b4-122">Element</span></span>|<span data-ttu-id="e13b4-123">Description</span><span class="sxs-lookup"><span data-stu-id="e13b4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e13b4-124">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="e13b4-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e13b4-125">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e13b4-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e13b4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e13b4-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="e13b4-127">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="e13b4-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
