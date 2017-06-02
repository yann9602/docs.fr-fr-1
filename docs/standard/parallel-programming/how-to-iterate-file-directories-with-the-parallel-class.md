---
title: "Comment&#160;: it&#233;rer les r&#233;pertoires de fichiers avec la classe parall&#232;le | Microsoft Docs"
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
  - "boucles parallèles, comment itérer des répertoires"
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: it&#233;rer les r&#233;pertoires de fichiers avec la classe parall&#232;le
Dans de nombreux cas, l'itération de fichier est une opération qui peut facilement être parallélisée.  La rubrique [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) indique le moyen le plus simple d'effectuer cette tâche dans de nombreux scénarios.  Toutefois, des problèmes peuvent se produire lorsque votre code doit traiter les nombreux types d'exceptions qui peuvent survenir lors de l'accès au système de fichiers.  L'exemple suivant indique une méthode pour faire face à ce problème.  Elle utilise une itération basée sur la pile pour parcourir tous les fichiers et dossiers d'un répertoire spécifié, et permet à votre code d'intercepter et de traiter diverses exceptions.  Évidemment, le choix du traitement des exceptions vous appartient.  
  
## Exemple  
 L'exemple suivant itère les répertoires séquentiellement, mais traite les fichiers en parallèle.  Il s'agit probablement de la méthode la mieux adaptée si vous avez un ratio fichier\/répertoire élevé.  Il est également possible de paralléliser l'itération des répertoires et d'accéder à chaque fichier séquentiellement.  Ce n'est probablement pas très efficace de paralléliser les deux boucles sauf si vous ciblez spécifiquement un ordinateur doté d'un grand nombre de processeurs.  Toutefois, comme dans tous les cas, vous devez tester votre application de manière approfondie afin de déterminer la meilleure méthode.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Dans cet exemple, les E\/S des fichiers sont exécutées en mode synchrone.  Si le nombre de fichiers est élevé ou si les connexions réseau sont lentes, il peut être préférable d'accéder aux fichiers en mode asynchrone.  Vous pouvez combiner les techniques d'E\/S asynchrones avec l'itération parallèle.  Pour plus d'informations, consultez [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 L'exemple utilise la variable locale `fileCount` pour contenir un nombre total le nombre de fichiers traités.  Parce que la variable peut être accessible simultanément par plusieurs tâches, l'accès vers elle est synchronisée en appelant la méthode <xref:System.Threading.Interlocked.Add%2A?displayProperty=fullName>.  
  
 Notez que si une exception est levée dans le thread principal, l'exécution des threads démarrés par la méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A> peut continuer.  Pour arrêter ces threads, vous pouvez définir une variable booléenne dans vos gestionnaires d'exceptions et vérifier sa valeur pour chaque itération de la boucle parallèle.  Si la valeur indique qu'une exception a été levée, utilisez la variable <xref:System.Threading.Tasks.ParallelLoopState> pour arrêter ou quitter la boucle.  Pour plus d'informations, consultez [How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/fr-fr/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).  
  
## Voir aussi  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)