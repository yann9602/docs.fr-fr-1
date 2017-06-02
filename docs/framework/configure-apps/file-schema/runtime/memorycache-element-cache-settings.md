---
title: "&lt;memoryCache&gt;, &#233;l&#233;ment (Param&#232;tres du cache) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<memoryCache> (élément)"
  - "mise en cache (.NET Framework), configuration"
  - "memoryCache (élément)"
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;memoryCache&gt;, &#233;l&#233;ment (Param&#232;tres du cache)
Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache>. La classe <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> définit un élément [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) que vous pouvez utiliser pour configurer le cache. Vous pouvez utiliser plusieurs instances de la classe <xref:System.Runtime.Caching.MemoryCache> dans une même application. Chaque élément `memoryCache` dans le fichier de configuration peut contenir des paramètres pour une instance <xref:System.Runtime.Caching.MemoryCache> nommée.  
  
 \<configuration\>  
\<system.runtime.caching\>  
\<memoryCache\>  
  
## Syntaxe  
  
```  
<memoryCache   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
< memoryCache />  
```  
  
## Type  
 Classe <xref:System.Runtime.Caching.MemoryCache>.  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Taille de mémoire maximale, en mégaoctets, que peut atteindre une instance d’un objet <xref:System.Runtime.Caching.MemoryCache>. La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`Name`|Nom de la configuration du cache.|  
|`PhysicalMemoryLimitPercentage`|Pourcentage de mémoire physique pouvant être utilisé par le cache. La valeur par défaut est 0, ce qui signifie que l’heuristique de dimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`PollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. La valeur est entrée au format « HH:MM:SS ».|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour l’instance `namedCache`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.runtime.caching\>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Contient des types qui vous permettent d’implémenter la mise en cache de sortie dans les applications intégrées au [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## Notes  
 La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation concrète de la classe <xref:System.Runtime.Caching.ObjectCache> abstraite. Les instances de la classe <xref:System.Runtime.Caching.MemoryCache> peuvent être fournies avec les informations de configuration tirées des fichiers de configuration d’application. La section de configuration [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) contient une collection de configurations `namedCaches`.  
  
 Quand un objet cache en mémoire est initialisé, il essaie tout d’abord de trouver une entrée `namedCaches` qui correspond au nom mentionné dans le paramètre passé au constructeur du cache mémoire. S’il trouve une entrée `namedCaches`, les informations de gestion de la mémoire et d’interrogation sont récupérées à partir du fichier de configuration.  
  
 Le processus d’initialisation détermine ensuite si des entrées de configuration ont été substituées, en utilisant la collection facultative de paires nom\/valeur d’informations de configuration dans le constructeur. Si vous passez l’une des valeurs suivantes dans la collection de paires nom\/valeur, ces valeurs remplacent les informations obtenues à partir du fichier de configuration :  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## Exemple  
 L’exemple suivant montre comment affecter le nom d’objet cache par défaut comme nom de l’objet <xref:System.Runtime.Caching.MemoryCache> en affectant la valeur « default » à l’attribut `name`.  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` prennent la valeur zéro. La définition de ces attributs sur zéro signifie que les heuristiques à dimensionnement automatique de <xref:System.Runtime.Caching.MemoryCache> sont utilisées par défaut. L’implémentation du cache doit comparer la charge de mémoire actuelle aux limites de mémoire en valeur absolue et en pourcentage toutes les deux minutes.  
  
```  
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
  
## Voir aussi  
 <xref:System.Runtime.Caching.MemoryCache>   
 [\<system.runtime.caching\>, éléments \(Paramètres du cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)   
 [\<namedCaches\>, élément \(Paramètres de cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)