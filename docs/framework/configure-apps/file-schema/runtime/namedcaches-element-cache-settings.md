---
title: "&lt;namedCaches&gt; élément (paramètres de Cache)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f4c4bd9901b053c96a260435c34ffa3ddd2c7283
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="57dff-102">&lt;namedCaches&gt; élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="57dff-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="57dff-103">Spécifie une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances.</span><span class="sxs-lookup"><span data-stu-id="57dff-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="57dff-104">Le <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration à partir d’un ou plusieurs `namedCaches` éléments du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="57dff-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="57dff-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="57dff-105">\<configuration></span></span>  
<span data-ttu-id="57dff-106">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="57dff-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="57dff-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="57dff-107">\<memoryCache></span></span>  
<span data-ttu-id="57dff-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="57dff-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57dff-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57dff-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="57dff-110">Type</span><span class="sxs-lookup"><span data-stu-id="57dff-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57dff-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="57dff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="57dff-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="57dff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57dff-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="57dff-113">Attributes</span></span>  
  
|<span data-ttu-id="57dff-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="57dff-114">Attribute</span></span>|<span data-ttu-id="57dff-115">Description</span><span class="sxs-lookup"><span data-stu-id="57dff-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="57dff-116">Valeur entière qui spécifie la taille maximale autorisée, en mégaoctets, qui une instance d’un <xref:System.Runtime.Caching.MemoryCache> peut atteindre.</span><span class="sxs-lookup"><span data-stu-id="57dff-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="57dff-117">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="57dff-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="57dff-118">Nom du cache.</span><span class="sxs-lookup"><span data-stu-id="57dff-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="57dff-119">Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire d’ordinateur physiquement installée qui peut être utilisé par le cache.</span><span class="sxs-lookup"><span data-stu-id="57dff-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="57dff-120">La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="57dff-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="57dff-121">Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache.</span><span class="sxs-lookup"><span data-stu-id="57dff-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="57dff-122">Cette valeur est entrée dans le format de « Hh : mm : ».</span><span class="sxs-lookup"><span data-stu-id="57dff-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57dff-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="57dff-123">Child Elements</span></span>  
  
|<span data-ttu-id="57dff-124">Élément</span><span class="sxs-lookup"><span data-stu-id="57dff-124">Element</span></span>|<span data-ttu-id="57dff-125">Description</span><span class="sxs-lookup"><span data-stu-id="57dff-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dff-126">\<add></span><span class="sxs-lookup"><span data-stu-id="57dff-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="57dff-127">Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="57dff-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="57dff-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="57dff-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="57dff-129">Efface la collection `namedCaches` pour un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="57dff-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="57dff-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="57dff-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="57dff-131">Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.</span><span class="sxs-lookup"><span data-stu-id="57dff-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57dff-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="57dff-132">Parent Elements</span></span>  
  
|<span data-ttu-id="57dff-133">Élément</span><span class="sxs-lookup"><span data-stu-id="57dff-133">Element</span></span>|<span data-ttu-id="57dff-134">Description</span><span class="sxs-lookup"><span data-stu-id="57dff-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dff-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="57dff-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="57dff-136">Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="57dff-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57dff-137">Notes</span><span class="sxs-lookup"><span data-stu-id="57dff-137">Remarks</span></span>  
 <span data-ttu-id="57dff-138">La section de configuration du cache mémoire du fichier Web.config peut contenir `add`, `remove`, et `clear` d’attributs pour le `namedCaches` collection.</span><span class="sxs-lookup"><span data-stu-id="57dff-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="57dff-139">Chaque `namedCaches` entrée est identifiée par le `name` attribut.</span><span class="sxs-lookup"><span data-stu-id="57dff-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="57dff-140">Vous pouvez récupérer des instances d’entrées de cache mémoire en référençant les informations contenues dans les fichiers de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="57dff-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="57dff-141">Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="57dff-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="57dff-142">L’instance de cache par défaut est l’instance qui est retourné à partir de la <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="57dff-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="57dff-143">Si vous définissez l’attribut de nom par « default », l’élément utilise l’instance de cache mémoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="57dff-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57dff-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="57dff-144">Example</span></span>  
 <span data-ttu-id="57dff-145">L’exemple suivant montre comment définir le nom du cache sur le nom d’entrée de cache par défaut en définissant le `name` attribut la valeur « default ».</span><span class="sxs-lookup"><span data-stu-id="57dff-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="57dff-146">Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="57dff-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="57dff-147">Si vous définissez ces attributs zéro signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="57dff-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="57dff-148">L’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage toutes les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="57dff-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57dff-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57dff-149">See Also</span></span>  
 [<span data-ttu-id="57dff-150">\<memoryCache >, élément (paramètres de Cache)</span><span class="sxs-lookup"><span data-stu-id="57dff-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
