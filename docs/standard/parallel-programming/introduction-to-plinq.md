---
title: "Introduction to PLINQ | Microsoft Docs"
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
  - "PLINQ queries, introduction to"
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# Introduction to PLINQ
## Qu'est\-ce qu'une requête parallèle ?  
 LINQ \(Langage\-Integrated Query\) a été introduit dans le [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Il comprend un modèle unifié pour interroger une source de données <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> d'une manière sécurisée du point de vue du type.  LINQ to Objects est le nom des requêtes LINQ exécutées sur les collections en mémoire telles que <xref:System.Collections.Generic.List%601> et les tableaux.  Cet article suppose que vous comprenez les notions fondamentales de LINQ.  Pour plus d'informations, consultez [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 PLINQ \(Parallel LINQ\) est une implémentation parallèle du modèle LINQ.  Une requête PLINQ ressemble à bien des égards à une requête non parallèle LINQ to Objects.  Les requêtes PLINQ, tout comme les requêtes séquentielles [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], fonctionnent avec toute source de données <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> en mémoire et ont une exécution différée, ce qui signifie que leur exécution ne démarre pas tant que la requête n'est pas énumérée.  La différence principale est que PLINQ essaie d'utiliser pleinement tous les processeurs du système.  Pour cela, il partitionne la source de données en segments et exécute la requête sur chaque segment sur des threads de travail différents en parallèle sur plusieurs processeurs.  L'exécution parallèle signifie souvent que la requête s'exécute beaucoup plus vite.  
  
 Via l'exécution parallèle, PLINQ peut accomplir une amélioration importante des performances du code hérité de certains genres de requêtes, souvent en ajoutant simplement l'opération de requête <xref:System.Linq.ParallelEnumerable.AsParallel%2A> à la source de données.  Toutefois, le parallélisme peut présenter ses propres complexités et toutes les opérations de requête exécutées ne sont pas plus rapides dans PLINQ.  En réalité, la parallélisation ralentit certaines requêtes.  Par conséquent, vous devez comprendre comment les aspects, tels que le classement, affectent les requêtes parallèles.  Pour plus d'informations, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Cette documentation utilise des expressions lambda pour définir des délégués en PLINQ.  Si vous n'êtes pas familiarisé avec les expressions lambda en C\# ou Visual Basic, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Le reste de cet article donne une vue d'ensemble des principales classes PLINQ et explique comment créer des requêtes PLINQ.  Chaque section contient des liens vers d'autres d'exemples de code et informations détaillées.  
  
## Classe ParallelEnumerable  
 La classe <xref:System.Linq.ParallelEnumerable?displayProperty=fullName> comprend la plupart des fonctionnalités de PLINQ.  Cette classe et les autres types d'espace de noms <xref:System.Linq?displayProperty=fullName> sont compilés dans l'assembly System.Core.dll.  Les projets par défaut C\# et Visual Basic dans Visual Studio référencent l'assembly et importent l'espace de noms.  
  
 <xref:System.Linq.ParallelEnumerable> inclut des implémentations de tous les opérateurs de requête standard pris en charge par LINQ to Objects, mais n'essaie pas de les paralléliser.  Si vous n'êtes pas familiarisé avec [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], consultez [Introduction to LINQ](../../../ocs/visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
 En plus des opérateurs de requête standard, la classe <xref:System.Linq.ParallelEnumerable> contient un ensemble de méthodes permettant certains comportements spécifiques à l'exécution parallèle.  Ces méthodes spécifiques à PLINQ sont répertoriées dans le tableau suivant.  
  
|Opérateur ParallelEnumerable|Description|  
|----------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Point d'entrée de PLINQ.  Spécifie que le reste de la requête doit être parallélisé, si possible.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Spécifie que le reste de la requête doit être exécuté séquentiellement, comme une requête LINQ non parallèle.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Spécifie que PLINQ doit conserver le classement de la séquence source pour le reste de la requête ou jusqu'à ce que le classement soit modifié, par exemple par l'utilisation d'une clause orderby \(Order By en Vlsual Basic\).|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Spécifie que, pour le reste de la requête, PLINQ n'a pas besoin de conserver le classement de la séquence source.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Spécifie que PLINQ doit régulièrement surveiller l'état du jeton d'annulation fourni et annuler l'exécution si cela est demandé.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Spécifie le nombre maximal de processeurs que PLINQ doit utiliser pour paralléliser la requête.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Fournit un commentaire sur la manière dont PLINQ doit, si possible, fusionner des résultats parallèles en une seule séquence sur le thread consommateur.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Spécifie si PLINQ doit paralléliser la requête même quand le comportement par défaut est d'exécuter séquentiellement.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Méthode d'énumération multithread qui, au lieu d'itérer au sein des résultats de la requête, permet aux résultats d'être traités en parallèle sans être d'abord fusionnés sur le thread consommateur.|  
|Surcharge <xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Surcharge unique à PLINQ qui permet l'agrégation intermédiaire sur des partitions locales de thread, plus une fonction d'agrégation finale pour combiner les résultats de toutes les partitions.|  
  
## Modèle déclaratif  
 Lorsque vous écrivez une requête, déclarez PLINQ en appelant la méthode d'extension <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName> sur la source de données, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 La méthode d'extension <xref:System.Linq.ParallelEnumerable.AsParallel%2A> lie les opérateurs de requête suivants, en l'occurrence, `where` et `select`, aux implémentations <xref:System.Linq.ParallelEnumerable?displayProperty=fullName>.  
  
## Modes d'exécution  
 Par défaut, PLINQ est conservateur.  Au moment de l'exécution, l'infrastructure PLINQ analyse la structure totale de la requête.  Si la requête est susceptible de s'accélérer grâce à la parallélisation, PLINQ partitionne la séquence source en tâches pouvant être exécutées simultanément.  S'il est risqué de paralléliser une requête, PLINQ exécute la requête séquentiellement.  Si PLINQ a le choix entre un algorithme parallèle potentiellement coûteux et un algorithme séquentiel non coûteux, il choisit par défaut l'algorithme séquentiel.  Vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et l'énumération <xref:System.Linq.ParallelExecutionMode?displayProperty=fullName> pour indiquer à PLINQ de sélectionner l'algorithme parallèle.  Cela se révèle utile lorsque vous savez, grâce aux tests et mesures effectuées, qu'une requête particulière s'exécute plus rapidement en parallèle.  Pour plus d'informations, consultez [How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## Degré de parallélisme  
 Par défaut, PLINQ utilise un maximum de 64 processeurs sur l'ordinateur hôte.  Vous pouvez indiquer à PLINQ d'utiliser un nombre maximal de processeurs à l'aide de la méthode <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>.  Cela se révèle utile lorsque vous voulez vous assurer que les autres processus qui s'exécutent sur l'ordinateur reçoivent une certaine quantité de temps processeur.  L'extrait de code suivant limite la requête à l'utilisation d'un maximum de deux processeurs.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 Dans les cas où une requête exécute une quantité significative de travail non orienté ordinateur, tel que l'E\/S de fichier, il peut être utile de spécifier un degré de parallélisme supérieur au nombre de cœurs de l'ordinateur.  
  
## Requêtes parallèles classées et non classées  
 Dans certaines requêtes, un opérateur de requête doit produire des résultats qui conservent le classement de la séquence source.  Pour cela, PLINQ fournit l'opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> est différent de <xref:System.Linq.ParallelEnumerable.AsSequential%2A>.  Une séquence <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> est toujours traitée en parallèle, mais ses résultats sont mis en mémoire tampon et triés.  Étant donné que la conservation de l'ordre implique en général un travail supplémentaire, une séquence <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> peut être traitée plus lentement que la séquence <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> par défaut.  L'exécution d'une opération parallèle classée n'est pas toujours plus rapide que l'exécution séquentielle car de nombreux facteurs entrent en jeu.  
  
 L'exemple de code suivant indique comment déclarer la conservation de l'ordre.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Pour plus d'informations, consultez [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## Comparaison entre les requêtes parallèles et les requêtes séquentielles  
 Certaines opérations requièrent que les données sources soient remises de façon séquentielle.  Les opérateurs de requête <xref:System.Linq.ParallelEnumerable> retournent automatiquement au mode séquentiel si nécessaire.  Pour les opérateurs de requête et délégués utilisateurs définis par l'utilisateur qui nécessitent une exécution séquentielle, PLINQ fournit la méthode <xref:System.Linq.ParallelEnumerable.AsSequential%2A>.  Lorsque vous utilisez <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, tous les opérateurs suivants de la requête sont exécutés séquentiellement jusqu'à ce que <xref:System.Linq.ParallelEnumerable.AsParallel%2A> soit appelé de nouveau.  Pour plus d'informations, consultez [How to: Combine Parallel and Sequential LINQ Queries](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## Options de fusion des résultats de requête  
 Lorsqu'une requête PLINQ s'exécute en parallèle, ses résultats de chaque thread de travail doivent être fusionnés sur le thread principal pour être consommés par une boucle `foreach` \(`For Each` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) ou insérés dans une liste ou un tableau.  Dans certains cas, il peut être bénéfique de spécifier un genre particulier d'opération de fusion, par exemple, pour commencer à produire des résultats plus rapidement.  Pour cela, PLINQ prend en charge la méthode <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> et l'énumération <xref:System.Linq.ParallelMergeOptions>.  Pour plus d'informations, consultez [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## Opérateur ForAll  
 Dans les requêtes [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] séquentielles, l'exécution est différée jusqu'à ce que la requête soit énumérée dans une boucle foreach \(`For Each` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) ou en appelant une méthode telle que `foreach` <xref:System.Linq.ParallelEnumerable.ToList%2A>, <xref:System.Linq.ParallelEnumerable.ToArray%2A> ou <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>.  Dans PLINQ, vous pouvez également utiliser `foreach` pour exécuter la requête et itérer au sein des résultats.  Toutefois, `foreach` ne s'exécute pas en parallèle, et par conséquent, requiert que la sortie de toutes les tâches parallèles soit fusionnée dans le thread sur lequel la boucle s'exécute.  En PLINQ, vous pouvez utiliser `foreach` lorsque le classement final des résultats de la requête doit être conservé et chaque fois que vous traitez des résultats séquentiellement, par exemple lorsque vous appelez `Console.WriteLine` pour chaque élément.  Pour une exécution de requête plus rapide lorsque la conservation de l'ordre n'est pas obligatoire et lorsque le traitement des résultats peut être parallélisé, utilisez la méthode <xref:System.Linq.ParallelEnumerable.ForAll%2A> pour exécuter une requête PLINQ.  <xref:System.Linq.ParallelEnumerable.ForAll%2A> n'exécute pas cette dernière étape de fusion.  L'exemple de code suivant montre comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.ForAll%2A>.  La méthode <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> est utilisée ici, car elle est optimisée pour plusieurs threads qui effectuent un ajout simultané sans essayer de supprimer des éléments.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 L'illustration suivante montre la différence entre `foreach` et <xref:System.Linq.ParallelEnumerable.ForAll%2A> quant à exécution de la requête.  
  
 ![ForAll et ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS\_ISVNT\_ALLvsEACH")  
  
## Annulation  
 PLINQ est intégré aux types d'annulation du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. \(Pour plus d'informations, consultez [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)\). Par conséquent, les requêtes PLINQ peuvent être annulées contrairement aux requêtes LINQ to Objects séquentielles.  Pour créer une requête PLINQ annulable, utilisez l'opérateur <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sur la requête et fournissez une instance <xref:System.Threading.CancellationToken> comme argument.  Lorsque la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> du jeton est définie sur true, PLINQ le remarque, arrête le traitement sur tous les threads et lève une <xref:System.OperationCanceledException>.  
  
 Une requête PLINQ peut continuer à traiter des éléments après la définition du jeton d'annulation.  
  
 Pour une plus grande réactivité, vous pouvez également répondre aux requêtes d'annulation dans des délégués utilisateurs de longue durée.  Pour plus d'informations, consultez [How to: Cancel a PLINQ Query](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## Exceptions  
 Lorsqu'une requête PLINQ s'exécute, plusieurs exceptions peuvent être levées en même temps par des threads différents.  Le code servant à gérer l'exception peut se trouver sur un thread différent que le code qui a levé l'exception.  PLINQ utilise le type <xref:System.AggregateException> pour encapsuler toutes les exceptions levées par une requête et marshale ces exceptions sur le thread appelant.  Sur le thread appelant, un seul bloc try\-catch est nécessaire.  Toutefois, vous pouvez itérer au sein de toutes les exceptions encapsulées dans <xref:System.AggregateException> et intercepter celles dont la récupération est sans risque.  Dans de rares cas, les exceptions non encapsulées dans un <xref:System.AggregateException> et les exceptions <xref:System.Threading.ThreadAbortException> également non encapsulées peuvent être levées.  
  
 Lorsque les exceptions sont autorisées à se propager vers le thread joint, il est possible qu'une requête puisse continuer à traiter des éléments après que l'exception a été levée.  
  
 Pour plus d'informations, consultez [How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## Partitionneurs personnalisés  
 Dans certains cas, il est possible d'améliorer les performances des requêtes en écrivant un partitionneur personnalisé qui tire parti de certaines caractéristiques des données sources.  Dans la requête, le partitionneur personnalisé est l'objet énumérable faisant l'objet de la requête.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 PLINQ prend en charge un nombre fixe de partitions \(bien que les données puissent être réaffectées dynamiquement à ces partitions pendant l'exécution de l'équilibrage de charge\).  <xref:System.Threading.Tasks.Parallel.For%2A> et <xref:System.Threading.Tasks.Parallel.ForEach%2A> prennent uniquement en charge le partitionnement dynamique, ce qui signifie que le nombre de partitions change au moment de l'exécution.  Pour plus d'informations, consultez [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## Mesure des performances PLINQ  
 Dans de nombreux cas, une requête peut être parallélisée, mais les surcharges de la configuration de la requête parallèle l'emportent sur les performances gagnées.  Si une requête n'exécute pas beaucoup de calculs ou si la source de données est petite, une requête PLINQ peut se révéler plus lente qu'une requête LINQ to Objects séquentielle.  Vous pouvez utiliser l'analyseur de performances parallèles de Visual Studio Team Server pour comparer les performances des différentes requêtes, trouver des goulots d'étranglement du processeur et déterminer si votre requête s'exécute en parallèle ou séquentiellement.  Pour plus d’informations, consultez [Visualiseur concurrence](../Topic/Concurrency%20Visualizer.md) et [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)