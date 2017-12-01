---
title: "Comment : itérer les répertoires de fichiers avec la classe parallèle"
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
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Comment : itérer les répertoires de fichiers avec la classe parallèle
Dans de nombreux cas, le parcours de fichiers est une opération qui peut être facilement mis en parallèle. La rubrique [Comment : itérer les répertoires de fichiers avec PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) montre la façon la plus simple pour effectuer cette tâche pour de nombreux scénarios. Toutefois, des problèmes peuvent se produire lorsque votre code doit traiter les nombreux types d’exceptions qui peuvent survenir lors de l’accès du système de fichiers. L’exemple suivant présente une approche pour le problème. Elle utilise une itération basée sur la pile pour parcourir tous les fichiers et dossiers situés sous un répertoire spécifié, et permet à votre code intercepter et gérer des exceptions différentes. Bien entendu, la façon de gérer les exceptions vous revient.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant itère les répertoires de manière séquentielle, mais traite les fichiers en parallèle. Ceci est probablement la meilleure approche lorsque vous disposez d’un rapport au répertoire de fichiers volumineux. Il est également possible de paralléliser l’itération active et d’accéder à chaque fichier de manière séquentielle. Il n’est probablement pas efficace de paralléliser les boucles, sauf si vous ciblez spécifiquement un ordinateur avec un grand nombre de processeurs. Toutefois, comme dans tous les cas, vous devez tester votre application minutieusement pour déterminer la meilleure approche.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Dans cet exemple, le fichier d’e/s est effectué de façon synchrone. Lors du traitement des fichiers volumineux ou des connexions réseau lentes, il peut être préférable d’accéder aux fichiers de façon asynchrone. Vous pouvez combiner des techniques d’e/s asynchrones avec l’itération parallèle. Pour plus d’informations, consultez [Bibliothèque parallèle de tâches (TPL) et programmation asynchrone](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 L’exemple utilise le `fileCount` variable pour conserver un décompte du nombre total de fichiers traités. Étant donné que la variable peut être accessibles simultanément par plusieurs tâches, l’accès lui est synchronisé en appelant le <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> (méthode).  
  
 Notez que si une exception est levée sur le principal thread, les threads qui sont démarrés par le <xref:System.Threading.Tasks.Parallel.ForEach%2A> méthode peut continuer à s’exécuter. Pour arrêter ces threads, vous pouvez définir une variable booléenne dans vos gestionnaires d’exceptions et vérifier sa valeur sur chaque itération de la boucle parallèle. Si la valeur indique qu’une exception a été levée, utilisez la <xref:System.Threading.Tasks.ParallelLoopState> variable à l’arrêt ou à partir de la boucle. Pour plus d’informations, consultez [Comment : arrêter ou rompre une boucle Parallel.For](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
