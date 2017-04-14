---
title: "Data Parallelism (Task Parallel Library) | Microsoft Docs"
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
  - "parallelism, data"
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: 25
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 25
---
# Data Parallelism (Task Parallel Library)
Le *parallélisme des données* fait référence aux scénarios dans lesquels la même opération est exécutée de manière simultanée \(autrement dit, en parallèle\) sur les éléments dans une collection source ou un tableau.  Dans les opérations en parallèle de données, la collection source est partitionnée afin que plusieurs threads puissent fonctionner simultanément sur des segments différents.  
  
 La bibliothèque parallèle de tâches prend en charge le parallélisme des données via la classe <xref:System.Threading.Tasks.Parallel?displayProperty=fullName>.  Cette classe fournit des implémentations parallèles basées sur méthode des boucles [for](../Topic/for%20\(C%23%20Reference\).md) et [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) \(`For`  et `For Each` en Visual Basic\).  Vous écrivez la logique de boucle d'une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> de la même manière que pour une boucle séquentielle.  Vous n'avez pas à créer de threads ou d'éléments de travail de file d'attente.  Dans les boucles simples, vous n'avez pas besoin d'acquérir de verrous.  La bibliothèque parallèle de tâches gère tous les travaux de bas niveau pour vous.  Pour des informations détaillées sur l'utilisation d'<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>, téléchargez le document [Modèles de programmation parallèle : présentation et application des modèles parallèles avec le .NET Framework 4](http://www.microsoft.com/download/details.aspx?id=19222).  L'exemple de code suivant montre une boucle `foreach` simple et son équivalent parallèle.  
  
> [!NOTE]
>  Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches.  Si les expressions lambda en C\# ou Visual Basic ne vous sont pas familières, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Quand une boucle parallèle s'exécute, la bibliothèque parallèle de tâches partitionne la source de données afin que la boucle puisse s'exécuter simultanément sur plusieurs parties.  En arrière\-plan, le planificateur de tâches partitionne la tâche en fonction des ressources système et de la charge de travail.  Quand cela lui est possible, le planificateur redistribue le travail entre plusieurs threads et processeurs si la charge de travail est déséquilibrée.  
  
> [!NOTE]
>  Vous pouvez également fournir votre propre partitionneur ou planificateur personnalisé.  Pour plus d'informations, consultez [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) et [Task Schedulers](../Topic/Task%20Schedulers.md).  
  
 Les méthodes <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> ont plusieurs surcharges qui vous permettent d'arrêter ou de quitter l'exécution d'une boucle, de surveiller l'état de la boucle sur d'autres threads, de maintenir l'état local de thread, de finaliser des objets locaux de thread, de contrôler le degré d'accès concurrentiel, etc.  Les types d'assistance qui permettent ces fonctionnalités incluent <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken> et <xref:System.Threading.CancellationTokenSource>.  
  
 Pour plus d'informations, consultez [Modèles de programmation parallèle](http://go.microsoft.com/fwlink/p/?LinkId=265491).  
  
 Le parallélisme des données avec syntaxe déclarative ou de requête est pris en charge par PLINQ.  Pour plus d'informations, consultez [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Explique comment écrire une boucle <xref:System.Threading.Tasks.Parallel.For%2A> sur tout tableau ou collection source <xref:System.Collections.Generic.IEnumerable%601> indexable.|  
|[How to: Write a Simple Parallel.ForEach Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Explique comment écrire une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A> sur toute collection source <xref:System.Collections.Generic.IEnumerable%601>.|  
|[How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/fr-fr/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Explique comment arrêter ou rompre une boucle parallèle afin que tous les threads soient informés de l'action.|  
|[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Explique comment écrire une boucle <xref:System.Threading.Tasks.Parallel.For%2A> dans laquelle chaque thread maintient une variable privée qui n'est pas visible pour les autres threads et comment synchroniser les résultats de tous les threads quand la boucle se termine.|  
|[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|Explique comment écrire une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A> dans laquelle chaque thread maintient une variable privée qui n'est pas visible pour les autres threads et comment synchroniser les résultats de tous les threads quand la boucle se termine.|  
|[How to: Cancel a Parallel.For or ForEach Loop](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Explique comment annuler une boucle parallèle à l'aide d'un <xref:System.Threading.CancellationToken?displayProperty=fullName>.|  
|[How to: Speed Up Small Loop Bodies](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Décrit une façon d'accélérer l'exécution quand un corps de boucle est très petit.|  
|[Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fournit une vue d'ensemble de la bibliothèque parallèle de tâches.|  
|[Parallel Programming](../../../docs/standard/parallel-programming/index.md)|Présente la programmation parallèle dans le .NET Framework.|  
  
## Voir aussi  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)