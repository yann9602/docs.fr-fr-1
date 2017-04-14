---
title: "&lt;performanceCounters&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<perfomanceCounters> (élément)"
  - "performanceCounters (élément)"
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;performanceCounters&gt;, &#233;l&#233;ment
Spécifie la taille de la mémoire globale partagée par les compteurs de performance.  
  
## Syntaxe  
  
```  
<performanceCounters filemappingsize="524288" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|filemappingsize|Attribut requis.<br /><br /> Spécifie la taille, en octets, de la mémoire globale partagée par les compteurs de performance.  La valeur par défaut est 524288.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## Notes  
 Les compteurs de performance utilisent un fichier mappé en mémoire, ou mémoire partagée, pour publier les données de performance.  La taille de la mémoire partagée détermine le nombre d'instances qui peuvent être utilisées en même temps.  Il existe deux types de mémoire partagée : la mémoire partagée globale et la mémoire partagée séparée.  La mémoire partagée globale est utilisée par toutes les catégories de compteurs de performance installés avec les versions 1.0 ou 1.1 du .NET Framework.  Les catégories de compteurs de performance installés avec le .NET Framework version 2.0 utilise une mémoire partagée distincte, chaque catégorie de compteurs de performance disposant de sa propre mémoire.  
  
 La taille de la mémoire partagée globale peut être définie uniquement dans un fichier de configuration.  La taille par défaut est de 524 288 octets, la taille maximale de 33 554 432 octets et la taille minimale de 32 768 octets.  Dans la mesure où la mémoire partagée globale est partagée par tous les processus et toutes les catégories, c'est le premier créateur qui spécifie sa taille.  Si vous définissez la taille dans le fichier de configuration de votre application, cette taille est utilisée uniquement si votre application est la première application qui déclenche l'exécution des compteurs de performance.  Par conséquent, l'emplacement correct pour spécifier la valeur de `filemappingsize` est le fichier Machine.config.  La mémoire de la mémoire partagée globale ne peut pas être libérée par les compteurs de performance individuels, de sorte que la mémoire partagée globale finit par être épuisée si un grand nombre d'instances de compteur de performance avec des noms différents sont créées.  
  
 En ce qui concerne la taille de la mémoire partagée séparée, c'est la valeur DWORD FileMappingSize de la clé de Registre HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\*\<category name\>*\\Performance qui est d'abord référencée, suivie de la valeur spécifiée pour la mémoire partagée globale dans le fichier de configuration.  Si la valeur FileMappingSize n'existe pas, la taille de la mémoire partagée séparée est définie avec une valeur représentant un quart \(1\/4\) du paramètre global spécifié dans le fichier de configuration.  
  
## Voir aussi  
 <xref:System.Diagnostics.PerformanceCounter>   
 <xref:System.Diagnostics.PerformanceCounterCategory>   
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>   
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>