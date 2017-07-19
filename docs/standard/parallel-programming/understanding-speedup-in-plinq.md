---
title: "Understanding Speedup in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, performance tuning"
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Understanding Speedup in PLINQ
L'objectif principal de PLINQ consiste à accélérer l'exécution des requêtes LINQ to Objects en exécutant les délégués de requête en parallèle sur les ordinateurs multicœurs.  PLINQ s'exécute au mieux lorsque le traitement de chaque élément dans une collection source est indépendant, avec un état non partagé parmi les délégués individuels.  Les opérations de ce type sont courantes dans LINQ to Objects et PLINQ et sont souvent appelées « *délicieusement parallèles* » parce qu'elles se prêtent facilement à la planification sur plusieurs threads.  Toutefois, toutes les requêtes ne sont pas entièrement composées d'opérations délicieusement parallèles ; dans la plupart des cas, une requête concerne quelques opérateurs qui ne peuvent pas non plus être parallélisés, ou qui ralentissent l'exécution parallèle.  Et même avec les requêtes qui sont entièrement délicieusement parallèles, PLINQ doit encore partitionner la source de données et planifier le travail sur les threads et généralement fusionner les résultats lorsque la requête se termine.  Toutes ces opérations s'ajoutent au coût de calcul de parallélisation ; ces coûts d'ajout de parallélisation sont appelés coûts de *surcharge*.  Pour atteindre les performances optimales dans une requête PLINQ, l'objectif est d'optimiser les parties qui sont délicieusement parallèles et de limiter les parties qui nécessitent de la surcharge.  Cet article fournit des informations qui vous aideront à écrire des requêtes PLINQ aussi efficaces que possible tout en produisant des résultats corrects.  
  
## Facteurs qui ont une incidence sur la performance des requêtes PLINQ  
 Les sections suivantes répertorient quelques\-uns des facteurs les plus importants qui ont une incidence sur les performances des requêtes parallèles.  Il s'agit d'instructions générales qui, à elles seules, ne suffisent pas à prédire les performances des requêtes dans tous les cas.  Comme toujours, il est important de mesurer la performance réelle des requêtes spécifiques sur les ordinateurs avec une plage de configurations et de charges représentatives.  
  
1.  Coût de calcul du travail global.  
  
     Pour atteindre l'accélération, une requête PLINQ doit comporter suffisamment de travail délicieusement parallèle pour compenser la surcharge.  Le travail peut être exprimé comme le coût de calcul de chaque délégué multiplié par le nombre d'éléments dans la collection source.  En supposant qu'une opération puisse être parallélisée, plus elle sollicite de ressources informatiques, plus importante sera l'accélération.  Par exemple, si une fonction s'exécute en une milliseconde, une requête séquentielle sur plus de 1 000 éléments prendra une seconde pour exécuter cette opération, alors qu'une requête parallèle sur un ordinateur doté de quatre cœurs pourrait ne durer que 250 millisecondes.  Cela permet d'obtenir une accélération de 750 millisecondes.  Si la fonction nécessitait une seconde pour s'exécuter pour chaque élément, alors l'accélération serait de 750 secondes.  Si le délégué est très cher, PLINQ peut offrir une accélération significative avec uniquement quelques éléments dans la collection source.  Inversement, les petites collections source avec les délégués triviaux ne sont généralement pas de bons candidats pour PLINQ.  
  
     Dans l'exemple suivant, le queryA est probablement un bon exemple de PLINQ, considérant que sa fonction de sélection implique beaucoup de travail. Le queryB n'est probablement pas un bon exemple parce qu'il n'y a pas assez de travail dans le relevé de sélection, et la surcharge de la parallélisation compensera la plupart si ce n'est la totalité des speedup.  
  
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
  
2.  Nombre de cœurs logiques sur le système \(degré de parallélisme\).  
  
     Ce point est un corollaire évident de la section précédente ; les requêtes qui sont délicieusement parallèles s'exécutent plus rapidement sur les ordinateurs qui sont dotés d'un nombre plus importants de cœurs parce que le travail peut être réparti sur un nombre plus important de threads simultanés.  La somme totale d'accélération dépend du pourcentage de travail global de la requête qui est parallélisable.  Toutefois, ne supposez pas que toutes les requêtes s'exécuteront deux fois plus rapidement sur un ordinateur à huit cœurs que sur un ordinateur à quatre cœurs.  Lorsque vous réglez des requêtes afin d'obtenir des performances optimales, il est important de mesurer les résultats réels sur les ordinateurs dotés d'un nombre différent de cœurs.  Ce point est lié au point n°1 : des groupes de données plus importants sont nécessaires pour tirer parti de ressources de calcul supérieures.  
  
