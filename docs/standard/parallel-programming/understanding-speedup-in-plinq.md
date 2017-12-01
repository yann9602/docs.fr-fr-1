---
title: "Fonctionnement de l'accélération dans PLINQ"
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
helpviewer_keywords: PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3373cb6a2c535bd7d42eb062e1f9727952f7cfb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-speedup-in-plinq"></a>Fonctionnement de l'accélération dans PLINQ
L’objectif principal de PLINQ est permettant d’accélérer l’exécution de LINQ aux requêtes d’objets en exécutant les délégués de requête en parallèle sur les ordinateurs multicœurs. PLINQ offre de meilleures performances lorsque le traitement de chaque élément dans une collection source est indépendant, sans aucun état partagé parmi les délégués individuels. Ces opérations sont courantes dans LINQ to Objects et PLINQ et sont souvent appelées «*délicieusement parallèles*», car elles se prêtent facilement à la planification sur plusieurs threads. Toutefois, toutes les requêtes sont constituées entièrement d’opérations délicieusement parallèles ; dans la plupart des cas, une requête concerne certains opérateurs qui soit ne peut pas être parallélisée, ou qui ralentissent l’exécution parallèle. Même avec les requêtes qui sont entièrement délicieusement parallèles, PLINQ doit encore partitionner la source de données et planifier le travail sur les threads, et généralement fusionner les résultats lorsque la requête est terminée. Toutes ces opérations ajoutent au coût de calcul de la parallélisation ; Ces coûts d’ajout de parallélisation sont appelés *surcharge*. Pour optimiser les performances dans une requête PLINQ, vise à optimiser les parties qui sont délicieusement parallèles et de limiter les parties qui nécessitent de surcharge. Cet article fournit des informations qui vous aideront à écrire des requêtes PLINQ aussi efficaces que possible tout en produisant des résultats corrects.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Facteurs qui influent sur les performances des requêtes PLINQ  
 Les sections suivantes répertorie certains des facteurs plus importants qu’impact sur les performances de requête parallèle. Il s’agit d’instructions générales qui eux-mêmes ne sont pas suffisantes pour prédire les performances des requêtes dans tous les cas. Comme toujours, il est important de mesurer les performances réelles des requêtes spécifiques sur les ordinateurs avec une plage de charges et les configurations représentatives.  
  
1.  Coût de calcul de l’ensemble.  
  
     Pour atteindre l’accélération, une requête PLINQ doit avoir suffisamment de travail délicieusement parallèle pour compenser la surcharge. Le travail peut être exprimé comme le coût de calcul de chaque délégué multiplié par le nombre d’éléments dans la collection source. En supposant qu’une opération peut être parallélisée, le plus de calculs coûteux il s’agit, plus la possibilité de l’accélération. Par exemple, si une fonction accepte une milliseconde, une requête séquentielle plus de 1000 éléments prendra une seconde pour effectuer cette opération, tandis qu’une requête parallèle sur un ordinateur doté de quatre cœurs peut prendre uniquement 250 millisecondes. Il en résulte une accélération de 750 millisecondes. Si la fonction nécessitait une seconde à s’exécuter pour chaque élément, puis l’accélération serait de 750 secondes. Si le délégué est très cher, PLINQ peut offrir une accélération significative avec uniquement quelques éléments de la collection source. À l’inverse, petites collections source avec les délégués triviaux ne sont généralement pas bons candidats pour PLINQ.  
  
     Dans l’exemple suivant, queryA est probablement un bon candidat pour PLINQ, en supposant que sa fonction Select implique de nombreuses tâches. queryB n’est probablement pas un bon candidat, car il n’existe pas de suffisamment de travail dans l’instruction Select, et la surcharge de parallélisation compensera la plupart ou la totalité de l’accélération.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2.  Le nombre de cœurs logiques sur le système (degré de parallélisme).  
  
     Ce point est un corollaire évident de la section précédente, les requêtes qui sont délicieusement parallèles s’exécuter plus rapidement sur les ordinateurs avec plusieurs cœurs, car le travail peut être divisé entre davantage de threads simultanés. La quantité globale de l’accélération varie selon le pourcentage de l’ensemble de la requête est redémarrée. Toutefois, ne supposez pas que toutes les requêtes s’exécuteront deux fois plus rapide sur un ordinateur de huit cœurs comme un ordinateur de quatre principaux. Lors du paramétrage des requêtes pour des performances optimales, il est important de mesurer les résultats réels sur les ordinateurs avec différents nombres de cœurs. Ce point est lié au point #1 : jeux de données volumineux est nécessaires pour tirer parti des ressources de calcul supérieures.  
  
