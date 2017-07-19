---
title: "Potential Pitfalls with PLINQ | Microsoft Docs"
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
  - "PLINQ queries, pitfalls"
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Potential Pitfalls with PLINQ
Dans de nombreux cas, PLINQ peut fournir une amélioration des performances significative sur des requêtes LINQ to Objects séquentielles.  Toutefois, la mise en parallèle de l'exécution de la requête présente une certaine complexité pouvant mener à des problèmes qui, dans du code séquentiel, ne sont que peu voire jamais rencontrés.  Cette rubrique répertorie les pratiques à éviter lorsque vous écrivez des requêtes PLINQ.  
  
## Parallèle n'est pas forcément synonyme de rapidité  
 Le parallélisation rend parfois l'exécution de la requête PLINQ plus lente que son équivalent LINQ to Objects.  La règle empirique de base est que les requêtes qui ont peu d'éléments source et des délégués utilisateurs rapides sont beaucoup moins susceptibles de s'accélérer.  Toutefois, étant donné que de nombreux facteurs sont impliqués dans les performances, il est recommandé d'évaluer les résultats réels avant de décider s'il est nécessaire d'utiliser PLINQ.  Pour plus d'informations, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Éviter d'écrire dans les zones de mémoire partagées  
 Dans du code séquentiel, il n'est pas rare de lire ou d'écrire dans les variables statiques ou les champs de classe.  Toutefois, lorsque plusieurs threads accèdent simultanément à de telles variables, les conditions de concurrence sont favorisées.  Bien qu'il soit possible d'utiliser des verrous pour synchroniser l'accès à la variable, le coût de synchronisation peut réduire les performances.  Par conséquent, il est recommandé d'éviter, ou du moins de limiter autant que possible, l'accès à l'état partagé dans une requête PLINQ.  
  
## Éviter la surparallélisation  
 En utilisant l'opérateur `AsParallel`, vous entraînez des coûts de partitionnement de la collection source et de synchronisation des threads de travail.  Les avantages de la parallélisation sont également limités par le nombre de processeurs de l'ordinateur.  L'exécution de plusieurs threads orientés ordinateur sur un seul processeur n'accélère pas l'exécution.  Par conséquent, veillez à éviter la surparallélisation des requêtes.  
  
 La surparallélisation se produit le plus souvent dans des sous\-requêtes, comme l'indique l'extrait de code suivant.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 Dans ce cas, il vaut mieux paralléliser uniquement la source de données externe \(customers\) à moins qu'une ou plusieurs des conditions suivantes ne s'appliquent :  
  
-   La source de données interne \(cust.Orders\) est connue pour être très longue.  
  
-   Vous exécutez un calcul coûteux sur chaque ordre \(l'opération affichée dans cet exemple n'est pas coûteuse\)  
  
-   Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads qui seront produits en parallélisant la requête sur `cust.Orders`.  
  
 Dans tous les cas, la meilleure méthode pour déterminer la forme de requête optimale est de la tester et la mesurer.  Pour plus d'informations, consultez [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## Éviter les appels à des méthodes non thread\-safe  
 L'écriture dans des méthodes d'instance non thread\-safe depuis une requête PLINQ peut mener à des données endommagées, susceptibles de ne pas être détectées dans votre programme.  Elle peut également provoquer des exceptions.  Dans l'exemple suivant, plusieurs threads essaient d'appeler simultanément la méthode `Filestream.Write`, qui n'est pas prise en charge par la classe.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## Limiter les appels à des méthodes thread\-safe  
 La plupart des méthodes statiques du .NET Framework sont thread\-safe et peuvent être appelées simultanément par plusieurs threads.  Toutefois, même dans ce cas\-là, la synchronisation impliquée peut mener à un ralentissement significatif de la requête.  
  
> [!NOTE]
>  Vous pouvez tester ceci vous\-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes.  Bien que cette méthode soit utilisée à des fins de démonstration dans les exemples de documentation, ne l'utilisez pas dans les requêtes PLINQ.  
  
## Éviter les opérations de classement non nécessaires  
 Lorsque PLINQ exécute une requête en parallèle, il divise simultanément la séquence source en partitions pouvant être exécutées simultanément sur plusieurs threads.  Par défaut, l'ordre dans lequel les partitions sont traitées et les résultats sont remis n'est pas prévisible \(sauf pour les opérateurs tels que `OrderBy`\).  Vous pouvez indiquer à PLINQ de conserver le classement de toute séquence source, mais cela aura un impact négatif sur les performances.  La meilleure pratique, lorsque cela est possible, est de structurer les requêtes afin qu'elles ne comptent pas sur la conservation de l'ordre.  Pour plus d'informations, consultez [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## Préférer ForAll à ForEach dans la mesure du possible  
 Bien que PLINQ exécute une requête sur plusieurs threads, si vous consommez les résultats dans une boucle `foreach` \(`For Each` en Visual Basic\), les résultats de la requête doivent être fusionnés dans un thread et consultés de façon séquentielle par l'énumérateur.  Dans certains cas, cela est inévitable ; toutefois, dès que possible, utilisez la méthode `ForAll` pour permettre à chaque thread de sortir ses propres résultats, par exemple, en écrivant dans une collection thread\-safe telle que <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>.  
  
 Le même problème s'applique à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>. En d'autres termes, `source.AsParallel().Where().ForAll(...)` doit être très préférable à  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## Connaître les problèmes d'affinité de thread  
 Certaines technologies, telles que l'interopérabilité COM pour les composants STA, Windows Forms et Windows Presentation Foundation \(WPF\), imposent des restrictions d'affinité de thread qui nécessitent que le code soit exécuté sur un thread spécifique.  Par exemple, un contrôle est accessible uniquement sur le thread sur lequel il a été créé dans Windows Forms et WPF.  Si vous tentez d'accéder à l'état partagé d'un contrôle Windows Forms dans une requête PLINQ, une exception est déclenchée si le débogueur est en cours d'exécution. \(ce paramètre peut être désactivé\) Toutefois, si votre requête est consommée sur le thread d'interface utilisateur, vous pouvez accéder au contrôle de la boucle `foreach` qui énumère les résultats de la requête car ce code s'exécute sur un seul thread.  
  
## Les itérations de ForEach, For et ForAll ne s'exécutent pas forcément toujours en parallèle  
 Il est important de ne pas oublier que les itérations individuelles dans une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> peuvent s'exécuter en parallèle, mais n'ont aucune obligation de le faire.  Par conséquent, vous devez éviter d'écrire du code dont l'exactitude dépend de l'exécution parallèle d'itérations ou de l'exécution d'itérations dans un ordre particulier.  
  
 Par exemple, ce code risque l'interblocage :  
  
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
  
 Dans cet exemple, une itération définit un événement, et toutes les autres itérations attendent l'événement.  Aucune des itérations en cours d'attente ne peut se terminer tant que l'itération définissant l'événement ne l'est pas elle\-même.  Toutefois, il est possible que les itérations en cours d'attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant la fin de l'exécution de l'itération définissant l'événement.  Cela provoque un interblocage, autrement dit, l'itération définissant l'événement ne s'exécutera jamais et les itérations en attente ne se réveilleront jamais.  
  
 En particulier, une itération d'une boucle parallèle ne doit jamais attendre une autre itération de la boucle pour poursuivre sa progression.  Si la boucle parallèle décide de planifier les itérations séquentiellement mais dans l'ordre opposé, un interblocage se produira.  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)