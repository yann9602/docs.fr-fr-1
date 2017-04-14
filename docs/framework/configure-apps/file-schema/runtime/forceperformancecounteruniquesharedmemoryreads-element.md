---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<forcePerformanceCounterUniqueSharedMemoryReads> (élément)"
  - "forcePerformanceCounterUniqueSharedMemoryReads (élément)"
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;, &#233;l&#233;ment
Spécifie si PerfCounter.dll utilise le paramètre du Registre CategoryOptions dans une application .NET Framework version 1.1 pour déterminer s'il faut charger des données de compteur de performance à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.  
  
## Syntaxe  
  
```  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si PerfCounter.dll utilise le paramètre du Registre CategoryOptions pour déterminer s'il faut charger des données de compteur de performance à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|PerfCounter.dll n'utilise pas le paramètre du Registre CategoryOptions. Il s'agit de la valeur par défaut.|  
|`true`|PerfCounter.dll utilise le paramètre du Registre CategoryOptions.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Dans les versions du .NET Framework avant le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], la version de PerfCounter.dll chargée correspondait au runtime chargé dans le processus.  Si le .NET Framework version 1.1 et le [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] étaient tous les deux installés sur un ordinateur, une application .NET Framework 1.1 chargerait le .NET Framework version 1.1 de PerfCounter.dll.  Lors du démarrage avec le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], la dernière version installée de PerfCounter.dll est chargée.  Cela signifie qu'une application .NET Framework 1.1 chargera la version [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] de PerfCounter.dll si le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] est installé sur l'ordinateur.  
  
 Lors du démarrage avec le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], lors de l'utilisation de compteurs de performance, PerfCounter.dll vérifie l'entrée de Registre CategoryOptions pour chaque fournisseur pour déterminer s'il doit lire dans la mémoire partagée spécifique à la catégorie ou dans la mémoire partagée globale.  Le fichier PerfCounter.dll du .NET Framework 1.1 ne lit pas cette entrée du Registre, parce qu'il ne tient pas compte de la mémoire partagée spécifique à la catégorie ; il lit toujours à partir de la mémoire partagée globale.  
  
 Pour la compatibilité descendante, le PerfCounter.dll [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] n'active pas l'entrée du Registre CategoryOptions lors du fonctionnement dans une application .NET Framework 1.1.  Il utilise simplement la mémoire partagée globale, comme le PerfCounter.dll .NET Framework 1.1.  Toutefois, vous pouvez demander au PerfCounter.dll [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] de vérifier le paramètre du Registre en activant l'élément `<forcePerformanceCounterUniqueSharedMemoryReads>`.  
  
> [!NOTE]
>  L'activation de l'élément `<forcePerformanceCounterUniqueSharedMemoryReads>` ne garantit pas que la mémoire partagée spécifique à la catégorie sera utilisée.  Si le paramètre est activé avec la valeur `true`, PerfCounter.dll référence le paramètre du Registre CategoryOptions.  Par défaut, CategoryOptions utilise la mémoire partagée spécifique à la catégorie ; toutefois, vous pouvez modifier CategoryOptions pour indiquer que la mémoire partagée globale doit être utilisée.  
  
 La clé de Registre qui contient le paramètre CategoryOptions est HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\\<categoryName\>\\Performance.  Par défaut, CategoryOptions a la valeur 3, ce qui indique à PerfCounter.dll d'utiliser la mémoire partagée spécifique à la catégorie.  Si CategoryOptions a la valeur 0, PerfCounter.dll utilise la mémoire partagée globale.  Les données d'instance seront réutilisées uniquement si le nom de l'instance qui est créée est identique à l'instance qui est réutilisée.  Toutes les versions pourront écrire dans la catégorie.  Si CategoryOptions a la valeur 1, la mémoire partagée globale est utilisée, mais les données d'instance peuvent être réutilisées si le nom de catégorie a la même longueur que la catégorie qui est réutilisée.  
  
 Les paramètres 0 et 1 peuvent mener à des fuites de mémoire et au remplissage de la mémoire du compteur de performances.  
  
## Exemple  
 L'exemple suivant montre comment spécifier que PerfCounter.dll doit référencer l'entrée de Registre CategoryOptions pour déterminer s'il doit utiliser la mémoire partagée spécifique à la catégorie.  
  
```  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)