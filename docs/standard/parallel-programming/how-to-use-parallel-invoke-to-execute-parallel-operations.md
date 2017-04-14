---
title: "How to: Use Parallel.Invoke to Execute Parallel Operations | Microsoft Docs"
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
  - "task parallelism in .NET"
  - "parallel programming, task parallelism"
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# How to: Use Parallel.Invoke to Execute Parallel Operations
Cet exemple indique comment paralléliser des opérations à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A> dans la bibliothèque parallèle de tâches.  Trois opérations sont effectuées sur la source de données partagée.  Étant donné qu'aucune des opérations ne modifie la source, elles peuvent être exécutées en parallèle de manière simple.  
  
> [!NOTE]
>  Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches.  Si les expressions lambda en C\# ou Visual Basic ne vous sont pas familières, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## Exemple  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Notez qu'avec <xref:System.Threading.Tasks.Parallel.Invoke%2A>, vous exprimez seulement quelles actions doivent s'exécuter simultanément ; le runtime gère tous les détails de planification de threads, notamment la mise à l'échelle automatique du nombre de cœurs présents sur l'ordinateur hôte.  
  
 Cet exemple parallélise les opérations et non les données.  Vous pouvez également paralléliser les requêtes LINQ à l'aide de PLINQ et exécuter les requêtes séquentiellement.  Vous pouvez aussi paralléliser les données à l'aide de PLINQ.  Une autre option consiste à paralléliser à la fois les requêtes et les tâches.  Bien que la surcharge résultante diminue les performances des ordinateurs hôtes avec un nombre réduit de processeurs, cela permettrait une bien meilleure mise à l'échelle des ordinateurs avec de nombreux processeurs.  
  
## Compilation du code  
  
-   Copiez et collez l'exemple entier dans un projet Microsoft Visual Studio 2010 et appuyez sur F5.  
  
## Voir aussi  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [How to: Wait on One or More Tasks to Complete](../Topic/How%20to:%20Wait%20on%20One%20or%20More%20Tasks%20to%20Complete.md)   
 [How to: Cancel a Task and Its Children](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)