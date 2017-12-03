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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1886f6efdfaa8f4105e6ef16ad72093867e0f3fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="4b9f2-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="4b9f2-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="4b9f2-103">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="4b9f2-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="4b9f2-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b9f2-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-105">\<behaviors></span></span>  
<span data-ttu-id="4b9f2-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4b9f2-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-107">\<behavior></span></span>  
<span data-ttu-id="4b9f2-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="4b9f2-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9f2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b9f2-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b9f2-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4b9f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4b9f2-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4b9f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b9f2-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="4b9f2-113">Attributes</span></span>  
 <span data-ttu-id="4b9f2-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="4b9f2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b9f2-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4b9f2-115">Child Elements</span></span>  
  
|<span data-ttu-id="4b9f2-116">Élément</span><span class="sxs-lookup"><span data-stu-id="4b9f2-116">Element</span></span>|<span data-ttu-id="4b9f2-117">Description</span><span class="sxs-lookup"><span data-stu-id="4b9f2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b9f2-118">\<Ajouter > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="4b9f2-119">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="4b9f2-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b9f2-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4b9f2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4b9f2-121">Élément</span><span class="sxs-lookup"><span data-stu-id="4b9f2-121">Element</span></span>|<span data-ttu-id="4b9f2-122">Description</span><span class="sxs-lookup"><span data-stu-id="4b9f2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b9f2-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="4b9f2-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="4b9f2-124">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b9f2-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b9f2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b9f2-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
