---
title: "How to: Unwrap a Nested Task | Microsoft Docs"
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
  - "tasks, how to unwrap nested tasks"
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unwrap a Nested Task
Vous pouvez retourner une tâche à partir d'une méthode, puis attendre ou continuer à partir de cette tâche, comme indiqué dans l'exemple suivant :  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Dans l'exemple précédent, la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> est de type `string` \(`String` en Visual Basic\).  
  
 Toutefois dans certains scénarios, vous pouvez créer une tâche dans une autre tâche, puis retourner la tâche imbriquée.  Dans ce cas, le `TResult` de la tâche englobante est lui\-même une tâche.  Dans l'exemple suivant, la propriété Result est un `Task<Task<string>>` en C\# ou `Task(Of Task(Of String))` en Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Bien que cela soit possible pour écrire le code afin de défaire la tâche externe et extraire la tâche d'origine et sa propriété <xref:System.Threading.Tasks.Task%601.Result%2A>, ce code n'est pas facile à écrire parce que vous devez gérer des exceptions et également des requêtes d'annulation.  Dans cette situation, nous recommandons que vous utilisiez l'une des méthodes d'extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Les méthodes <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> peuvent être utilisées pour transformer tout `Task<Task>` ou `Task<Task<TResult>>` \(`Task(Of Task)` ou `Task(Of Task(Of TResult))` en Visual Basic\) à un `Task` ou `Task<TResult>` \(`Task(Of TResult)` en Visual Basic\).  La nouvelle tâche représente entièrement la tâche imbriquée interne et inclut l'état d'annulation et toutes les exceptions.  
  
## Exemple  
 L'exemple suivant montre comment utiliser les méthodes d'extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## Voir aussi  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=fullName>   
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)