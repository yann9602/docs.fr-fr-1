---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3782eb9cbe793fef450c8b1c58456a1d4f7b0b94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="8d17e-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="8d17e-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="8d17e-103">Spécifie l'URI pour lequel le canal de transport doit être créé.</span><span class="sxs-lookup"><span data-stu-id="8d17e-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="8d17e-104">Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="8d17e-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="8d17e-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8d17e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d17e-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="8d17e-106">\<behaviors></span></span>  
<span data-ttu-id="8d17e-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8d17e-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="8d17e-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="8d17e-108">\<behavior></span></span>  
<span data-ttu-id="8d17e-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="8d17e-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d17e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d17e-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d17e-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d17e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8d17e-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d17e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d17e-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d17e-113">Attributes</span></span>  
  
|<span data-ttu-id="8d17e-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d17e-114">Attribute</span></span>|<span data-ttu-id="8d17e-115">Description</span><span class="sxs-lookup"><span data-stu-id="8d17e-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="8d17e-116">Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.</span><span class="sxs-lookup"><span data-stu-id="8d17e-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d17e-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d17e-117">Child Elements</span></span>  
 <span data-ttu-id="8d17e-118">None</span><span class="sxs-lookup"><span data-stu-id="8d17e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d17e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d17e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d17e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8d17e-120">Element</span></span>|<span data-ttu-id="8d17e-121">Description</span><span class="sxs-lookup"><span data-stu-id="8d17e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d17e-122">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="8d17e-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8d17e-123">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8d17e-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d17e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d17e-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
