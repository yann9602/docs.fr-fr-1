---
title: "&lt;remove&gt;, &#233;l&#233;ment de &lt;namedCaches&gt; | Microsoft Docs"
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
  - "<remove> (élément de namedCaches)"
  - "remove (élément de namedCaches)"
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;remove&gt;, &#233;l&#233;ment de &lt;namedCaches&gt;
Supprime une entrée de cache nommée de la collection `namedCaches` pour un cache mémoire.  
  
## Syntaxe  
  
```  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## Type  
 `None`  
  
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
 L'élément `remove` supprime une entrée `namedCache` de la collection de caches nommée pour un cache en mémoire.  
  
## Voir aussi  
 [\<namedCaches\>, élément \(Paramètres de cache\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)