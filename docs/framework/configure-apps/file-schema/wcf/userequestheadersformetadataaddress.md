---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="d39b7-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="d39b7-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="d39b7-103">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="d39b7-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="d39b7-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d39b7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d39b7-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="d39b7-105">\<behaviors></span></span>  
<span data-ttu-id="d39b7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d39b7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d39b7-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="d39b7-107">\<behavior></span></span>  
<span data-ttu-id="d39b7-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="d39b7-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39b7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d39b7-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d39b7-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d39b7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d39b7-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d39b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d39b7-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d39b7-112">Attributes</span></span>  
 <span data-ttu-id="d39b7-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="d39b7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d39b7-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d39b7-114">Child Elements</span></span>  
  
|<span data-ttu-id="d39b7-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d39b7-115">Element</span></span>|<span data-ttu-id="d39b7-116">Description</span><span class="sxs-lookup"><span data-stu-id="d39b7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d39b7-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="d39b7-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="d39b7-118">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="d39b7-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d39b7-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d39b7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d39b7-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d39b7-120">Element</span></span>|<span data-ttu-id="d39b7-121">Description</span><span class="sxs-lookup"><span data-stu-id="d39b7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d39b7-122">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="d39b7-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d39b7-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="d39b7-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d39b7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d39b7-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
