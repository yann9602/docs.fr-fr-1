---
title: "Await, opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="da559-102">Await, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da559-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="da559-103">Vous appliquez le `Await` opérateur à un opérande dans une expression lambda ou de méthode asynchrone pour suspendre l’exécution de la méthode jusqu'à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="da559-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="da559-104">La tâche représente un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="da559-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="da559-105">La méthode dans laquelle `Await` utilisé doit avoir un [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="da559-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="da559-106">Une telle méthode, définie à l’aide de la `Async` modificateur et généralement contenant un ou plusieurs `Await` expressions, est appelé un *méthode async*.</span><span class="sxs-lookup"><span data-stu-id="da559-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da559-107">Les mots clés `Async` et `Await` ont été introduites dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="da559-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="da559-108">Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="da559-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="da559-109">En règle générale, la tâche à laquelle vous appliquez le `Await` opérateur est la valeur de retour d’un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](http://go.microsoft.com/fwlink/?LinkId=204847), autrement dit, un <xref:System.Threading.Tasks.Task>ou un <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="da559-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="da559-110">Dans le code suivant, la <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>retourne `getContentsTask`, un `Task(Of Byte())`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="da559-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="da559-111">La tâche est une promesse de produire le tableau d’octets réel lorsque l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="da559-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="da559-112">L'opérateur `Await` est appliqué à `getContentsTask` pour suspendre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé.</span><span class="sxs-lookup"><span data-stu-id="da559-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="da559-113">Entre-temps, le contrôle revient à l'appelant de `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="da559-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="da559-114">Quand `getContentsTask` est terminé, l'expression `Await` s'évalue en tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="da559-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
<span data-ttu-id="da559-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="da559-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="da559-116">Pour un exemple complet, consultez la page [procédure pas à pas : accès Web à l’aide de Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="da559-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="da559-117">Vous pouvez télécharger l’exemple à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) sur le site Web Microsoft.</span><span class="sxs-lookup"><span data-stu-id="da559-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="da559-118">L'exemple est dans le projet AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="da559-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="da559-119">Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task(Of TResult)`, le type de la `Await` expression est TResult.</span><span class="sxs-lookup"><span data-stu-id="da559-119">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="da559-120">Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task`, le `Await` expression ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="da559-120">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="da559-121">L'exemple suivant illustre la différence.</span><span class="sxs-lookup"><span data-stu-id="da559-121">The following example illustrates the difference.</span></span>  
  
<span data-ttu-id="da559-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="da559-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="da559-123">Un `Await` expression ou une instruction ne bloque pas le thread sur lequel il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="da559-123">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="da559-124">Au lieu de cela, elle entraîne le compilateur à inscrire le reste de la méthode async, après le `Await` expression, comme une liaison dans la tâche attendue.</span><span class="sxs-lookup"><span data-stu-id="da559-124">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="da559-125">Le contrôle revient alors à l'appelant de la méthode async.</span><span class="sxs-lookup"><span data-stu-id="da559-125">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="da559-126">Quand la tâche est terminée, elle appelle sa continuation et l’exécution de la méthode async reprend là où elle s’était arrêtée.</span><span class="sxs-lookup"><span data-stu-id="da559-126">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="da559-127">Un `Await` expression peut se produire uniquement dans le corps d’une expression lambda ou de la méthode englobante immédiate marquée par une `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="da559-127">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="da559-128">Le terme *Await* sert à un mot clé uniquement dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="da559-128">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="da559-129">Partout ailleurs, il est interprété en tant qu'identificateur.</span><span class="sxs-lookup"><span data-stu-id="da559-129">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="da559-130">Dans l’expression lambda ou de la méthode async, un `Await` expression ne peut pas se produire dans une expression de requête, dans le `catch` ou `finally` bloquer d’un [essayez... Catch... Enfin](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instruction, dans l’expression de variable de contrôle de boucle d’une `For` ou `For Each` boucle, ou dans le corps d’un [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instruction.</span><span class="sxs-lookup"><span data-stu-id="da559-130">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="da559-131">Exceptions</span><span class="sxs-lookup"><span data-stu-id="da559-131">Exceptions</span></span>  
 <span data-ttu-id="da559-132">La plupart des méthodes async retourne <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="da559-132">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="da559-133">Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final.</span><span class="sxs-lookup"><span data-stu-id="da559-133">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="da559-134">L'opérateur `Await` accède à ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="da559-134">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="da559-135">Si vous attendez une méthode async retournant des tâches qui lève une exception, l'opérateur `Await` lève de nouveau l'exception.</span><span class="sxs-lookup"><span data-stu-id="da559-135">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="da559-136">Si vous attendez une méthode async retournant des tâches qui est annulée, la `Await` opérateur lève à nouveau une <xref:System.OperationCanceledException>.</xref:System.OperationCanceledException></span><span class="sxs-lookup"><span data-stu-id="da559-136">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="da559-137">Une tâche qui se trouve dans un état d’erreur peut refléter plusieurs exceptions.</span><span class="sxs-lookup"><span data-stu-id="da559-137">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="da559-138">Par exemple, la tâche peut être le résultat d’un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="da559-138">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="da559-139">Quand vous attendez une telle tâche, l’opération await lève à nouveau une seule des exceptions.</span><span class="sxs-lookup"><span data-stu-id="da559-139">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="da559-140">Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.</span><span class="sxs-lookup"><span data-stu-id="da559-140">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="da559-141">Pour obtenir des exemples de gestion des erreurs dans les méthodes asynchrones, consultez [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da559-141">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da559-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="da559-142">Example</span></span>  
 <span data-ttu-id="da559-143">L'exemple Windows Forms suivant illustre l'utilisation de `Await` dans une méthode async, `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="da559-143">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="da559-144">Comparez le comportement de cette méthode avec celui de `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="da559-144">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="da559-145">Sans un `Await` (opérateur), `WaitSynchronously` s’exécute de façon synchrone en dépit de l’utilisation de la `Async` modificateur dans sa définition et un appel à <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>dans son corps.</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="da559-145">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> in its body.</span></span>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="da559-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da559-146">See Also</span></span>  
 <span data-ttu-id="da559-147">[Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="da559-147">[Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="da559-148"> [Procédure pas à pas : Accès Web en utilisant Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="da559-148"> [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="da559-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span><span class="sxs-lookup"><span data-stu-id="da559-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span></span>
