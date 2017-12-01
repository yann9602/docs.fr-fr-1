---
title: "Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12d234b86b0067178d54d2fdcb5d37ceaee6109d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)
Pour paralléliser une opération sur une source de données, l’une des étapes essentielles consiste à *partition* la source en plusieurs sections qui peuvent être accessibles simultanément par plusieurs threads. PLINQ et la bibliothèque parallèle de tâches (TPL) fournissent des partitionneurs par défaut qui fonctionnent de façon transparente lorsque vous écrivez une requête parallèle ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> boucle. Pour des scénarios plus avancés, vous pouvez incorporer dans votre propre partitionneur.  
  
## <a name="kinds-of-partitioning"></a>Genres de partitionnement  
 Il existe de nombreuses façons d’une source de données de partition. Dans les approches les plus efficaces, plusieurs threads coopèrent pour le processus de la séquence source d’origine, plutôt que de séparer physiquement la source en plusieurs sous-séquences. Pour des tableaux et d’autres sources indexées telles que <xref:System.Collections.IList> collections où la longueur est connue à l’avance, *partitionnement par plage* est le type le plus simple de partitionnement. Chaque thread reçoit unique de début et de fin des index, afin qu’il puisse traiter sa plage de la source sans remplacer ou être remplacé par un autre thread. La seule surcharge impliquées dans le partitionnement par plage est le travail initial de création de plages ; Aucune synchronisation supplémentaire n’est requise par la suite. Par conséquent, elle peut fournir de bonnes performances tant que la charge de travail est réparti de manière égale. L’inconvénient de partitionnement par plage est que si un thread se termine plus tôt, il ne peut pas aider les autres threads terminer son travail.  
  
 Pour des listes liées ou d’autres collections dont la longueur n’est pas connue, vous pouvez utiliser *le partitionnement*. Dans le partitionnement, chaque thread ou une tâche dans une boucle parallèle ou une requête consomme un certain nombre d’éléments de la source dans un segment, les traite, puis revient pour extraire des éléments supplémentaires. Le partitionneur garantit que tous les éléments sont distribués et qu’il n’y a pas de doublons. Un segment peut être n’importe quelle taille. Par exemple, le partitionneur qui est illustré dans [Comment : implémenter des Partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) crée des segments qui contiennent uniquement un élément. Tant que les segments ne sont pas trop volumineux, ce type de partitionnement est, par nature, l’équilibrage de charge, car l’assignation d’éléments aux threads n’est pas prédéfinie. Toutefois, le partitionneur subit la surcharge de synchronisation chaque fois que le thread a besoin d’un autre segment. La quantité de synchronisation effectuée dans ces cas est inversement proportionnelle à la taille des blocs.  
  
 En règle générale, partitionnement par plage n’est plus rapide lorsque la durée d’exécution du délégué est faible à modérée et la source a un grand nombre d’éléments, et le total du travail de chaque partition est à peu près équivalent. Le partitionnement est donc généralement plus rapide dans la plupart des cas. Sur les sources avec un petit nombre d’éléments ou les durées d’exécution pour le délégué, puis les performances de segment et le partitionnement par plage sont équivalente.  
  
 Les partitionneurs prêts à la bibliothèque parallèle de tâches prennent également en charge un nombre dynamique de partitions. Cela signifie qu’ils peuvent créer des partitions à la volée, par exemple, lorsque le <xref:System.Threading.Tasks.Parallel.ForEach%2A> boucle engendre une nouvelle tâche. Cette fonctionnalité permet au partitionneur à l’échelle de la boucle elle-même. Les partitionneurs dynamiques sont également, par nature, l’équilibrage de charge. Lorsque vous créez un partitionneur personnalisé, vous devez prendre en charge le partitionnement dynamique pour être utilisable à partir d’un <xref:System.Threading.Tasks.Parallel.ForEach%2A> boucle.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Configuration de partitionneurs pour PLINQ d’équilibrage de charge  
 Certaines surcharges de la <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> méthode vous permettre de créer un partitionneur pour un tableau ou <xref:System.Collections.IList> source et de spécifier s’il doit essayer d’équilibrer la charge de travail entre les threads. Lorsque le partitionneur est configuré pour l’équilibrage de charge, le partitionnement est utilisé, et les éléments sont remis à chaque partition en petits segments lorsqu’ils sont demandés. Cette approche garantit que toutes les partitions ont des éléments à traiter jusqu'à ce que la boucle ou que la requête est terminée. Une surcharge supplémentaire peut être utilisée pour fournir le partitionnement d’équilibrage de charge de n’importe quel <xref:System.Collections.IEnumerable> source.  
  
 En général, l’équilibrage de charge requiert que les partitions pour demander des éléments relativement souvent à partir du partitionneur. En revanche, un partitionneur qui effectue le partitionnement statique peut affecter les éléments à chaque partitionneur tous en même temps à l’aide de la plage ou le partitionnement. Cela nécessite moins de surcharge que l’équilibrage de charge, mais elle peut prendre plus de temps à s’exécuter si un thread finit avec considérablement plus de travail que les autres. Par défaut lorsqu’il est passé un IList ou un tableau, PLINQ utilise toujours partitionnement par plage sans équilibrage de charge. Pour activer l’équilibrage de charge pour PLINQ, utilisez la `Partitioner.Create` méthode, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 La meilleure méthode pour déterminer si utiliser charge équilibrage de charge dans un scénario donné est à faire des essais et mesurer la durée d’opérations se terminent sous une charge représentative et les configurations d’ordinateur. Par exemple, le partitionnement statique peut fournir une accélération significative sur un ordinateur multicœur qui a uniquement quelques cœurs, mais cela peut entraîner des ralentissements sur les ordinateurs qui disposent de nombreux cœurs.  
  
 Le tableau suivant répertorie les surcharges disponibles de la <xref:System.Collections.Concurrent.Partitioner.Create%2A> (méthode). Utilisation de ces partitionneurs n’êtes pas limitée à utiliser uniquement avec PLINQ ou <xref:System.Threading.Tasks.Task>. Ils peuvent également être utilisés avec toute construction parallèle personnalisée.  
  
