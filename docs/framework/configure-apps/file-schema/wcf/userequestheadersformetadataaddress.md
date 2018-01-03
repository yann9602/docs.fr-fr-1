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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94dafcfa68463a0e82696cf16a96abe45632e72a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="9b157-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="9b157-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="9b157-103">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="9b157-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="9b157-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9b157-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9b157-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="9b157-105">\<behaviors></span></span>  
<span data-ttu-id="9b157-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9b157-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9b157-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="9b157-107">\<behavior></span></span>  
<span data-ttu-id="9b157-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="9b157-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b157-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b157-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b157-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b157-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b157-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9b157-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b157-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b157-112">Attributes</span></span>  
 <span data-ttu-id="9b157-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b157-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b157-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b157-114">Child Elements</span></span>  
  
|<span data-ttu-id="9b157-115">Élément</span><span class="sxs-lookup"><span data-stu-id="9b157-115">Element</span></span>|<span data-ttu-id="9b157-116">Description</span><span class="sxs-lookup"><span data-stu-id="9b157-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b157-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="9b157-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="9b157-118">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="9b157-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b157-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b157-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9b157-120">Élément</span><span class="sxs-lookup"><span data-stu-id="9b157-120">Element</span></span>|<span data-ttu-id="9b157-121">Description</span><span class="sxs-lookup"><span data-stu-id="9b157-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b157-122">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="9b157-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9b157-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="9b157-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b157-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b157-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
