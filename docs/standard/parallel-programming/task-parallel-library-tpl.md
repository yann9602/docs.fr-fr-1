---
title: "Task Parallel Library (TPL) | Microsoft Docs"
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
  - ".NET, concurrency in"
  - ".NET, parallel programming in"
  - "Parallel Programming"
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: 37
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 37
---
# Task Parallel Library (TPL)
La bibliothèque parallèle de tâches est un ensemble de types publics et d'API dans les espaces de noms <xref:System.Threading?displayProperty=fullName> et <xref:System.Threading.Tasks?displayProperty=fullName>.  L'objectif de la bibliothèque parallèle de tâches est d'accroître la productivité des développeurs en simplifiant le processus d'ajout du parallélisme et de l'accès concurrentiel aux applications.  La bibliothèque parallèle de tâches met à l'échelle dynamiquement le degré d'accès concurrentiel pour utiliser plus efficacement tous les processeurs disponibles.  De plus, la bibliothèque parallèle de tâches gère le partitionnement du travail, la planification de threads sur le <xref:System.Threading.ThreadPool>, la prise en charge de l'annulation, la gestion d'état et d'autres détails de bas niveau.  L'utilisation de la bibliothèque parallèle de tâches vous permet de maximiser les performances de votre code tout en vous concentrant sur le travail que votre programme doit accomplir.  
  
 À partir du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la bibliothèque parallèle de tâches est la meilleure méthode pour écrire le code multithread et parallèle.  Toutefois, tout le code est pas approprié pour la parallélisation ; par exemple, si une boucle exécute uniquement une petite quantité de travail sur chaque itération ou ne s'exécute que pour un nombre limité d'itérations, la charge mémoire de la parallélisation peut ralentir l'exécution du code.  En outre, comme tout code multithread, la parallélisation rend l'exécution du programme plus complexe.  Même si la bibliothèque parallèle de tâches simplifie les scénarios multithread, il est recommandé de connaître les notions fondamentales des concepts de threading, tels que les verrous, les interblocages et les conditions de concurrence critique, afin de pouvoir utiliser efficacement la bibliothèque parallèle de tâches.  
  
## Rubriques connexes  
  
|||  
|-|-|  
|Titre|Description|  
|[Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Décrit comment créer des boucles parallèles `for` et `foreach` \(`For` et `For Each` en Visual Basic\).|  
|[Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Décrit comment créer et exécuter implicitement des tâches à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> ou explicitement en utilisant des objets <xref:System.Threading.Tasks.Task> directement.|  
|[Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Explique comment utiliser les composants de flux de données dans la bibliothèque de flux de données de TPL pour effectuer plusieurs opérations qui doivent communiquer entre elles ou pour traiter les données lorsqu'elles sont disponibles.|  
|[Using TPL with Other Asynchronous Patterns](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Décrit comment utiliser la bibliothèque parallèle de tâches avec d'autres modèles asynchrones dans .NET.|  
|[Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Décrit des pièges courants et la manière de les éviter.|  
|[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Décrit comment atteindre le parallélisme des données avec les requêtes LINQ.|  
|[Parallel Programming](../../../docs/standard/parallel-programming/index.md)|Nœud de niveau supérieur pour la programmation parallèle .NET.|  
  
## Voir aussi  
 [Exemples de programmation parallèle avec .NET Framework](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)