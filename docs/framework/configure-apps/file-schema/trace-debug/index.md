---
title: "Sch&#233;ma des param&#232;tres de tra&#231;age et de d&#233;bogage | Microsoft Docs"
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
  - "schéma de configuration (.NET Framework), paramètres de traçage et de débogage"
  - "sections de configuration (.NET Framework)"
  - "paramètres de configuration (.NET Framework), débogage"
  - "paramètres de configuration (.NET Framework), traçage"
  - "éléments (.NET Framework), paramètres de traçage et de débogage"
  - "paramètres de configuration (schéma)"
  - "écouteurs de traçage, schéma des paramètres de traçage et de débogage"
  - "traçage (.NET Framework), schéma des paramètres de traçage et de débogage"
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# Sch&#233;ma des param&#232;tres de tra&#231;age et de d&#233;bogage
Les paramètres de traçage et de débogage spécifient les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.  
  
 Le tableau suivant décrit la fonction de chaque élément des paramètres de trace et de débogage.  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Ajoute un écouteur à la collection `Listeners` pour une source de trace.|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Ajoute un écouteur à la collection `sharedListeners`.|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Spécifie le niveau auquel un commutateur de traçage est défini.|  
|[\<assert\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Spécifie s'il convient d'afficher une boîte de message lorsque vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ; spécifie également le nom du fichier dans lequel écrire les messages.|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Efface le contenu de la collection `Listeners` pour une source de trace.|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Efface le contenu de la collection `Listeners` de l'élément trace.|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` de la trace.|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Ajoute un filtre à un écouteur de la collection `sharedListeners`.|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Spécifie des écouteurs pour la collection `Listeners` pour une source de trace.|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Spécifie des écouteurs pour la collection `Listeners` de la trace.|  
|[\<performanceCounters\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Spécifie la taille de la mémoire globale partagée par les compteurs de performance.|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Supprime un écouteur de la collection `Listeners` de la trace.|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Supprime un écouteur de la collection `Listeners` pour une source de trace.|  
|[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Contient des écouteurs qui peuvent être référencés par n'importe quel élément trace ou source.|  
|[\<sources\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Contient des sources de trace qui initient des messages de traçage.|  
|[\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Spécifie une source de trace qui initie le traçage des messages.|  
|[\<switches\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Contient des commutateurs de traçage et le niveau auquel les commutateurs de traçage sont définis.|  
|[\<system.diagnostics\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|[\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Contient des écouteurs qui collectent, stockent et routent des messages de traçage.|  
  
## Voir aussi  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.Debug>   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)