|Surcharge|Utilise l’équilibrage de charge|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Toujours|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Lorsque l’argument Boolean est spécifié comme true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Lorsque l’argument Boolean est spécifié comme true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Never|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Configuration de partitionneurs de plages statiques pour Parallel.ForEach  
 Dans un <xref:System.Threading.Tasks.Parallel.For%2A> boucle, le corps de la boucle est fourni à la méthode en tant que délégué. Le coût de l’appel de ce délégué est plus qu’un appel de méthode virtuelle. Dans certains scénarios, le corps d’une boucle parallèle peut être suffisamment petit pour que le coût de l’appel du délégué sur chaque itération de boucle devient important. Dans ce cas, vous pouvez utiliser une de le <xref:System.Collections.Concurrent.Partitioner.Create%2A> surcharges pour créer un <xref:System.Collections.Generic.IEnumerable%601> des partitions par plage sur les éléments source. Ensuite, vous pouvez passer cette collection de plages à un <xref:System.Threading.Tasks.Parallel.ForEach%2A> méthode dont le corps se compose d’une expression régulière `for` boucle. L’avantage de cette approche est que le coût d’appel de délégué implique qu’une seule fois par plage, plutôt qu’une seule fois par élément. L’exemple suivant illustre le modèle de base.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Chaque thread dans la boucle reçoit son propre <xref:System.Tuple%602> qui contient le début et fin des valeurs d’index dans la plage spécifiée. Interne `for` boucle utilise le `fromInclusive` et `toExclusive` pour parcourir le tableau de valeurs ou <xref:System.Collections.IList> directement.  
  
 Parmi les <xref:System.Collections.Concurrent.Partitioner.Create%2A> surcharges vous permet de spécifier la taille des partitions et le nombre de partitions. Cette surcharge peut être utilisée dans les scénarios où le travail par élément est donc faible qu’appel d’une méthode virtuelle par élément a un impact perceptible sur les performances.  
  
