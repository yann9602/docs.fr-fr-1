---
title: "Pièges potentiels avec PLINQ"
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
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a>Pièges potentiels avec PLINQ
Dans de nombreux cas, PLINQ peut fournir des améliorations significatives des performances sur séquentiel requêtes LINQ to Objects. Toutefois, le travail de la parallélisation de l’exécution de requête présente une certaine complexité peut entraîner des problèmes qui, dans du code séquentiel, ne sont que peu ou pas rencontrés. Cette rubrique répertorie les pratiques à éviter lorsque vous écrivez des requêtes PLINQ.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Ne partez pas du principe qu’une boucle parallèle est toujours plus rapide  
 Parfois, la parallélisation entraîne une requête PLINQ s’exécuter plus lentement que son LINQ en équivalent d’objets. La règle empirique de base est que les requêtes qui ont peu d’éléments source et des délégués utilisateurs rapides sont bien en termes d’accélération. Toutefois, étant donné que de nombreux facteurs sont impliqués dans les performances, nous vous recommandons d’évaluer les résultats réels avant de décider s’il faut utiliser PLINQ. Pour plus d’informations, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Éviter d’écrire à des emplacements de mémoire partagés  
 Dans du code séquentiel, il n’est pas rare de lire des variables statiques ou d’écrire dans ces dernières ou dans des champs de classe. Toutefois, l’accès simultané de plusieurs threads à de telles variables entraîne un fort risque d’engorgement. Bien que vous puissiez utiliser des verrous pour synchroniser l’accès à la variable, le coût de synchronisation peut nuire aux performances. Par conséquent, nous vous recommandons d’éviter, ou au moins limiter, l’accès à un état partagé dans une requête PLINQ autant que possible.  
  
## <a name="avoid-over-parallelization"></a>Éviter la surparallélisation  
 À l’aide de la `AsParallel` (opérateur), vous encourez des coûts de partitionnement de la collection source et de synchronisation des threads de travail. Les avantages de la parallélisation sont également limités par le nombre de processeurs de l’ordinateur. L’exécution de plusieurs threads liés au calcul sur un seul processeur ne permet aucune accélération. Par conséquent, vous devez être faites attention de ne pas trop forte paralléliser une requête.  
  
 Le scénario le plus courant dans surparallélisation se produit des requêtes imbriquées, comme indiqué dans l’extrait de code suivant.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 Dans ce cas, il est préférable de paralléliser uniquement la source de données externe (customers), sauf si un ou plusieurs des conditions suivantes s’appliquent :  
  
-   La source de données interne (cust. Commandes) est connu pour être très longue.  
  
-   Vous effectuez un calcul coûteux sur chaque commande. (l’opération montrée dans l’exemple n’est pas coûteuse)  
  
-   Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads produits en parallélisant la requête sur `cust.Orders`.  
  
 Dans tous les cas, le test et la mesure sont la meilleure façon de déterminer la forme de requête optimale. Pour plus d’informations, consultez [Comment : mesurer les performances de requête PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Éviter de faire appel aux méthodes qui ne sont pas thread-safe  
 Écrire des méthodes d’instance non thread-safe à partir d’un PLINQ requête risque d’altération des données qui ne peut-être pas être détectées dans votre programme. Cela peut également entraîner des exceptions. Dans l’exemple suivant, plusieurs threads essaient d’appeler le `Filestream.Write` méthode simultanément, ce qui n'est pas pris en charge par la classe.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limiter les appels aux méthodes qui ne sont pas thread-safe  
 La plupart des méthodes statiques du .NET Framework sont thread-safe et peuvent être appelées à partir de plusieurs threads simultanément. Toutefois, même dans ces cas, la synchronisation impliquée peut entraîner un ralentissement significatif de la requête.  
  
> [!NOTE]
>  Vous pouvez tester ceci vous-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes. Bien que cette méthode est utilisée dans les exemples de documentation à titre de démonstration, ne l’utilisez pas dans les requêtes PLINQ.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Évitez les opérations de tri inutiles  
 Lorsque PLINQ exécute une requête en parallèle, il divise la séquence source en partitions peuvent être exécutées simultanément sur plusieurs threads. Par défaut, l’ordre dans lequel les partitions sont traitées et les résultats sont remis n’est pas prévisible (à l’exception des opérateurs tels que `OrderBy`). Vous pouvez demander à PLINQ de conserver le classement de toute séquence source, mais cela a un impact négatif sur les performances. La meilleure pratique, si possible, consiste à structurer les requêtes afin qu’ils ne reposent pas sur la conservation de l’ordre. Pour plus d’informations, consultez [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md) (Conservation de l’ordre dans PLINQ).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Préférer ForAll à ForEach lorsqu’il est Possible de  
 Bien que PLINQ exécute une requête sur plusieurs threads, si vous consommez les résultats dans un `foreach` boucle (`For Each` en Visual Basic), puis les résultats de requête doivent être fusionnés dans un thread et consultés de façon séquentielle par l’énumérateur. Dans certains cas, il est inévitable ; Toutefois, si possible, utilisez le `ForAll` méthode d’activation de chaque thread de sortir ses propres résultats, par exemple, en écrivant à une collection thread-safe, tel que <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Le même problème s’applique aux <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> en d’autres termes, `source.AsParallel().Where().ForAll(...)` doit être fortement préféré à  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Tenir compte des problèmes d’affinité de thread  
 Certaines technologies, par exemple, les composants STA (Single-Threaded Apartment), Windows Forms et Windows Presentation Foundation (WPF) imposent des restrictions d’affinité de thread qui requièrent l’exécution de code sur un thread spécifique. Par exemple, dans Windows Forms et WPF, un contrôle est uniquement accessible sur le thread sur lequel il a été créé. Si vous essayez d’accéder à l’état partagé d’un contrôle Windows Forms dans une requête PLINQ, une exception est levée si vous exécutez dans le débogueur. (Ce paramètre peut être désactivé.) Toutefois, si votre requête est consommée sur le thread d’interface utilisateur, vous pouvez accéder au contrôle à partir de la `foreach` résultats de la boucle qui énumère la requête, car ce code s’exécute sur un seul thread.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Ne pas supposer que les itérations de ForEach, For et ForAll s’exécutent toujours en parallèle  
 Il est important de garder à l’esprit que les itérations individuelles dans un <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> mai de boucle mais n’avez pas à exécuter en parallèle. Par conséquent, vous devez éviter d’écrire du code dont l’exactitude dépend de l’exécution parallèle d’itérations ou de l’exécution d’itérations dans un ordre particulier.  
  
 Par exemple, ce code est susceptible d’interbloquer :  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 Dans cet exemple, une itération définit un événement que toutes les autres itérations attendent. Aucune des itérations en attente ne peut s’achever tant que l’itération de définition d’événement n’est pas terminée. Toutefois, il est possible que les itérations en attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant que l’itération de définition d’événement ait eu une chance de s’exécuter. Cela provoque un interblocage : l’itération de définition d’événement ne s’exécute jamais et les itérations en attente ne s’activent pas non plus.  
  
 En particulier, une itération de boucle parallèle ne doit jamais attendre une autre itération de la boucle pour progresser. Si la boucle parallèle décide de planifier les itérations de manière séquentielle, mais dans l’ordre inverse, un interblocage se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
