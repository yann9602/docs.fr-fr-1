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
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;supprimer&gt; , élément pour &lt;namedCaches&gt;
Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.  
  
 \<System.Runtime.Caching >  
\<memoryCache >  
\<namedCaches >  
\<Supprimer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 `None`  
  
### <a name="child-elements"></a>Éléments enfants  
 `None`  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour le nommé <xref:System.Runtime.Caching.MemoryCache> instances.|  
  
## <a name="remarks"></a>Remarques  
 Le `remove` élément supprime un `namedCache` entrée à partir de la collection de cache nommé pour un cache mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [\<namedCaches >, élément (paramètres de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