## <a name="custom-partitioners"></a>Partitionneurs personnalisés  
 Dans certains scénarios, il peut être utile ou même requise pour implémenter votre propre partitionneur. Par exemple, vous pouvez avoir une classe de collection personnalisée que vous pouvez partitionner plus efficacement que la valeur par défaut partitionneurs, selon votre connaissance de la structure interne de la classe. Ou bien, vous voudrez créer des partitions de plage de tailles différentes en fonction de votre connaissance de leur durée d’éléments de processus à différents emplacements dans la collection source.  
  
 Pour créer un partitionneur personnalisé de base, dérivez une classe de <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> et substituez les méthodes virtuelles, comme décrit dans le tableau suivant.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un IList(IEnumerator(TSource)). Chaque thread de travail dans la boucle ou requête peut appeler `GetEnumerator` sur la liste pour récupérer un <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retourner `true` si vous implémentez <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, dans le cas contraire, `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Si les résultats doivent être pouvant être triées ou vous avez besoin d’accès indexé dans les éléments, puis dérivent <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> et substituer ses méthodes virtuelles comme décrit dans le tableau suivant.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un `IList(IEnumerator(TSource))`. Chaque thread de travail dans la boucle ou requête peut appeler `GetEnumerator` sur la liste pour récupérer un <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retourner `true` si vous implémentez <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; sinon, false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|En règle générale, cela entraîne l’appel <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Le tableau suivant fournit des détails supplémentaires sur la façon des trois genres d’équilibrage de charge de mettre en œuvre les partitionneurs prêts à la <xref:System.Collections.Concurrent.OrderablePartitioner%601> classe.  
  
|Méthode/propriété|IList / tableau sans équilibrage de charge|IList / tableau avec équilibrage de charge|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Utilise le partitionnement par plage|Utilise le partitionnement est optimisé pour les listes pour le partitionCount spécifié|Utilise le partitionnement en créant un nombre statique de partitions.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Lève une exception non prise en charge (exception)|Utilise le partitionnement est optimisé pour les listes et les partitions dynamiques|Utilise le partitionnement en créant un nombre dynamique de partitions.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Retourne `true`.|Retourne `true`.|Retourne `true`.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Retourne `true`.|Retourne `false`.|Retourne `false`.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Retourne `true`.|Retourne `true`.|Retourne `true`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retourne `false`.|Retourne `true`.|Retourne `true`.|  
  
### <a name="dynamic-partitions"></a>Partitions dynamiques  
 Si vous envisagez du partitionneur à utiliser dans un <xref:System.Threading.Tasks.Parallel.ForEach%2A> (méthode), vous devez être en mesure de retourner un nombre dynamique de partitions. Cela signifie que le partitionneur peut fournir un énumérateur pour une nouvelle partition à la demande à tout moment pendant l’exécution de la boucle. En fait, chaque fois que la boucle ajoute une nouvelle tâche parallèle, elle demande une nouvelle partition pour cette tâche. Si vous avez besoin des données à être commandé, puis dérivent <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> afin qu’un index unique est assigné à chaque élément de chaque partition.  
  
 Pour plus d’informations et un exemple, consultez [Comment : implémenter des Partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Contrat pour les partitionneurs  
 Lorsque vous implémentez un partitionneur personnalisé, suivez ces instructions pour garantir l’interaction correcte avec PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A> dans la bibliothèque parallèle de tâches :  
  
-   Si <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> est appelé avec un argument de zéro ou moins pour `partitionsCount`, lever <xref:System.ArgumentOutOfRangeException>. Bien que PLINQ et la bibliothèque parallèle de tâches ne passent jamais dans un `partitionCount` égal à 0, nous vous recommandons néanmoins de vous prémunir contre les risques.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> doit toujours renvoyer `partitionsCount` nombre de partitions. Si le partitionneur manque de données et ne peut pas créer autant de partitions comme demandé, la méthode doit retourner un énumérateur vide pour chacune des partitions restantes. Sinon, PLINQ et la bibliothèque parallèle de tâches lèvent une <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> ne doit jamais retourner `null` (`Nothing` en Visual Basic). Dans le cas, PLINQ / TPL lèveront une <xref:System.InvalidOperationException>.  
  
-   Les méthodes qui retournent des partitions doivent toujours renvoyer des partitions qui peuvent entièrement et de façon unique énumérer la source de données. Il ne doit y avoir aucune duplication dans la source de données ou les éléments ignorés, sauf si spécifiquement requis par la conception du partitionneur. Si cette règle n’est pas suivie, l’ordre de sortie peut être brouillé.  
  
-   Les accesseurs booléens suivants doivent toujours retourner correctement les valeurs suivantes afin que l’ordre de sortie ne soit pas brouillé :  
  
    -   `KeysOrderedInEachPartition`: Chaque partition retourne des éléments en augmentant les index clés.  
  
    -   `KeysOrderedAcrossPartitions`: Pour toutes les partitions qui sont retournées, les index de clé dans la partition *i* sont plus élevées que les index de clé de partition *i*-1.  
  
    -   `KeysNormalized`: Tous les index de clé sont monotone, sans espaces vides, à partir de zéro.  
  
-   Tous les index doivent être uniques. Il peut être pas d’index en double. Si cette règle n’est pas suivie, l’ordre de sortie peut être brouillé.  
  
-   Tous les index doivent être non négatifs. Si cette règle n’est pas suivie, PLINQ/TPL peut lever des exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)  
 [Guide pratique pour implémenter des partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [Guide pratique pour implémenter un partitionneur pour un partitionnement statique](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
