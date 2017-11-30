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
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="4e445-102">Comment : désencapsuler une tâche imbriquée</span><span class="sxs-lookup"><span data-stu-id="4e445-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="4e445-103">Vous pouvez retourner une tâche à partir d’une méthode, puis attendre ou continuer à partir de cette tâche, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e445-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="4e445-104">Dans l’exemple précédent, le <xref:System.Threading.Tasks.Task%601.Result%2A> propriété est de type `string` (`String` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4e445-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="4e445-105">Toutefois, dans certains scénarios, vous souhaiterez créer une tâche dans une autre tâche, puis retourner la tâche imbriquée.</span><span class="sxs-lookup"><span data-stu-id="4e445-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="4e445-106">Dans ce cas, le `TResult` de la tâche englobante est lui-même une tâche.</span><span class="sxs-lookup"><span data-stu-id="4e445-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="4e445-107">Dans l’exemple suivant, la propriété du résultat est un `Task<Task<string>>` en c# ou `Task(Of Task(Of String))` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4e445-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="4e445-108">Bien qu’il soit possible d’écrire du code pour désencapsuler la tâche externe et extraire la tâche d’origine et son <xref:System.Threading.Tasks.Task%601.Result%2A> propriété, ce code n’est pas facile à écrire, car vous devez gérer des exceptions et également des demandes d’annulation.</span><span class="sxs-lookup"><span data-stu-id="4e445-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="4e445-109">Dans ce cas, nous vous recommandons d’utiliser un de le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> méthodes d’extension, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4e445-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="4e445-110">Le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> méthodes peuvent être utilisées pour transformer les `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` en Visual Basic) à un `Task` ou `Task<TResult>` (`Task(Of TResult)` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4e445-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="4e445-111">La nouvelle tâche entièrement représente la tâche imbriquée interne et inclut l’état d’annulation et toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="4e445-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e445-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e445-112">Example</span></span>  
 <span data-ttu-id="4e445-113">L’exemple suivant montre comment utiliser le <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> les méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="4e445-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="4e445-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e445-114">See Also</span></span>  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [<span data-ttu-id="4e445-115">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="4e445-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
