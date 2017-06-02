---
title: "Custom Partitioners for PLINQ and TPL | Microsoft Docs"
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
  - "tasks, partitioners"
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Custom Partitioners for PLINQ and TPL
Pour paralléliser une opération sur une source de données, l'une des étapes essentielles consiste à *partitionner* la source en plusieurs sections auxquelles il est possible d'accéder de manière simultanée par le biais de plusieurs threads.  PLINQ et la bibliothèque parallèle de tâches fournissent des partitionneurs par défaut qui fonctionnent de façon transparente lorsque vous écrivez une requête parallèle ou une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A>.  Pour disposer de scénarios plus avancés, vous pouvez brancher votre propre partitionneur.  
  
## Genres de partitionnement  
 Il existe de nombreuses méthodes pour partitionner une source de données.  Dans les approches les plus efficaces, plusieurs threads coopèrent pour traiter la séquence source d'origine, plutôt que de séparer physiquement la source en plusieurs sous\-séquences.  Pour des tableaux et d'autres sources indexées telles que des collections <xref:System.Collections.IList> où la longueur est connue à l'avance, le *partitionnement par plages de valeurs* est le genre de partitionnement le plus simple.  Chaque thread reçoit des index de début et de fin uniques, afin qu'il puisse traiter sa plage de la source sans remplacer ou être remplacé par tout autre thread.  Les seules surcharges impliquées dans le partitionnement par plages de valeurs sont le travail initial de création de plages ; après cela, aucune synchronisation supplémentaire n'est obligatoire.  Par conséquent, une bonne performance peut être fournie tant que la charge de travail est divisée en parts égales.  Le partitionnement par plages de valeurs présente un inconvénient : si un thread finit tôt, il ne peut pas aider les autres threads à finir leur travail.  
  
 Dans le cas de listes liées ou d'autres collections dont la longueur n'est pas connue, vous pouvez utiliser le *partitionnement par segments*.  Dans le cas du partitionnement par segments, chaque thread ou tâche dans une requête ou une boucle parallèle consomme un certain nombre d'éléments source dans un segment, les traite, puis revient pour extraire des éléments supplémentaires.  Le partitionneur vérifie que tous les éléments sont distribués et qu'il n'y a pas de doublons.  Un segment peut être de toute taille.  Par exemple, le partitionneur illustré dans [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) crée des segments qui contiennent juste un élément.  Tant que les segments ne sont pas trop grands, ce genre de partitionnement équilibre la charge de manière intrinsèque parce que l'assignation d'éléments aux threads n'est pas prédéterminée.  Toutefois, le partitionneur subit les surcharges de synchronisation chaque fois que le thread a besoin d'un autre segment.  La quantité de synchronisation encourue dans ces cas\-là est inversement proportionnelle à la taille des segments.  
  
 En général, le partitionnement par plages de valeurs est plus rapide uniquement lorsque la durée d'exécution du délégué est faible à modérée, que la source se compose d'un grand nombre d'éléments et que le travail total de chaque partition est approximativement équivalent.  Le partitionnement par segments est ainsi généralement plus rapide dans la plupart des cas.  Sur des sources composées d'un petit nombre d'éléments ou affichant des durées d'exécution plus longues pour le délégué, la performance du partitionnement par plages de valeurs et par segments est presque égale.  
  
 Les partitionneurs de la bibliothèque parallèle de tâches prennent également en charge un nombre dynamique de partitions.  Cela signifie qu'ils peuvent créer des partitions à la volée, par exemple, lorsque la boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A> engendre une nouvelle tâche.  Cette fonctionnalité permet au partitionneur de se mettre à l'échelle de la boucle elle\-même.  Les partitionneurs dynamiques équilibrent également la charge de manière intrinsèque.  Lorsque vous créez un partitionneur personnalisé, vous devez prendre en charge le partitionnement dynamique qui sera consommable à partir d'une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A>.  
  