3.  Nombre et genres d'opérations en attente.  
  
     PLINQ fournit l'opérateur AsOrdered pour les situations pour lesquelles il est nécessaire de maintenir l'ordre des éléments dans la séquence source.  Ce classement engendre un coût, mais ce coût est généralement modeste.  Les opérations GroupBy et Join entraînent également une surcharge.  PLINQ s'exécute le mieux lorsqu'il est autorisé à traiter des éléments dans la collection source dans n'importe quel ordre, et les passe à l'opérateur suivant dès qu'ils sont prêts.  Pour plus d'informations, consultez [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  Formulaire d'exécution de la requête.  
  
     Si vous stockez les résultats d'une requête en appelant ToArray ou ToList, les résultats de tous les threads parallèles doivent être fusionnés dans la structure de données unique.  Cela implique un coût de calcul inévitable.  De même, si vous itérez les résultats à l'aide d'une boucle foreach \(For Each en Visual Basic\), les résultats des threads de travail doivent être sérialisés sur le thread énumérateur.  Mais si vous souhaitez juste exécuter quelque action en fonction du résultat de chaque thread, vous pouvez utiliser la méthode ForAll pour exécuter ce travail sur plusieurs threads.  
  
5.  Type d'options de fusion.  
  
     PLINQ peut être configuré pour mettre en mémoire tampon sa sortie et en produire des segments ou la totalité après avoir produit le jeu de résultats entier, ou enfin transmettre en continu des résultats individuels à mesure qu'ils sont produits.  Le premier résultat représente le temps d'exécution réduit et les derniers résultats représentent la latence entre les éléments produits.  Tandis que les options de fusion n'ont pas toujours une incidence majeure sur les performances globales de la requête, elles peuvent affecter les performances perçues dans la mesure où elles contrôlent la durée d'attente d'un utilisateur avant consultation des résultats.  Pour plus d'informations, consultez [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  Genre de partitionnement.  
  
     Dans certains cas, une requête PLINQ sur une collection source indexable peut provoquer une charge de travail déséquilibrée.  Lorsque cela se produit, vous pouvez être en mesure d'augmenter les performances de la requête en créant un partitionneur personnalisé.  Pour plus d'informations, consultez [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## Lorsque PLINQ choisit le mode séquentiel  
 PLINQ essaiera toujours d'exécuter une requête au moins aussi rapidement que si la requête s'exécutait de manière séquentielle.  Bien que PLINQ ne contrôle pas la sollicitation en ressources informatiques des délégués d'utilisateur ou la taille de la source d'entrée, il recherche certaines « formes » de requête. Spécifiquement, il recherche des opérateurs de requête ou des combinaisons d'opérateurs qui, en général, entraînent le ralentissement de l'exécution d'une requête en mode parallèle.  Lorsqu'il recherche des formes de ce type, PLINQ revient par défaut au mode séquentiel.  
  
 Toutefois, après avoir mesuré les performances d'une requête spécifique, vous pouvez déterminer qu'elle s'exécute plus rapidement en mode parallèle.  Dans ces cas\-là, vous pouvez utiliser les indicateurs <xref:System.Linq.ParallelExecutionMode?displayProperty=fullName> via la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> pour indiquer à PLINQ de paralléliser la requête.  Pour plus d'informations, consultez [How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 La liste suivante décrit les formes de requêtes que PLINQ exécutera par défaut en mode séquentiel :  
  
-   Requêtes contenant une clause Select, Where indexée, SelectMany indexée ou ElementAt après un opérateur de classement ou de filtrage qui a supprimé ou réorganisé des index d'origine.  
  
-   Requêtes qui contiennent un opérateur Take, TakeWhile, Skip ou SkipWhile et dont les index dans la séquence source ne figurent pas dans l'ordre d'origine.  
  
-   Requêtes qui contiennent Zip ou SequenceEquals, à moins que l'une des sources de données ait un index classé à l'origine et que l'autre source de données soit indexable \(c.\-à\-d. un tableau ou un IList\(T\)\).  
  
-   Requêtes qui contiennent Concat, à moins qu'il ne s'applique aux sources de données indexables.  
  
-   Requêtes qui contiennent Reverse, à moins qu'il ne s'applique à une source de données indexable.  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)