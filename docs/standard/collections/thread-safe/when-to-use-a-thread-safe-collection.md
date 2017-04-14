---
title: "Quand utiliser une collection thread-safe | Microsoft Docs"
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
  - "collections thread-safe, quand effectuer une mise à niveau"
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Quand utiliser une collection thread-safe
Le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] présente cinq nouveaux types de collection conçus spécialement pour prendre en charge les opérations d'ajout et de suppression multithread.  Pour garantir la sécurité des threads, ces nouveaux types utilisent différents genres de mécanismes de verrouillage et de synchronisation sans verrou efficaces.  La synchronisation ajoute de la charge mémoire à une opération.  La quantité de charge mémoire dépend du genre de synchronisation utilisé, du type d'opérations exécuté et d'autres facteurs tels que le nombre de threads qui essaient d'accéder à la collection simultanément.  
  
 Dans certains scénarios, la charge mémoire de synchronisation est négligeable et permet au type multithread de s'exécuter considérablement plus rapidement et d'évoluer nettement mieux que son équivalent non thread\-safe en cas de protection par un verrou externe.  Dans d'autres scénarios, la charge mémoire peut générer une exécution et une évolutivité du type thread\-safe égales ou plus lentes que la version non thread\-safe et verrouillée extérieurement du type.  
  
 Les sections suivantes fournissent des recommandations générales concernant le moment où utiliser une collection thread\-safe ou son équivalent non thread\-safe possédant un verrou fourni par l'utilisateur autour de ses opérations de lecture et d'écriture.  Étant donné que les performances peuvent varier en fonction de nombreux facteurs, ces recommandations ne sont pas spécifiques et ne sont pas nécessairement valables dans toutes les circonstances.  Si les performances sont très importantes, la meilleure façon de déterminer le type de collection à utiliser consiste à mesurer les performances en fonction de configurations et de charges d'ordinateur représentatives.  Ce document utilise les conditions suivantes :  
  
 *Scénario producteur\-consommateur pur*  
 Tout thread donné ajoute ou supprime des éléments, mais pas les deux.  
  
 *Scénario producteur\-consommateur mixte*  
 Tout thread donné ajoute et supprime des éléments.  
  
 *Accélération*  
 Performances algorithmiques plus rapides par rapport à un autre type dans le même scénario.  
  
 *Extensibilité*  
 Augmentation des performances proportionnelle au nombre de cœurs de l'ordinateur.  Un algorithme évolutif s'exécute plus vite sur huit cœurs qu'il ne le fait sur deux cœurs.  
  
## ConcurrentQueue \(T\) et la file d'attente \(T\)  
 Dans les scénarios producteur\-consommateur purs, où le temps de traitement de chaque élément est très court \(quelques instructions\), <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> peut offrir des avantages modestes en matière de performances par rapport à un <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> avec un verrou externe.  Dans ce scénario, <xref:System.Collections.Concurrent.ConcurrentQueue%601> fonctionne mieux lorsqu'un thread dédié effectue la mise en file d'attente et un autre thread dédié annule la mise en file d'attente.  Si vous n'appliquez pas cette règle, <xref:System.Collections.Generic.Queue%601> peut même s'exécuter légèrement plus rapidement que <xref:System.Collections.Concurrent.ConcurrentQueue%601> sur des ordinateurs à plusieurs cœurs.  
  
 Lorsque le temps de traitement est autour de 500 opérations en virgule flottante ou plus, la règle de deux threads ne s'applique pas à <xref:System.Collections.Concurrent.ConcurrentQueue%601>, qui possède alors une très bonne extensibilité.  <xref:System.Collections.Generic.Queue%601> n'évolue pas bien dans ce scénario.  
  
 Dans les scénarios producteur\-consommateur mixtes, lorsque le temps de traitement est très court, une <xref:System.Collections.Generic.Queue%601> qui possède un verrou externe évolue mieux que <xref:System.Collections.Concurrent.ConcurrentQueue%601>.  Toutefois, lorsque le temps de traitement est autour de 500 opérations en virgule flottante ou plus, la <xref:System.Collections.Concurrent.ConcurrentQueue%601> évolue mieux.  
  
## ConcurrentStack et Stack  
 Dans les scénarios producteur\-consommateur purs, lorsque le temps de traitement est très court, <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> et <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> qui a un verrou externe s'exécuteront probablement de la même manière avec un thread d'exécution push dédié et un thread dépilant dédié.  Toutefois, à mesure que le nombre de threads augmente, les deux types ralentissent à cause de l'augmentation des conflits et <xref:System.Collections.Generic.Stack%601> peut fonctionner mieux que <xref:System.Collections.Concurrent.ConcurrentStack%601>.  Lorsque le temps de traitement est autour de 500 opérations en virgule flottante ou plus, les deux types évoluent environ au même taux.  
  
 Dans les scénarios producteur\-consommateur mixtes, <xref:System.Collections.Concurrent.ConcurrentStack%601> est plus rapide à la fois pour les petites charges de travail et les grandes.  
  
 L'utilisation de <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> et <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> peut accélérer considérablement les temps d'accès.  
  
## ConcurrentDictionary et le dictionnaire  
 En général, vous utilisez un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> dans tout scénario où vous ajoutez et mettez à jour des clés ou des valeurs simultanément à partir de plusieurs threads.  Dans les scénarios qui impliquent des mises à jour fréquentes et des lectures relativement peu nombreuses, le <xref:System.Collections.Concurrent.ConcurrentDictionary%602> offre généralement des avantages modestes.  Dans les scénarios qui impliquent de nombreuses lectures et de nombreuses mises à jour, le <xref:System.Collections.Concurrent.ConcurrentDictionary%602> est généralement considérablement plus rapide, quel que soit le nombre de cœurs des ordinateurs.  
  
 Dans les scénarios qui impliquent des mises à jour fréquentes, vous pouvez augmenter le degré d'accès concurrentiel dans le <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, puis mesurer pour voir si les performances augmentent sur les ordinateurs qui ont plus de cœurs.  Si vous modifiez le niveau d'accès concurrentiel, évitez les opérations globales autant que possible.  
  
 Si vous lisez uniquement des clé ou des valeurs, le <xref:System.Collections.Generic.Dictionary%602> est plus rapide car aucune synchronisation n'est requise si le dictionnaire n'est pas modifié par des threads.  
  
## ConcurrentBag  
 Dans les scénarios producteur\-consommateur purs, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> s'exécutera probablement plus lentement que les autres types de collection simultanés.  
  
 Dans les scénarios producteur\-consommateur mixtes, <xref:System.Collections.Concurrent.ConcurrentBag%601> est généralement beaucoup plus rapide et plus évolutif que les autres types de collection simultanés à la fois pour les petites charges de travail et pour les grandes.  
  
## BlockingCollection  
 Lorsqu'une sémantique de liaison et de blocage est requise, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> s'exécutera probablement plus rapidement que toute implémentation personnalisée.  Il prend également en charge une gestion riche des annulations, énumérations et exceptions.  
  
## Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Collections thread\-safe](../../../../docs/standard/collections/thread-safe/index.md)   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)