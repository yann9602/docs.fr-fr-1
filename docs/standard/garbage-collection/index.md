---
title: Garbage Collection | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: 36
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 11ea4186a77a600d1645fe334ba9fd704fe728b4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="garbage-collection"></a>Garbage Collection
Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application. Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé. Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets. Toutefois, la mémoire n’est pas infinie. Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire. Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées. Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Principes de base du Garbage Collection](../../../docs/standard/garbage-collection/fundamentals.md)|Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.|  
|[Garbage Collection et performances](../../../docs/standard/garbage-collection/performance.md)|Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.|  
|[Collections forcées](../../../docs/standard/garbage-collection/induced.md)|Décrit comment faire pour qu’un garbage collection se produise.|  
|[Modes de latence](../../../docs/standard/garbage-collection/latency.md)|Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.|  
|[Optimisation de l'hébergement web partagé](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.|  
|[Notifications de garbage collection](../../../docs/standard/garbage-collection/notifications.md)|Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.|  
|[Analyse de ressource de domaine d'application](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.|  
|[Références faibles](../../../docs/standard/garbage-collection/weak-references.md)|Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.|  
  
## <a name="reference"></a>Référence  
 <xref:System.GC?displayProperty=fullName>  
  
 <xref:System.GCCollectionMode?displayProperty=fullName>  
  
 <xref:System.GCNotificationStatus?displayProperty=fullName>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
  
 <xref:System.IDisposable?displayProperty=fullName>  
  
## <a name="see-also"></a>Voir aussi  
 [Nettoyage de ressources non managées](../../../docs/standard/garbage-collection/unmanaged.md)
