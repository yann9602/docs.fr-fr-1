---
title: "&lt;ajouter&gt; , élément pour &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0baafcb53bf79a25618dad56c2dcf1412e48624b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="9c2a3-102">&lt;ajouter&gt; , élément pour &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="9c2a3-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="9c2a3-103">Ajoute un `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="9c2a3-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="9c2a3-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="9c2a3-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="9c2a3-105">\<memoryCache></span></span>  
<span data-ttu-id="9c2a3-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="9c2a3-106">\<namedCaches></span></span>  
<span data-ttu-id="9c2a3-107">\<add></span><span class="sxs-lookup"><span data-stu-id="9c2a3-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2a3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c2a3-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9c2a3-109">Type</span><span class="sxs-lookup"><span data-stu-id="9c2a3-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c2a3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c2a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c2a3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c2a3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c2a3-112">Attributes</span></span>  
  
|<span data-ttu-id="9c2a3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9c2a3-113">Attribute</span></span>|<span data-ttu-id="9c2a3-114">Description</span><span class="sxs-lookup"><span data-stu-id="9c2a3-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="9c2a3-115">Valeur entière qui spécifie la taille maximale autorisée (en mégaoctets) qui une instance d’un <xref:System.Runtime.Caching.MemoryCache> peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="9c2a3-116">La valeur par défaut est 0, ce qui signifie que le <xref:System.Runtime.Caching.MemoryCache> heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="9c2a3-117">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="9c2a3-118">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire d’ordinateur physiquement installée qui peut être utilisé par le cache.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="9c2a3-119">La valeur par défaut est 0, ce qui signifie que le <xref:System.Runtime.Caching.MemoryCache> heuristiques de redimensionnement automatique de la classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="9c2a3-120">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="9c2a3-121">Cette valeur est entrée dans le format de « Hh : mm : ».</span><span class="sxs-lookup"><span data-stu-id="9c2a3-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c2a3-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c2a3-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9c2a3-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c2a3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9c2a3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="9c2a3-124">Element</span></span>|<span data-ttu-id="9c2a3-125">Description</span><span class="sxs-lookup"><span data-stu-id="9c2a3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c2a3-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="9c2a3-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="9c2a3-127">Contient une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c2a3-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c2a3-128">Remarks</span></span>  
 <span data-ttu-id="9c2a3-129">Le `add` élément ajoute une entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="9c2a3-130">Vous pouvez utiliser la [effacer](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) élément avant d’utiliser le `add` pour garantir qu’il n’existe aucun autre cache nommé dans la collection.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="9c2a3-131">Cet élément peut être utilisé dans le fichier machine.config et dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2a3-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c2a3-132">Example</span></span>  
 <span data-ttu-id="9c2a3-133">L’exemple suivant montre comment définir les paramètres de la valeur par défaut `namedCache` entrée à la `namedCaches` collection pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c2a3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c2a3-134">See Also</span></span>  
 [<span data-ttu-id="9c2a3-135">\<namedCaches >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="9c2a3-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
