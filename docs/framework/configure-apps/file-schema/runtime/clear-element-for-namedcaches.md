---
title: "&lt;clear&gt;, &#233;l&#233;ment de &lt;namedCaches&gt; | Microsoft Docs"
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
  - "<clear> (élément de <namedCaches>)"
  - "clear (élément de <namedCaches>)"
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;clear&gt;, &#233;l&#233;ment de &lt;namedCaches&gt;
Efface toutes les entrées `namedCache` dans la collection `namedCaches` pour un cache mémoire.  
  
## Syntaxe  
  
```  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 `None`  
  
### Éléments enfants  
 `None`  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour les instances <xref:System.Runtime.Caching.MemoryCache> nommées.|  
  
## Notes  
 L'élément `clear` efface toutes les entrées `namedCache` dans la collection de caches nommée pour un cache mémoire.  Vous pouvez utiliser l'élément `clear` avant d'utiliser l'élément `add` pour ajouter une nouvelle entrée du cache nommée, pour être sûr qu'il n'existe aucun autre cache nommé dans la collection.  
  
## Voir aussi  
 [\<namedCaches\>, élément \(Paramètres de cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)