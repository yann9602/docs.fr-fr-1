---
title: "&lt;namedCaches&gt;, &#233;l&#233;ment (Param&#232;tres de cache) | Microsoft Docs"
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
  - "<namedCaches> (élément)"
  - "mise en cache (.NET Framework), configuration"
  - "namedCaches (élément)"
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;namedCaches&gt;, &#233;l&#233;ment (Param&#232;tres de cache)
Spécifie une collection de paramètres de configuration pour les instances <xref:System.Runtime.Caching.MemoryCache> nommées.  La propriété <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> référence la collection de paramètres de configuration d'un ou plusieurs éléments `namedCaches` du fichier de configuration.  
  
## Syntaxe  
  
```  
<namedCaches>  
  <add name="default"   
</namedCaches>  
```  
  
## Type  
 `None`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Valeur entière qui spécifie la taille autorisée maximale, en mégaoctets, qu'une instance d'un objet <xref:System.Runtime.Caching.MemoryCache> peut atteindre.  La valeur par défaut est 0, ce qui signifie que l'heuristique de redimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`Name`|Nom du cache.|  
|`PhysicalMemoryLimitPercentage`|Valeur entière entre 0 et 100 qui spécifie le pourcentage maximal de mémoire de l'ordinateur physiquement installée qui peut être consommée par le cache.  La valeur par défaut est 0, ce qui signifie que l'heuristique de redimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`PollingInterval`|Valeur qui indique l'intervalle de temps à l'issue duquel l'implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et sous forme de pourcentage définies pour l'instance de cache.  Cette valeur est entrée au format « HH:MM:SS ».|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` pour un cache mémoire.|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Supprime une entrée de cache nommée de la collection `namedCaches` pour un cache mémoire.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<memoryCache\>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
## Notes  
 La section de configuration du cache mémoire du fichier Web.config peut contenir les attributs `add`, `remove` et `clear` pour la collection `namedCaches`.  Chaque entrée `namedCaches` est identifiée uniquement par l'attribut de `name`.  
  
 Vous pouvez extraire des instances d'entrées de cache mémoire en référençant les informations dans les fichiers de configuration de l'application.  Par défaut, seule l'instance de cache par défaut a une entrée dans le fichier de configuration.  L'instance de cache par défaut est l'instance retournée à partir de la propriété <xref:System.Runtime.Caching.MemoryCache.Default%2A>.  
  
 Si vous affectez la valeur  « par défaut » à l'attribut de nom, l'élément utilise l'instance de cache mémoire par défaut.  
  
## Exemple  
 L'exemple suivant montre comment affecter au cache le nom d'entrée de cache par défaut en donnant à l'attribut `name` la valeur « par défaut ».  
  
 La valeur des attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` est définie à zéro.  Si ces attributs sont définis sur zéro, les méthodes heuristiques de redimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> sont utilisées.  L'implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et sous forme de pourcentage toutes les deux minutes.  
  
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
 [\<memoryCache\>, élément \(Paramètres du cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)