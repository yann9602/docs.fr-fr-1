---
title: "How to: Return a Value from a Task | Microsoft Docs"
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
  - "tasks, how to return a value"
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Return a Value from a Task
Cet exemple montre comment utiliser le type <xref:System.Threading.Tasks.Task%601?displayProperty=fullName> pour retourner une valeur à partir de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.  Il nécessite que le répertoire C:\\Users\\Public\\Pictures\\Sample Pictures\\ existe et qu'il contienne des fichiers.  
  
## Exemple  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> bloque le thread appelant jusqu'à ce que la tâche se termine.  
  
 Pour savoir comment passer le résultat d'une <xref:System.Threading.Tasks.Task%601?displayProperty=fullName> à une tâche de continuation, consultez [Chaînage des tâches à l'aide de tâches de continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## Voir aussi  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)