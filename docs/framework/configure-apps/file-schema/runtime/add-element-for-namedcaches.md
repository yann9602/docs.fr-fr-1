---
title: "&lt;add&gt; (&#233;l&#233;ment de &lt;namedCaches&gt;) | Microsoft Docs"
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
  - "<add> (élément de <namedCaches>)"
  - "add (élément de <namedCaches>)"
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;add&gt; (&#233;l&#233;ment de &lt;namedCaches&gt;)
Ajoute une entrée `namedCache` à la collection `namedCaches` pour un cache mémoire.  
  
## Syntaxe  
  
```  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## Type  
 `None`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|||  
|-|-|  
|Attribut|Description|  
|`CacheMemoryLimitMegabytes`|Valeur entière qui spécifie la taille autorisée maximale \(en mégaoctets\) qu'une instance d'un objet <xref:System.Runtime.Caching.MemoryCache> peut atteindre.  La valeur par défaut est 0, ce qui signifie que l'heuristique de redimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`Name`|Nom du cache.|  
|`PhysicalMemoryLimitPercentage`|Valeur entière entre 0 et 100 qui spécifie le pourcentage maximal de mémoire de l'ordinateur physiquement installée qui peut être consommée par le cache.  La valeur par défaut est 0, ce qui signifie que l'heuristique de redimensionnement automatique de la classe <xref:System.Runtime.Caching.MemoryCache> est utilisée par défaut.|  
|`PollingInterval`|Valeur qui indique l'intervalle de temps à l'issue duquel l'implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et sous forme de pourcentage définies pour l'instance de cache.  Cette valeur est entrée au format « HH:MM:SS ».|  
  
### Éléments enfants  
 `None`  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour les instances <xref:System.Runtime.Caching.MemoryCache> nommées.|  
  
## Notes  
 L'élément `add` ajoute une entrée à la collection `namedCaches` pour un cache mémoire.  Vous pouvez utiliser l'élément [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) avant d'utiliser `add` pour garantir l'absence de tout autre cache nommé dans la collection.  Cet élément peut être utilisé dans les fichiers machine.config et Web.config.  
  
## Exemple  
 L'exemple suivant montre comment définir les paramètres de l'entrée `namedCache` par défaut sur la collection `namedCaches`  pour un cache mémoire.  
  
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
 [\<namedCaches\>, élément \(Paramètres de cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)