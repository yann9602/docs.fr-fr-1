---
title: "Comment : désencapsuler une tâche imbriquée"
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
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a>Comment : désencapsuler une tâche imbriquée
Vous pouvez retourner une tâche à partir d’une méthode, puis attendre ou continuer à partir de cette tâche, comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Dans l’exemple précédent, le <xref:System.Threading.Tasks.Task%601.Result%2A> propriété est de type `string` (`String` en Visual Basic).  
  
 Toutefois, dans certains scénarios, vous souhaiterez créer une tâche dans une autre tâche, puis retourner la tâche imbriquée. Dans ce cas, le `TResult` de la tâche englobante est lui-même une tâche. Dans l’exemple suivant, la propriété du résultat est un `Task<Task<string>>` en c# ou `Task(Of Task(Of String))` en Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Bien qu’il soit possible d’écrire du code pour désencapsuler la tâche externe et extraire la tâche d’origine et son <xref:System.Threading.Tasks.Task%601.Result%2A> propriété, ce code n’est pas facile à écrire, car vous devez gérer des exceptions et également des demandes d’annulation. Dans ce cas, nous vous recommandons d’utiliser un de le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> méthodes d’extension, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> méthodes peuvent être utilisées pour transformer les `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` en Visual Basic) à un `Task` ou `Task<TResult>` (`Task(Of TResult)` en Visual Basic). La nouvelle tâche entièrement représente la tâche imbriquée interne et inclut l’état d’annulation et toutes les exceptions.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> les méthodes d’extension.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
