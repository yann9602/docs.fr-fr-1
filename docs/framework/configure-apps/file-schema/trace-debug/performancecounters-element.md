---
title: "&lt;performanceCounters&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64afd62c6eeca7bce14e331fdc65fccfa3d02bce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt; élément
Spécifie la taille de la mémoire globale partagée par les compteurs de performances.  
  
 \<configuration>  
\<System.Diagnostics >  
\<performanceCounters >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|FileMappingSize|Attribut requis.<br /><br /> Spécifie la taille, en octets, de la mémoire globale partagée par les compteurs de performances. La valeur par défaut est 524288.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Notes  
 Compteurs de performance utilisent un fichier mappé en mémoire, ou mémoire partagée, pour publier les données de performances.  La taille de la mémoire partagée détermine le nombre d’instances peut être utilisé à la fois.  Il existe deux types de mémoire partagée : mémoire partagée globale et mémoire partagée séparée.  La mémoire partagée globale est utilisée par toutes les catégories de compteur de performance installés avec les versions de .NET Framework 1.0 ou 1.1.  Catégories de compteur de performance installés avec le .NET Framework version 2.0 utilisent une mémoire partagée distincte, chaque catégorie de compteur de performance possédant sa propre mémoire.  
  
 La taille de la mémoire partagée globale peut être définie uniquement avec un fichier de configuration.  La taille par défaut est 524 288 octets, la taille maximale est de 33 554 432 octets et la taille minimale est de 32 768 octets.  Étant donné que la mémoire partagée globale est partagée par tous les processus et les catégories, le créateur du premier spécifie la taille.  Si vous définissez la taille de votre fichier de configuration d’application, cette taille est utilisée uniquement si votre application est la première application qui provoque les compteurs de performances à exécuter.  Par conséquent, l’emplacement correct pour spécifier le `filemappingsize` valeur est le fichier Machine.config.  La mémoire dans la mémoire partagée globale ne peut pas être libérée par les compteurs de performances individuels, forScope mémoire partagée globale est épuisée si un grand nombre d’instances de compteur de performance avec des noms différents est créé.  
  
 La taille de mémoire partagée séparée, la valeur DWORD FileMappingSize dans le Registre de clé HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nom de la catégorie >*\Performance est référencé. tout d’abord, suivi par la valeur spécifiée pour la mémoire partagée globale dans le fichier de configuration. Si la valeur FileMappingSize n’existe pas, alors que la taille de la mémoire partagée séparée est définie à un quart (1/4) le paramètre global dans le fichier de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