### Configuration de partitionneurs d'équilibrage de charge pour PLINQ  
 Quelques surcharges de la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=fullName> vous permettent de créer un partitionneur pour un tableau ou une source <xref:System.Collections.IList> et de spécifier s'il doit essayer d'équilibrer la charge de travail entre les threads.  Lorsque le partitionneur est configuré pour équilibrer la charge, le partitionnement par segments est utilisé et les éléments sont rendus à chaque partition en petits segments comme ils sont demandés.  Cette approche permet de vérifier que toutes les partitions ont des éléments à traiter jusqu'à ce que la boucle entière ou la requête soit effectuée.  Une surcharge supplémentaire peut être utilisée pour fournir le partitionnement d'équilibrage de charge de toute source <xref:System.Collections.IEnumerable>.  
  
 En général, l'équilibrage de charge requiert que les partitions demandent relativement souvent des éléments à partir du partitionneur.  Par contraste, un partitionneur qui effectue le partitionnement statique peut assigner tous les éléments à chaque partitionneur en une fois en utilisant le partitionnement par plages de valeurs ou par segments.  Cela nécessite moins de surcharge que l'équilibrage de charge, mais l'exécution peut prendre plus de temps si un thread finit avec considérablement plus de travail que les autres.  Par défaut, lorsqu'un IList ou un tableau lui est passé, PLINQ utilise toujours le partitionnement par plages de valeurs sans équilibrage de charge.  Pour permettre l'équilibrage de charge pour PLINQ, utilisez la méthode `Partitioner.Create`, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 La meilleure méthode pour déterminer s'il convient d'utiliser l'équilibrage de charge dans tout scénario donné consiste à expérimenter et à mesurer le temps que prennent les opérations avec des charges et des configurations d'ordinateurs représentatives.  Par exemple, le partitionnement statique peut fournir une accélération significative sur un ordinateur multicœur qui est uniquement doté de quelques cœurs, mais il peut provoquer des ralentissements sur les ordinateurs qui disposent de nombreux cœurs.  
  
 Le tableau suivant répertorie les surcharges disponibles de la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A>.  L'utilisation de ces partitionneurs n'est pas limitée uniquement à PLINQ ou à <xref:System.Threading.Tasks.Task>.  Ils peuvent également être utilisés avec toute construction parallèle personnalisée.  
  
