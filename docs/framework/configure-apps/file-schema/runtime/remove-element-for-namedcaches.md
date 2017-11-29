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
ms.openlocfilehash: 6170b59e87948225708c9e697cba1542d756d2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="14cae-102">&lt;supprimer&gt; , élément pour &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="14cae-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="14cae-103">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="14cae-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="14cae-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="14cae-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="14cae-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="14cae-105">\<memoryCache></span></span>  
<span data-ttu-id="14cae-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="14cae-106">\<namedCaches></span></span>  
<span data-ttu-id="14cae-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="14cae-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14cae-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14cae-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="14cae-109">Type</span><span class="sxs-lookup"><span data-stu-id="14cae-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14cae-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14cae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14cae-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14cae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14cae-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="14cae-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="14cae-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14cae-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="14cae-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14cae-114">Parent Elements</span></span>  
  
|<span data-ttu-id="14cae-115">Élément</span><span class="sxs-lookup"><span data-stu-id="14cae-115">Element</span></span>|<span data-ttu-id="14cae-116">Description</span><span class="sxs-lookup"><span data-stu-id="14cae-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14cae-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="14cae-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="14cae-118">Contient une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances.</span><span class="sxs-lookup"><span data-stu-id="14cae-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14cae-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="14cae-119">Remarks</span></span>  
 <span data-ttu-id="14cae-120">Le `remove` élément supprime un `namedCache` entrée à partir de la collection de cache nommé pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="14cae-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cae-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14cae-121">See Also</span></span>  
 [<span data-ttu-id="14cae-122">\<namedCaches >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="14cae-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
