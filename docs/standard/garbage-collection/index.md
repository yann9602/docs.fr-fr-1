---
title: "Garbage Collection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "memory, garbage collection"
  - "garbage collection, automatic memory management"
  - "GC [.NET Framework]"
  - "memory, allocating"
  - "common language runtime, garbage collection"
  - "garbage collector"
  - "cleanup operations"
  - "garbage collection"
  - "memory, releasing"
  - "common language runtime, automatic memory management"
  - "automatic memory management"
  - "runtime, automatic memory management"
  - "runtime, garbage collection"
  - "garbage collection, about"
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: 36
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 36
---
# Garbage Collection
Le garbage collector \(également appelé ramasse\-miettes\) du .NET Framework manage l'allocation et la libération de mémoire dans votre application.  Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire à l'objet à partir du tas managé.  Tant que de l'espace d'adressage est disponible dans le tas managé, le runtime continue à allouer de l'espace pour les nouveaux objets.  Toutefois, la mémoire n'est pas infinie.  Le garbage collector doit finir par effectuer un garbage collection afin de libérer de la mémoire.  Le moteur d'optimisation du garbage collector détermine le meilleur moment pour effectuer un garbage collection en fonction des allocations en cours.  Lorsque le garbage collector effectue un garbage collection, il recherche les objets figurant dans le tas managé qui ne sont plus utilisés par l'application et effectue les opérations nécessaires pour récupérer leur mémoire.  
  
<a name="related_topics"></a>   
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Fundamentals of Garbage Collection](../../../docs/standard/garbage-collection/fundamentals.md)|Décrit le fonctionnement du garbage collection, comment les objets sont alloués sur le tas managé, ainsi que d'autres concepts importants.|  
|[Garbage Collection and Performance](../../../docs/standard/garbage-collection/performance.md)|Décrit les vérifications des performances que vous pouvez utiliser pour diagnostiquer les problèmes de nettoyage de la mémoire et de performances.|  
|[Collections forcées](../../../docs/standard/garbage-collection/induced.md)|Décrit comment générer un garbage collection.|  
|[Latency Modes](../../../docs/standard/garbage-collection/latency.md)|Décrit les modes qui déterminent l'intrusion de garbage collection.|  
|[Optimization for Shared Web Hosting](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Décrit comment optimiser le garbage collection sur les serveurs partagés par plusieurs petits sites Web.|  
|[Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md)|Décrit comment déterminer à quel moment un garbage collection est effectué et à quel moment il est fini.|  
|[Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Décrit comment contrôler l'utilisation de la mémoire et de l'UC par un domaine d'application.|  
|[Weak References](../../../docs/standard/garbage-collection/weak-references.md)|Décrit les fonctionnalités qui autorisent le garbage collector à rassembler un objet tout en permettant à l'application d'accéder à ce dernier.|  
  
## Référence  
 <xref:System.GC?displayProperty=fullName>  
  
 <xref:System.GCCollectionMode?displayProperty=fullName>  
  
 <xref:System.GCNotificationStatus?displayProperty=fullName>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
  
 <xref:System.IDisposable?displayProperty=fullName>  
  
## Voir aussi  
 [Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md)