|Surcharge|Utilise l'équilibrage de charge|  
|---------------|-------------------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Toujours|  
|[Create\<TSource\>\(TSource\<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Lorsque l'argument Boolean est spécifié comme true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Lorsque l'argument Boolean est spécifié comme true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Jamais|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Jamais|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Jamais|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Jamais|  
  
### Configuration de partitionneurs de plages statiques pour Parallel.ForEach  
 Dans une boucle <xref:System.Threading.Tasks.Parallel.For%2A>, le corps de la boucle est fourni à la méthode en tant que délégué.  Le coût d'appel de ce délégué est approximativement le même que celui d'un appel de méthode virtuel.  Dans certains scénarios, le corps d'une boucle parallèle peut être suffisamment petit pour que le coût d'appel du délégué sur chaque itération de boucle devienne significatif.  Dans ce type de situations, vous pouvez utiliser l'une des surcharges <xref:System.Collections.Concurrent.Partitioner.Create%2A> pour créer un <xref:System.Collections.Generic.IEnumerable%601> de partitions de plages de valeurs sur les éléments source.  Vous pouvez passer ensuite cette collection de plages à une méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A> dont le corps se compose d'une boucle `for` normale.  Cette approche présente un avantage : le coût d'appel du délégué est uniquement encouru une fois par plage, plutôt qu'une fois par élément.  L'exemple suivant illustre le modèle de base.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Chaque thread dans la boucle reçoit son propre <xref:System.Tuple%602> qui contient les valeurs d'index de début et de fin dans la sous\-plage spécifiée.  La boucle `for` interne utilise les valeurs `toExclusive` et `fromInclusive` pour faire une boucle directement sur le tableau ou le <xref:System.Collections.IList>.  
  
 L'une des surcharges <xref:System.Collections.Concurrent.Partitioner.Create%2A> vous permet de spécifier la taille des partitions et leur nombre.  Cette surcharge peut être utilisée dans des scénarios où le travail par élément est si faible que même un appel de méthode virtuel par élément a un impact notable sur la performance.  
  
## Partitionneurs personnalisés  
 Dans certains scénarios, il peut valoir la peine ou même être obligatoire d'implémenter votre propre partitionneur.  Par exemple, vous pouvez avoir une classe de collection personnalisée que vous pouvez partitionner plus efficacement que les partitionneurs par défaut, selon votre connaissance de la structure interne de la classe.  Sinon, vous pouvez créer des partitions de plages de valeurs de diverses tailles selon votre connaissance de la durée de traitement de ces éléments à des emplacements différents dans la collection source.  
  
 Pour créer un partitionneur personnalisé de base, dérivez une classe à partir de <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=fullName> et substituez les méthodes virtuelles, comme décrit dans le tableau suivant.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un IList \(IEnumerator \(TSource\)\).  Chaque thread de travail dans la boucle ou requête peut appeler `GetEnumerator` sur la liste pour récupérer un <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retournez la valeur `true` si vous implémentez <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, sinon, `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Si vous devez pouvoir trier les résultats ou si vous nécessitez un accès indexé aux éléments, dérivez alors de <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> et substituez ses méthodes virtuelles comme décrit dans le tableau suivant.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un `IList(IEnumerator(TSource))`.  Chaque thread de travail dans la boucle ou requête peut appeler `GetEnumerator` sur la liste pour récupérer un <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retournez la valeur `true` si vous implémentez <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; sinon, false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|En général, cela entraîne l'appel de <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Le tableau suivant fournit des détails supplémentaires sur la façon dont les trois genres de partitionneurs d'équilibrage de charge implémentent la classe <xref:System.Collections.Concurrent.OrderablePartitioner%601>.  
  
|Méthode\/Propriété|IList \/ Tableau sans équilibrage de charge|IList \/ tableau avec équilibrage de charge|IEnumerable|  
|------------------------|-------------------------------------------------|-------------------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Utilise le partitionnement par plages de valeurs|Utilise le partitionnement par segments optimisés pour les listes du partitionCount spécifié|Utilise le partitionnement par segments en créant un nombre statique de partitions.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=fullName>|Lève une exception non prise en charge.|Utilise le partitionnement par segments optimisé pour les listes et les partitions dynamiques|Utilise le partitionnement par segments en créant un nombre dynamique de partitions.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Retourne `true`|Retourne `true`|Retourne `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Retourne `true`|Retourne `false`|Retourne `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Retourne `true`|Retourne `true`|Retourne `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retourne `false`|Retourne `true`|Retourne `true`|  
  
### Partitions dynamiques  
 Si vous prévoyez d'utiliser le partitionneur dans une méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A>, vous devez être en mesure de retourner un nombre dynamique de partitions.  Cela signifie que le partitionneur peut fournir un énumérateur pour une nouvelle partition à la demande à n'importe quel moment pendant l'exécution de la boucle.  Fondamentalement, chaque fois que la boucle ajoute une nouvelle tâche parallèle, elle demande une nouvelle partition pour cette tâche.  Si vous devez pouvoir classer les données, dérivez alors de <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> afin qu'un index unique soit assigné à chaque élément de chaque partition.  
  
 Pour obtenir des informations supplémentaires et un exemple, consultez [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### Contrat pour les partitionneurs  
 Lorsque vous implémentez un partitionneur personnalisé, suivez ces indications afin d'aider à vérifier l'interaction correcte avec PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A> dans la bibliothèque parallèle de tâches :  
  
-   Si <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> est appelé avec un argument de zéro ou moins pour `partitionsCount`, levez <xref:System.ArgumentOutOfRangeException>.  Bien que PLINQ et TPL ne passent jamais dans un `partitionCount` égal à 0, nous vous recommandons néanmoins de vous prémunir contre cette possibilité.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> doivent toujours retourner un nombre `partitionsCount` de partitions.  Si le partitionneur manque de données et ne peut pas créer autant de partitions qu'il est demandé, alors la méthode doit retourner un énumérateur vide pour chacune des partitions restantes.  Sinon, PLINQ et TPL lèveront un <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> ne doivent jamais retourner `null` \(`Nothing` en Visual Basic\).  Le cas échéant, PLINQ \/ TPL lèveront une <xref:System.InvalidOperationException>.  
  
-   Les méthodes qui retournent des partitions doivent toujours retourner les partitions qui peuvent énumérer de manière complète et unique la source de données.  Il ne doit y avoir aucune duplication dans la source de données ou les éléments ignorés à moins que la conception du partitionneur ne le requière spécifiquement.  Si cette règle n'est pas suivie, l'ordre de sortie peut être brouillé.  
  
-   Les accesseurs booléens suivants doivent toujours retourner correctement les valeurs suivantes afin que l'ordre de sortie ne soit pas brouillé :  
  
    -   `KeysOrderedInEachPartition`: chaque partition retourne des éléments avec des index clés accrus.  
  
    -   `KeysOrderedAcrossPartitions`: pour toutes les partitions retournées, les index clés dans la partition *i* sont plus élevés que les index clés de la partition *i*\-1.  
  
    -   `KeysNormalized`: tous les index clés s'accroissent de manière monotone, sans écart, en démarrant à partir du zéro.  
  
-   Tous les index doivent être uniques.  Il ne peut pas y avoir d'index en double.  Si cette règle n'est pas suivie, l'ordre de sortie peut être brouillé.  
  
-   Tous les index ne doivent pas être négatifs.  Si cette règle n'est pas suivie, PLINQ\/TPL peut lever des exceptions.  
  
## Voir aussi  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)   
 [How to: Implement a Partitioner for Static Partitioning](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)