---
title: "&lt;supprimer&gt; , élément pour &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="aab66-102">&lt;supprimer&gt; , élément pour &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="aab66-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="aab66-103">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="aab66-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="aab66-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="aab66-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="aab66-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="aab66-105">\<memoryCache></span></span>  
<span data-ttu-id="aab66-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="aab66-106">\<namedCaches></span></span>  
<span data-ttu-id="aab66-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="aab66-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aab66-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aab66-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="aab66-109">Type</span><span class="sxs-lookup"><span data-stu-id="aab66-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aab66-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aab66-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aab66-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aab66-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aab66-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="aab66-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="aab66-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aab66-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="aab66-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aab66-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aab66-115">Élément</span><span class="sxs-lookup"><span data-stu-id="aab66-115">Element</span></span>|<span data-ttu-id="aab66-116">Description</span><span class="sxs-lookup"><span data-stu-id="aab66-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aab66-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aab66-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="aab66-118">Contient une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances.</span><span class="sxs-lookup"><span data-stu-id="aab66-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aab66-119">Notes</span><span class="sxs-lookup"><span data-stu-id="aab66-119">Remarks</span></span>  
 <span data-ttu-id="aab66-120">Le `remove` élément supprime un `namedCache` entrée à partir de la collection de cache nommé pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="aab66-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab66-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aab66-121">See Also</span></span>  
 [<span data-ttu-id="aab66-122">\<namedCaches >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="aab66-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
