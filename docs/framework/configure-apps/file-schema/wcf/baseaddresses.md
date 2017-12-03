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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe66b499eb50a058ed8b6a46769893f6dc5fd6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="ed4db-102">&lt;adresses de base&gt;</span><span class="sxs-lookup"><span data-stu-id="ed4db-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="ed4db-103">Représente une collection d'éléments `baseAddress`, qui sont les adresses de base d'un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="ed4db-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="ed4db-104">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="ed4db-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="ed4db-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ed4db-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed4db-106">\<client ></span><span class="sxs-lookup"><span data-stu-id="ed4db-106">\<client></span></span>  
<span data-ttu-id="ed4db-107">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="ed4db-107">\<endpoint></span></span>  
<span data-ttu-id="ed4db-108">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="ed4db-108">\<host></span></span>  
<span data-ttu-id="ed4db-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ed4db-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed4db-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed4db-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="ed4db-111">Type</span><span class="sxs-lookup"><span data-stu-id="ed4db-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed4db-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ed4db-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ed4db-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ed4db-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed4db-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ed4db-114">Attributes</span></span>  
 <span data-ttu-id="ed4db-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="ed4db-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed4db-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ed4db-116">Child Elements</span></span>  
  
|<span data-ttu-id="ed4db-117">Élément</span><span class="sxs-lookup"><span data-stu-id="ed4db-117">Element</span></span>|<span data-ttu-id="ed4db-118">Description</span><span class="sxs-lookup"><span data-stu-id="ed4db-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed4db-119">\<add></span><span class="sxs-lookup"><span data-stu-id="ed4db-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="ed4db-120">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ed4db-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed4db-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ed4db-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ed4db-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ed4db-122">Element</span></span>|<span data-ttu-id="ed4db-123">Description</span><span class="sxs-lookup"><span data-stu-id="ed4db-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed4db-124">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="ed4db-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="ed4db-125">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ed4db-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed4db-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed4db-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="ed4db-127">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="ed4db-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
