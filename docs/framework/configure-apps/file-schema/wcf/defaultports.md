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
ms.workload: dotnet
ms.openlocfilehash: dd4fba4d7d5bcb0adc5a1a638598af2746ad4cf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="60eef-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="60eef-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="60eef-103">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="60eef-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="60eef-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="60eef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="60eef-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="60eef-105">\<behaviors></span></span>  
<span data-ttu-id="60eef-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="60eef-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="60eef-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="60eef-107">\<behavior></span></span>  
<span data-ttu-id="60eef-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="60eef-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="60eef-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="60eef-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60eef-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60eef-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60eef-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="60eef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60eef-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="60eef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60eef-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="60eef-113">Attributes</span></span>  
 <span data-ttu-id="60eef-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="60eef-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60eef-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60eef-115">Child Elements</span></span>  
  
|<span data-ttu-id="60eef-116">Élément</span><span class="sxs-lookup"><span data-stu-id="60eef-116">Element</span></span>|<span data-ttu-id="60eef-117">Description</span><span class="sxs-lookup"><span data-stu-id="60eef-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60eef-118">\<Ajouter > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="60eef-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="60eef-119">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="60eef-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60eef-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="60eef-120">Parent Elements</span></span>  
  
|<span data-ttu-id="60eef-121">Élément</span><span class="sxs-lookup"><span data-stu-id="60eef-121">Element</span></span>|<span data-ttu-id="60eef-122">Description</span><span class="sxs-lookup"><span data-stu-id="60eef-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60eef-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="60eef-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="60eef-124">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="60eef-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60eef-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60eef-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
