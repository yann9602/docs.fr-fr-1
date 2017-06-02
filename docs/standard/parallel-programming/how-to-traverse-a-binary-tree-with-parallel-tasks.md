---
title: "How to: Traverse a Binary Tree with Parallel Tasks | Microsoft Docs"
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
  - "tasks, how to traverse a tree"
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Traverse a Binary Tree with Parallel Tasks
L'exemple suivant montre deux utilisations des tâches parallèles pour parcourir une arborescence de données.  La création de l'arborescence elle\-même correspond à un exercice.  
  
## Exemple  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Les deux méthodes indiquées sont équivalentes du point de vue fonctionnel.  En utilisant la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> pour créer et exécuter des tâches, vous récupérez un handle des tâches pouvant être utilisé pour attendre les tâches et gérer des exceptions.  
  
## Voir aussi  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)