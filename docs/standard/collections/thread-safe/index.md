---
title: "Collections thread-safe | Microsoft Docs"
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
  - "collections thread-safe, vue d’ensemble"
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# Collections thread-safe
Le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] introduit l'espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName>, qui inclut plusieurs classes de collections qui sont à la fois thread\-safe et évolutives.  Plusieurs threads peuvent, sans risque et de façon efficace, ajouter ou supprimer des éléments de ces collections, sans nécessiter une synchronisation supplémentaire dans le code utilisateur.  Lorsque vous écrivez du nouveau code, utilisez les classes de collections simultanées chaque fois que la collection écrit simultanément dans plusieurs threads.  Si vous ne faites que lire à partir d'une collection partagée, vous pouvez utiliser les classes de l'espace de noms <xref:System.Collections.Generic?displayProperty=fullName>.  Nous vous recommandons de ne pas utiliser les classes de collections 1.0 à moins que vous ne deviez cibler le .NET Framework 1.1 ou une version antérieure.  
  
## Synchronisation de threads dans les collections .NET Framework 1.0 et 2.0  
 Les collections introduites dans le .NET Framework 1.0 se trouvent dans l'espace de noms <xref:System.Collections?displayProperty=fullName>.  Ces collections, qui incluent les <xref:System.Collections.ArrayList> et <xref:System.Collections.Hashtable> souvent utilisés, fournissent une certaine sécurité des threads via la propriété `Synchronized`, qui retourne un wrapper thread\-safe autour de la collection.  Le wrapper fonctionne en verrouillant l'ensemble de la collection à chaque opération d'ajout ou de suppression.  Par conséquent, chaque thread qui essaie d'accéder à la collection doit attendre son tour pour prendre le verrou.  Ce fonctionnement n'est pas évolutif et peut provoquer une importante dégradation des performances pour les grandes collections.  De même, la conception n'est pas complètement protégée contre les conditions de concurrence.  Pour plus d'informations, consultez [Synchronisation dans les collections génériques](http://go.microsoft.com/fwlink/?LinkID=161130) sur le site Web MSDN.  
  
 Les classes de collections introduites dans le .NET Framework 2.0 se trouvent dans l'espace de noms <xref:System.Collections.Generic?displayProperty=fullName>.  Il s'agit notamment de <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, etc.  Ces classes fournissent une sécurité de type et des performances améliorées par rapport aux classes du .NET Framework 1.0.  Toutefois, les classes de collections .NET Framework 2.0 ne fournissent pas de synchronisation des threads. Le code utilisateur doit fournir toute la synchronisation lorsque des éléments sont ajoutés ou supprimés sur plusieurs threads simultanément.  
  
 Nous recommandons les classes de collections simultanées du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] car elles ne fournissent pas uniquement la sécurité de type des classes de collections .NET Framework 2.0, mais également plus d'efficacité et de sécurité des threads que les collections [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)].  
  
## Verrouillage de granularité fine et mécanismes sans verrou  
 Certains types de collections simultanés utilisent des mécanismes de synchronisation légers tels que <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim> et <xref:System.Threading.CountdownEvent>, qui sont des nouveautés du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  Ces types de synchronisation utilisent en général la *rotation intensive* pendant de courtes périodes avant de mettre le thread dans un véritable état d'attente.  Lorsque les temps d'attente sont supposés être très courts, la rotation est beaucoup moins gourmande en ressources informatiques que l'attente, qui implique une transition de noyau complexe.  Pour les classes de collections qui utilisent la rotation, cette efficacité signifie que plusieurs threads peuvent ajouter et supprimer des éléments à un taux très élevé.  Pour plus d'informations sur la rotation contre le blocage, consultez [SpinLock](../../../../docs/standard/threading/spinlock.md) et [SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 Les classes <xref:System.Collections.Concurrent.ConcurrentStack%601> et <xref:System.Collections.Concurrent.ConcurrentQueue%601> n'utilisent pas de verrous du tout.  À la place, ils se reposent sur des opérations <xref:System.Threading.Interlocked> pour accomplir la sécurité des threads.  
  
> [!NOTE]
>  Étant donné que les classes de collections simultanées prennent en charge <xref:System.Collections.ICollection>, elles fournissent des implémentations pour les propriétés <xref:System.Collections.ICollection.IsSynchronized%2A> et <xref:System.Collections.ICollection.SyncRoot%2A>, bien que ces propriétés ne soient pas pertinentes.  `IsSynchronized` retourne toujours `false` et `SyncRoot` a toujours la valeur `null` \(`Nothing` en Visual Basic\).  
  
 Le tableau suivant répertorie les types de collections dans l'espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName>.  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Fournit des fonctionnalités de délimitation et de blocage pour tout type qui implémente <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.  Pour plus d'informations, consultez [Vue d'ensemble de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implémentation thread\-safe d'un dictionnaire de paires clé\-valeur.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implémentation thread\-safe d'une file d'attente FIFO \(premier entré, premier sorti\).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implémentation thread\-safe d'une pile LIFO \(dernier entré, premier sorti\).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implémentation thread\-safe d'une collection non ordonnée d'éléments.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Interface qu'un type doit implémenter pour être utilisé dans une `BlockingCollection`.|  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d'ensemble de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Décrit les fonctionnalités fournies par le type <xref:System.Collections.Concurrent.BlockingCollection%601>.|  
|[Comment : ajouter et supprimer des éléments d'un ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Décrit comment ajouter et supprimer des éléments d'un <xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Comment : ajouter et prendre des éléments individuellement dans un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Décrit comment ajouter et extraire des éléments d'une collection bloquante sans utiliser l'énumérateur en lecture seule.|  
|[Comment : ajouter des fonctionnalités de liaison et de blocage à une collection](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Décrit comment utiliser toute classe de collection en tant que mécanisme de stockage sous\-jacent pour une collection <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.|  
|[Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Décrit comment utiliser `foreach` \(`For Each` en Visual Basic\) pour supprimer tous les éléments d'une collection bloquante.|  
|[Comment : utiliser des tableaux de collections de blocage dans un pipeline](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Décrit comment utiliser en même temps plusieurs collections bloquantes pour implémenter un pipeline.|  
|[Comment : créer un pool d'objets à l'aide d'un ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Indique comment utiliser un conteneur simultané pour améliorer les performances dans les scénarios où vous pouvez réutiliser des objets au lieu d'en créer continuellement de nouveaux.|  
  
## Référence  
 <xref:System.Collections.Concurrent?displayProperty=fullName>