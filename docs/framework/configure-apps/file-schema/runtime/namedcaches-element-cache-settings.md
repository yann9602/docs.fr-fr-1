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
ms.openlocfilehash: 7c25f0039f75ba1c736cff946dbaaff9252dc93e
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; élément (paramètres de Cache)
Spécifie une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances. Le <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriété fait référence à la collection de paramètres de configuration à partir d’un ou plusieurs `namedCaches` éléments du fichier de configuration.  
  
 \<configuration>  
\<System.Runtime.Caching >  
\<memoryCache >  
\<namedCaches >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Valeur entière qui spécifie la taille maximale autorisée, en mégaoctets, qui une instance d’un <xref:System.Runtime.Caching.MemoryCache> peut atteindre. La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées par défaut.|  
|`name`|Nom du cache.|  
|`physicalMemoryLimitPercentage`|Valeur entière comprise entre 0 et 100 qui spécifie le pourcentage maximal de mémoire d’ordinateur physiquement installée qui peut être utilisé par le cache. La valeur par défaut est 0, ce qui signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées par défaut.|  
|`pollingInterval`|Valeur qui indique l’intervalle de temps après lequel l’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage définies pour l’instance de cache. Cette valeur est entrée dans le format de « Hh : mm : ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|  
  
## <a name="remarks"></a>Notes  
 La section de configuration du cache mémoire du fichier Web.config peut contenir `add`, `remove`, et `clear` d’attributs pour le `namedCaches` collection. Chaque `namedCaches` entrée est identifiée par le `name` attribut.  
  
 Vous pouvez récupérer des instances d’entrées de cache mémoire en référençant les informations contenues dans les fichiers de configuration d’application. Par défaut, seule l’instance de cache par défaut a une entrée dans le fichier de configuration. L’instance de cache par défaut est l’instance qui est retourné à partir de la <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriété.  
  
 Si vous définissez l’attribut de nom par « default », l’élément utilise l’instance de cache mémoire par défaut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir le nom du cache sur le nom d’entrée de cache par défaut en définissant le `name` attribut la valeur « default ».  
  
 Les attributs `cacheMemoryLimitMegabytes` et `physicalMemoryPercentage` sont définis sur zéro. Si vous définissez ces attributs zéro signifie que l’heuristique de redimensionnement automatique de la <xref:System.Runtime.Caching.MemoryCache> classe sont utilisées. L’implémentation de cache compare la charge de mémoire actuelle aux limites de mémoire absolue et en pourcentage toutes les deux minutes.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<memoryCache >, élément (paramètres de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