3.  Le nombre et le type d’opérations.  
  
     PLINQ fournit l’opérateur AsOrdered pour les situations dans lesquelles il est nécessaire de conserver l’ordre des éléments dans la séquence source. Il existe un coût associé à la commande, mais ce coût est généralement modeste. Opérations GroupBy et Join entraînent également une surcharge. PLINQ offre de meilleures performances lorsqu’elle est autorisée à traiter les éléments de la collection source dans n’importe quel ordre et les passer à l’opérateur suivant dès qu’ils sont prêts. Pour plus d’informations, consultez [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md) (Conservation de l’ordre dans PLINQ).  
  
4.  Le formulaire de l’exécution des requêtes.  
  
     Si vous stockez les résultats d’une requête en appelant ToArray ou ToList, les résultats de tous les threads parallèles doivent être fusionnés dans la structure de données unique. Cela implique un coût de calcul inévitable. De même, si vous itérez les résultats à l’aide d’une boucle foreach (For Each en Visual Basic), les résultats à partir de threads de travail doivent être sérialisés sur le thread de l’énumérateur. Mais si vous souhaitez simplement effectuer une action en fonction du résultat de chaque thread, vous pouvez utiliser la méthode ForAll pour exécuter ce travail sur plusieurs threads.  
  
5.  Le type des options de fusion.  
  
     PLINQ peut être configuré pour sa sortie en mémoire tampon et de produire des segments ou à la fois une fois que le jeu de résultats complet est généré, ou aux résultats individuels de flux de données qu’ils sont produits. Le premier résultat est le temps d’exécution réduit et les derniers résultats de la latence entre les éléments rapportés.  Alors que les options de fusion n’ont pas toujours un impact considérable sur les performances globales de requête, elles peuvent affecter les performances perçues car elles contrôlent la durée pendant laquelle un utilisateur doit attendre à voir les résultats. Pour plus d’informations, consultez l’article [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md) (Options de fusion de PLINQ).  
  
6.  Le type de partitionnement.  
  
     Dans certains cas, une requête PLINQ sur une collection source indexable peut entraîner une charge de travail déséquilibrée. Lorsque cela se produit, vous pourrez peut-être augmenter les performances des requêtes en créant un partitionneur personnalisé. Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Lorsque PLINQ choisit le Mode séquentiel  
 PLINQ essaiera toujours exécuter une requête au moins aussi rapide que la requête s’exécute de manière séquentielle. Bien que PLINQ ne pas la sollicitation en coûteux les délégués de l’utilisateur sont ou si la taille la source d’entrée, il recherche certaines requêtes « formes ». Plus précisément, il recherche des opérateurs de requête ou des combinaisons d’opérateurs qui provoquent généralement une requête à exécuter plus lentement en mode parallèle. Lorsqu’il recherche des formes, PLINQ par défaut revient au mode séquentiel.  
  
 Toutefois, après avoir mesuré les performances d’une requête spécifique, vous pouvez déterminer qu’elle s’exécute plus rapidement en mode parallèle. Dans ce cas, vous pouvez utiliser la <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> indicateur la <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> méthode pour indiquer à PLINQ de paralléliser la requête. Pour plus d’informations, consultez [How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md) (Guide pratique pour spécifier le mode d’exécution dans PLINQ).  
  
 La liste suivante décrit les formes de requêtes PLINQ par défaut s’exécute en mode séquentiel :  
  
-   Requêtes qui contiennent une instruction Select, Where indexée, SelectMany indexée ou ElementAt après un opérateur de tri ou de filtrage qui a supprimé ou réorganisé les indices d’origine.  
  
-   Requêtes qui contiennent un SkipWhile opérateur Take, TakeWhile, ignorer et où les index de la séquence source ne sont pas dans l’ordre d’origine.  
  
-   Requêtes qui contiennent Zip ou SequenceEquals, sauf si une des sources de données a un index ordonné à l’origine et la source de données indexable (autrement dit, un tableau ou un IList(T)).  
  
-   Requêtes qui contiennent Concat, sauf si elle est appliquée aux sources de données indexables.  
  
-   Requêtes qui contiennent Reverse, sauf si appliqué à une source de données indexable.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
