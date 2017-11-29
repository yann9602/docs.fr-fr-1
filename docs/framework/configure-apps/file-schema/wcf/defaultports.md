---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="29f7b-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="29f7b-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="29f7b-103">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="29f7b-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="29f7b-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29f7b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="29f7b-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="29f7b-105">\<behaviors></span></span>  
<span data-ttu-id="29f7b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="29f7b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="29f7b-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="29f7b-107">\<behavior></span></span>  
<span data-ttu-id="29f7b-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="29f7b-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="29f7b-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="29f7b-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f7b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f7b-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29f7b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29f7b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="29f7b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="29f7b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29f7b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="29f7b-113">Attributes</span></span>  
 <span data-ttu-id="29f7b-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="29f7b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29f7b-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29f7b-115">Child Elements</span></span>  
  
|<span data-ttu-id="29f7b-116">Élément</span><span class="sxs-lookup"><span data-stu-id="29f7b-116">Element</span></span>|<span data-ttu-id="29f7b-117">Description</span><span class="sxs-lookup"><span data-stu-id="29f7b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29f7b-118">\<Ajouter > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="29f7b-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="29f7b-119">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="29f7b-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29f7b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29f7b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="29f7b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="29f7b-121">Element</span></span>|<span data-ttu-id="29f7b-122">Description</span><span class="sxs-lookup"><span data-stu-id="29f7b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29f7b-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="29f7b-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="29f7b-124">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="29f7b-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29f7b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f7b-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
