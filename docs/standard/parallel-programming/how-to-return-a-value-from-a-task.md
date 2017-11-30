---
title: "Comment : retourner une valeur à partir d’une tâche"
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
helpviewer_keywords: tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ade2aadc7d76c12c633f84eeb9eced7a637d5df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="8bea4-102">Comment : retourner une valeur à partir d’une tâche</span><span class="sxs-lookup"><span data-stu-id="8bea4-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="8bea4-103">Cet exemple montre comment utiliser le type <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pour retourner une valeur à partir de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bea4-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="8bea4-104">Il nécessite que le répertoire C:\Users\Public\Pictures\Sample Pictures\ existe et qu'il contienne des fichiers.</span><span class="sxs-lookup"><span data-stu-id="8bea4-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bea4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8bea4-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="8bea4-106">La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> bloque le thread appelant jusqu'à ce que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="8bea4-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="8bea4-107">Pour savoir comment passer le résultat d’une <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> à une tâche de continuation, consultez [chaînage des tâches à l’aide de tâches de Continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="8bea4-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bea4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bea4-108">See Also</span></span>  
 [<span data-ttu-id="8bea4-109">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="8bea4-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [<span data-ttu-id="8bea4-110">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="8bea4-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
