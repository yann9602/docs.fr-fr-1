---
title: "Utilisation du modèle asynchrone basé sur les tâches"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90b2a36f0e6bf06b0fefe2191d5b17c9c07d1588
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="e131d-102">Utilisation du modèle asynchrone basé sur les tâches</span><span class="sxs-lookup"><span data-stu-id="e131d-102">Consuming the Task-based Asynchronous Pattern</span></span>
<span data-ttu-id="e131d-103">Lorsque vous utilisez le modèle asynchrone basé sur les tâches (TAP) pour travailler avec des opérations asynchrones, vous pouvez utiliser des rappels pour terminer l’attente sans blocage.</span><span class="sxs-lookup"><span data-stu-id="e131d-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="e131d-104">Pour les tâches, cela est possible via les méthodes telles que <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e131d-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e131d-105">La prise en charge asynchrone basée sur le langage masque les rappels en permettant aux opérations asynchrones d’être attendues dans le flux de contrôle normal, et le code généré par le compilateur fournit cette même prise en charge au niveau de l’API.</span><span class="sxs-lookup"><span data-stu-id="e131d-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>  
  
## <a name="suspending-execution-with-await"></a><span data-ttu-id="e131d-106">Suspension de l’exécution avec Await</span><span class="sxs-lookup"><span data-stu-id="e131d-106">Suspending Execution with Await</span></span>  
 <span data-ttu-id="e131d-107">En commençant par le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vous pouvez utiliser la [await](~/docs/csharp/language-reference/keywords/await.md) mot clé en c# et la [opérateur Await](~/docs/visual-basic/language-reference/operators/await-operator.md) en Visual Basic pour attendre de façon asynchrone <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> objets.</span><span class="sxs-lookup"><span data-stu-id="e131d-107">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="e131d-108">Lorsque vous êtes en attente d’un <xref:System.Threading.Tasks.Task>, le `await` expression est de type `void`.</span><span class="sxs-lookup"><span data-stu-id="e131d-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="e131d-109">Lorsque vous êtes en attente d’un <xref:System.Threading.Tasks.Task%601>, le `await` expression est de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="e131d-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="e131d-110">Une expression `await` doit se produire dans le corps d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="e131d-111">Pour plus d’informations sur la prise en charge des langages C# et Visual Basic dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez les spécifications des langages C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e131d-111">For more information about C# and Visual Basic language support in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see the C# and Visual Basic language specifications.</span></span>  
  
 <span data-ttu-id="e131d-112">En arrière-plan, la fonctionnalité await installe un rappel sur la tâche à l’aide d’une continuation.</span><span class="sxs-lookup"><span data-stu-id="e131d-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="e131d-113">Ce rappel reprend la méthode asynchrone au point d’interruption.</span><span class="sxs-lookup"><span data-stu-id="e131d-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="e131d-114">Lorsque la méthode asynchrone est reprise, si l’opération attendue s’est terminée avec succès et a été un <xref:System.Threading.Tasks.Task%601>, ses `TResult` est retourné.</span><span class="sxs-lookup"><span data-stu-id="e131d-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="e131d-115">Si le <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée sur le <xref:System.Threading.Tasks.TaskStatus.Canceled> état, un <xref:System.OperationCanceledException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="e131d-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="e131d-116">Si le <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée sur le <xref:System.Threading.Tasks.TaskStatus.Faulted> d’état, l’exception qui a entraîné une erreur est levée.</span><span class="sxs-lookup"><span data-stu-id="e131d-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="e131d-117">Une `Task` peut échouer à cause de plusieurs exceptions, mais seule une de ces exceptions est propagée.</span><span class="sxs-lookup"><span data-stu-id="e131d-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="e131d-118">Toutefois, le <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriété retourne un <xref:System.AggregateException> exception qui contient toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="e131d-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>  
  
 <span data-ttu-id="e131d-119">Si un contexte de synchronisation (<xref:System.Threading.SynchronizationContext> objet) est associée au thread qui a été l’exécution de la méthode asynchrone au moment de la suspension (par exemple, si le <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> propriété n’est pas `null`), la méthode asynchrone reprend sur ce même contexte de synchronisation à l’aide du contexte de <xref:System.Threading.SynchronizationContext.Post%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e131d-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="e131d-120">Sinon, elle s’appuie sur le Planificateur de tâches (<xref:System.Threading.Tasks.TaskScheduler> objet) qui était actif au moment de la suspension.</span><span class="sxs-lookup"><span data-stu-id="e131d-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="e131d-121">En règle générale, il s’agit du Planificateur de tâches par défaut (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), qui cible le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="e131d-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="e131d-122">Le planificateur de tâches détermine si l’opération asynchrone attendue doit reprendre où elle s’est terminée ou si la reprise doit être planifiée.</span><span class="sxs-lookup"><span data-stu-id="e131d-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="e131d-123">Le planificateur par défaut permet généralement à la continuation de s’exécuter sur le thread qui a effectué l’opération attendue.</span><span class="sxs-lookup"><span data-stu-id="e131d-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>  
  
 <span data-ttu-id="e131d-124">Lorsqu’une méthode asynchrone est appelée, elle exécute simultanément le corps de la fonction jusqu'à la première expression await sur une instance prenant en charge await qui n’est pas encore terminée. À ce moment, l’appel retourne à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e131d-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="e131d-125">Si la méthode asynchrone ne renvoie pas `void`, un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> est retourné pour représenter le calcul en cours.</span><span class="sxs-lookup"><span data-stu-id="e131d-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="e131d-126">Dans une méthode asynchrone non void, si une instruction return est rencontrée, ou la fin du corps de méthode, la tâche est terminée dans le <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> état final.</span><span class="sxs-lookup"><span data-stu-id="e131d-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="e131d-127">Si une exception non gérée provoque quitter le corps de la méthode asynchrone du contrôle, la tâche se termine à la <xref:System.Threading.Tasks.TaskStatus.Faulted> état.</span><span class="sxs-lookup"><span data-stu-id="e131d-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="e131d-128">Si cette exception est une <xref:System.OperationCanceledException>, la tâche se termine à la place de la <xref:System.Threading.Tasks.TaskStatus.Canceled> état.</span><span class="sxs-lookup"><span data-stu-id="e131d-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="e131d-129">De cette manière, la publication du résultat ou de l’exception a finalement lieu.</span><span class="sxs-lookup"><span data-stu-id="e131d-129">In this manner, the result or exception is eventually published.</span></span>  
  
 <span data-ttu-id="e131d-130">Il existe plusieurs variations importantes de ce comportement.</span><span class="sxs-lookup"><span data-stu-id="e131d-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="e131d-131">Pour des raisons de performances, si une tâche est déjà terminée au moment où la tâche est attendue avec await, le contrôle n’est pas transmis et la fonction continue à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="e131d-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="e131d-132">En outre, le retour au contexte d’origine n’est pas toujours souhaitable et ce comportement peut être modifié. Cette opération est décrite plus en détail dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="e131d-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="e131d-133">Configuration de la suspension et de la reprise avec Yield et ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="e131d-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>  
 <span data-ttu-id="e131d-134">Plusieurs méthodes fournissent davantage de contrôle sur l’exécution d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="e131d-135">Par exemple, vous pouvez utiliser la <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> méthode introduire un point dans la méthode asynchrone :</span><span class="sxs-lookup"><span data-stu-id="e131d-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 <span data-ttu-id="e131d-136">Cela équivaut à la publication asynchrone ou à la replanification vers le contexte actuel.</span><span class="sxs-lookup"><span data-stu-id="e131d-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>  
  
```csharp  
Task.Run(async delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
```  
  
 <span data-ttu-id="e131d-137">Vous pouvez également utiliser le <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> méthode pour mieux contrôler la suspension et reprise dans une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="e131d-138">Comme mentionné précédemment, par défaut, le contexte actuel est capturé au moment où une méthode asynchrone est interrompue, et ce contexte capturé est utilisé pour appeler la continuation de la méthode asynchrone lors de la reprise.</span><span class="sxs-lookup"><span data-stu-id="e131d-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="e131d-139">Dans de nombreux cas, il s’agit du comportement exact que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="e131d-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="e131d-140">Dans d’autres cas, vous pouvez ne pas vous soucier du contexte de continuation, et vous pouvez obtenir de meilleures performances en évitant d’effectuer ces publications vers le contexte d’origine.</span><span class="sxs-lookup"><span data-stu-id="e131d-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="e131d-141">Pour ce faire, utilisez le <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pour informer l’opération await pas à capturer et à reprendre sur le contexte, mais pour poursuivre l’exécution chaque fois que l’opération asynchrone qui a été attendue terminée :</span><span class="sxs-lookup"><span data-stu-id="e131d-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="e131d-142">Annulation d'une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="e131d-142">Canceling an Asynchronous Operation</span></span>  
 <span data-ttu-id="e131d-143">En commençant par le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], appuyez sur les méthodes qui prennent en charge l’annulation fournissent au moins une surcharge qui accepte un jeton d’annulation (<xref:System.Threading.CancellationToken> objet).</span><span class="sxs-lookup"><span data-stu-id="e131d-143">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>  
  
 <span data-ttu-id="e131d-144">Un jeton d’annulation est créé via une source de jeton d’annulation (<xref:System.Threading.CancellationTokenSource> objet).</span><span class="sxs-lookup"><span data-stu-id="e131d-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="e131d-145">La source de <xref:System.Threading.CancellationTokenSource.Token%2A> propriété retourne le jeton d’annulation qui sera signalé lors de la source <xref:System.Threading.CancellationTokenSource.Cancel%2A> méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="e131d-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="e131d-146">Par exemple, si vous souhaitez télécharger une page Web unique et que vous voulez être en mesure d’annuler l’opération, vous créez un <xref:System.Threading.CancellationTokenSource> de l’objet, la passer son jeton pour la méthode TAP et l’appel de la source <xref:System.Threading.CancellationTokenSource.Cancel%2A> méthode lorsque vous êtes prêt à annuler l’opération :</span><span class="sxs-lookup"><span data-stu-id="e131d-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 <span data-ttu-id="e131d-147">Pour annuler plusieurs appels asynchrones, vous pouvez passer le même jeton pour tous les appels :</span><span class="sxs-lookup"><span data-stu-id="e131d-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 <span data-ttu-id="e131d-148">Ou bien, vous pouvez passer le même jeton à un sous-ensemble sélectif d’opérations :</span><span class="sxs-lookup"><span data-stu-id="e131d-148">Or, you can pass the same token to a selective subset of operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 <span data-ttu-id="e131d-149">Les demandes d’annulation peuvent être lancées à partir de n’importe quel thread.</span><span class="sxs-lookup"><span data-stu-id="e131d-149">Cancellation requests may be initiated from any thread.</span></span>  
  
 <span data-ttu-id="e131d-150">Vous pouvez passer le <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> valeur à une méthode qui accepte un jeton d’annulation pour indiquer que l’annulation ne sera jamais demandée.</span><span class="sxs-lookup"><span data-stu-id="e131d-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="e131d-151">Cela entraîne le <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> propriété à retourner `false`, et la méthode appelée peut optimiser en conséquence.</span><span class="sxs-lookup"><span data-stu-id="e131d-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="e131d-152">À des fins de test, vous pouvez également transmettre un jeton pré-annulation instancié à l’aide du constructeur qui accepte une valeur booléenne pour indiquer si le jeton doit démarrer dans un état non annulable ou déjà annulé.</span><span class="sxs-lookup"><span data-stu-id="e131d-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>  
  
 <span data-ttu-id="e131d-153">Cette approche de l’annulation présente plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="e131d-153">This approach to cancellation has several advantages:</span></span>  
  
-   <span data-ttu-id="e131d-154">Vous pouvez passer le même jeton d’annulation à n’importe quel nombre d’opérations asynchrones ou synchrones.</span><span class="sxs-lookup"><span data-stu-id="e131d-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>  
  
-   <span data-ttu-id="e131d-155">La même demande d’annulation peut être déployée vers n’importe quel nombre d’écouteurs.</span><span class="sxs-lookup"><span data-stu-id="e131d-155">The same cancellation request may be proliferated to any number of listeners.</span></span>  
  
-   <span data-ttu-id="e131d-156">Le développeur de l’API asynchrone a le contrôle complet de la possibilité de demander l’annulation et du timing de la prise d’effet.</span><span class="sxs-lookup"><span data-stu-id="e131d-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>  
  
-   <span data-ttu-id="e131d-157">Le code qui utilise l’API peut déterminer de manière sélective les appels asynchrones qui seront transmis aux demandes d’annulation.</span><span class="sxs-lookup"><span data-stu-id="e131d-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>  
  
## <a name="monitoring-progress"></a><span data-ttu-id="e131d-158">Contrôle de la progression</span><span class="sxs-lookup"><span data-stu-id="e131d-158">Monitoring Progress</span></span>  
 <span data-ttu-id="e131d-159">Certaines méthodes asynchrones exposent la progression via une interface de progression transmise à la méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="e131d-160">Par exemple, considérez une fonction qui télécharge une chaîne de texte de façon asynchrone et qui, tout au long du processus, déclenche des mises à jour de progression qui incluent le pourcentage de téléchargement terminé jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="e131d-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="e131d-161">Cette méthode peut être utilisée dans une application Windows Presentation Foundation (WPF), comme suit :</span><span class="sxs-lookup"><span data-stu-id="e131d-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)    
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,   
            new Progress<int>(p => pbDownloadProgress.Value = p));  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
<a name="combinators"></a>   
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="e131d-162">Utilisation des combinateurs intégrés sur les tâches</span><span class="sxs-lookup"><span data-stu-id="e131d-162">Using the Built-in Task-based Combinators</span></span>  
 <span data-ttu-id="e131d-163">Le <xref:System.Threading.Tasks> espace de noms inclut plusieurs méthodes de composition et utilisation des tâches.</span><span class="sxs-lookup"><span data-stu-id="e131d-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>  
  
### <a name="taskrun"></a><span data-ttu-id="e131d-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="e131d-164">Task.Run</span></span>  
 <span data-ttu-id="e131d-165">Le <xref:System.Threading.Tasks.Task> classe comprend plusieurs <xref:System.Threading.Tasks.Task.Run%2A> les méthodes qui vous permettent de facilement déchargement du travail en tant qu’un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> au pool de threads, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
```  
  
 <span data-ttu-id="e131d-166">Certaines de ces <xref:System.Threading.Tasks.Task.Run%2A> méthodes, telles que la <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> de surcharge, exister en tant que raccourci permettant du <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e131d-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="e131d-167">Autres surcharges, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable vous permet d’utiliser await dans le travail déchargé, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 <span data-ttu-id="e131d-168">Ces surcharges sont logiquement équivalentes à l’aide du <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> méthode conjointement avec la <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> méthode d’extension dans la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="e131d-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>  
  
### <a name="taskfromresult"></a><span data-ttu-id="e131d-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="e131d-169">Task.FromResult</span></span>  
 <span data-ttu-id="e131d-170">Utilisez le <xref:System.Threading.Tasks.Task.FromResult%2A> méthode dans les scénarios où les données peuvent être déjà disponibles et uniquement doit être retourné à partir d’une méthode retournant des tâches dans un <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="e131d-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
```  
  
### <a name="taskwhenall"></a><span data-ttu-id="e131d-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="e131d-171">Task.WhenAll</span></span>  
 <span data-ttu-id="e131d-172">Utilisez la <xref:System.Threading.Tasks.Task.WhenAll%2A> méthode doit attendre de façon asynchrone sur plusieurs opérations asynchrones sont représentées en tant que tâches.</span><span class="sxs-lookup"><span data-stu-id="e131d-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="e131d-173">La méthode a plusieurs surcharges qui prennent en charge un ensemble de tâches non génériques ou un ensemble non uniforme de tâches génériques (par exemple, l’attente asynchrone de plusieurs opérations qui retournent void, ou l’attente asynchrone de plusieurs méthodes retournant des valeurs où chaque valeur peut avoir un type différent) ou prennent en charge un ensemble uniforme de tâches génériques (comme l’attente asynchrone de plusieurs méthodes retournant `TResult`).</span><span class="sxs-lookup"><span data-stu-id="e131d-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>  
  
 <span data-ttu-id="e131d-174">Supposons que vous souhaitez envoyer des messages électroniques à plusieurs clients.</span><span class="sxs-lookup"><span data-stu-id="e131d-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="e131d-175">Vous pouvez superposer l’envoi des messages afin de ne pas attendre la fin de l’envoi d’un message avant d’envoyer le suivant.</span><span class="sxs-lookup"><span data-stu-id="e131d-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="e131d-176">Vous saurez également quand les opérations d’envoi se sont terminées et si des erreurs se sont produites :</span><span class="sxs-lookup"><span data-stu-id="e131d-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 <span data-ttu-id="e131d-177">Ce code ne gère pas les exceptions qui peuvent se produire, mais permet de propager des exceptions explicitement le `await` sur la tâche obtenue à partir de <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="e131d-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="e131d-178">Pour gérer les exceptions, vous pouvez utiliser le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e131d-178">To handle the exceptions, you can use code such as the following:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    ...  
}  
```  
  
 <span data-ttu-id="e131d-179">Dans ce cas, si une opération asynchrone échoue, toutes les exceptions seront consolidées dans une <xref:System.AggregateException> exception, qui est stockée dans le <xref:System.Threading.Tasks.Task> qui est retourné à partir de la <xref:System.Threading.Tasks.Task.WhenAll%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e131d-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="e131d-180">Toutefois, une seul de ces exceptions est propagée par le mot-clé `await`.</span><span class="sxs-lookup"><span data-stu-id="e131d-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="e131d-181">Si vous souhaitez examiner toutes les exceptions, vous pouvez réécrire le code précédent comme suit :</span><span class="sxs-lookup"><span data-stu-id="e131d-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>  
  
```csharp  
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
 <span data-ttu-id="e131d-182">Prenons un exemple de téléchargement de plusieurs fichiers à partir du web de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="e131d-183">Dans ce cas, toutes les opérations asynchrones ont des types de résultats homogènes, et il est facile d’accéder aux résultats :</span><span class="sxs-lookup"><span data-stu-id="e131d-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 <span data-ttu-id="e131d-184">Vous pouvez utiliser les mêmes techniques de gestion des exceptions que celles évoquées dans le scénario précédent qui retournait void :</span><span class="sxs-lookup"><span data-stu-id="e131d-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>  
  
```csharp  
Task [] asyncOps =   
    (from url in urls select DownloadStringAsync(url)).ToArray();  
try  
{  
    string [] pages = await Task.WhenAll(asyncOps);  
    ...  
}  
catch(Exception exc)  
{  
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
### <a name="taskwhenany"></a><span data-ttu-id="e131d-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="e131d-185">Task.WhenAny</span></span>  
 <span data-ttu-id="e131d-186">Vous pouvez utiliser la <xref:System.Threading.Tasks.Task.WhenAny%2A> méthode asynchrone en attente pour l’une des multiples opérations asynchrones représentée en tant que tâches à effectuer.</span><span class="sxs-lookup"><span data-stu-id="e131d-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="e131d-187">Cette méthode couvre quatre principaux cas d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="e131d-187">This method serves four primary use cases:</span></span>  
  
-   <span data-ttu-id="e131d-188">Redondance : Exécution d’une opération plusieurs fois et sélection de celle qui se termine en premier (par exemple, en contactant plusieurs services web de cotation boursière qui produiront un résultat unique et en sélectionnant celui qui se terminera le plus rapidement).</span><span class="sxs-lookup"><span data-stu-id="e131d-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>  
  
-   <span data-ttu-id="e131d-189">Entrelacement : Lancement de plusieurs opérations, en attendant que toutes se terminent, mais en traitant chacune lors de leur achèvement.</span><span class="sxs-lookup"><span data-stu-id="e131d-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>  
  
-   <span data-ttu-id="e131d-190">Limitation : Autorisation du lancement de nouvelles opérations lorsque d’autres se terminent.</span><span class="sxs-lookup"><span data-stu-id="e131d-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="e131d-191">Il s’agit d’une extension de l’entrelacement.</span><span class="sxs-lookup"><span data-stu-id="e131d-191">This is an extension of the interleaving scenario.</span></span>  
  
-   <span data-ttu-id="e131d-192">Interruption anticipée : par exemple, une opération représentée par la tâche t1 peut être regroupée dans un <xref:System.Threading.Tasks.Task.WhenAny%2A> tâche avec une autre tâche t2 et que vous pouvez attendre la <xref:System.Threading.Tasks.Task.WhenAny%2A> tâche.</span><span class="sxs-lookup"><span data-stu-id="e131d-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="e131d-193">La tâche t2 peut représenter un délai d’attente, ou l’annulation ou certaines autres signal qui provoque le <xref:System.Threading.Tasks.Task.WhenAny%2A> tâche se termine avant la fin de t1.</span><span class="sxs-lookup"><span data-stu-id="e131d-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>  
  
#### <a name="redundancy"></a><span data-ttu-id="e131d-194">Redondance</span><span class="sxs-lookup"><span data-stu-id="e131d-194">Redundancy</span></span>  
 <span data-ttu-id="e131d-195">Prenons un cas où vous souhaitez prendre une décision sur la nécessité d’acheter une action.</span><span class="sxs-lookup"><span data-stu-id="e131d-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="e131d-196">Il existe plusieurs services de recommandation de cotation boursière auxquels vous faites confiance, mais selon la charge quotidienne, chaque service peut avoir des lenteurs à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="e131d-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="e131d-197">Vous pouvez utiliser la <xref:System.Threading.Tasks.Task.WhenAny%2A> méthode pour recevoir une notification lorsque n’importe quelle opération est terminée :</span><span class="sxs-lookup"><span data-stu-id="e131d-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>  
  
```csharp  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol),   
    GetBuyRecommendation2Async(symbol),  
    GetBuyRecommendation3Async(symbol)  
};  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
if (await recommendation) BuyStock(symbol);  
```  
  
 <span data-ttu-id="e131d-198">Contrairement aux <xref:System.Threading.Tasks.Task.WhenAll%2A>, qui retourne les résultats non encapsulés de toutes les tâches qui s’est terminée avec succès, <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="e131d-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="e131d-199">Si une tâche échoue, il est important de savoir qu’elle a échoué, et si une tâche réussit, il est important de savoir la tâche à laquelle la valeur de retour est associée.</span><span class="sxs-lookup"><span data-stu-id="e131d-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="e131d-200">Par conséquent, vous devez accéder au résultat de la tâche retournée ou l’attendre davantage, comme le montre cet exemple.</span><span class="sxs-lookup"><span data-stu-id="e131d-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>  
  
 <span data-ttu-id="e131d-201">Comme avec <xref:System.Threading.Tasks.Task.WhenAll%2A>, vous devez être en mesure de prendre en compte les exceptions.</span><span class="sxs-lookup"><span data-stu-id="e131d-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="e131d-202">Étant donné que vous recevez la tâche terminée, vous pouvez attendre la tâche retournée pour propager les erreurs, et utiliser `try/catch` dessus comme nécessaire, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>  
  
```csharp  
Task<bool> [] recommendations = …;  
while(recommendations.Count > 0)  
{   
    Task<bool> recommendation = await Task.WhenAny(recommendations);      
    try  
    {  
        if (await recommendation) BuyStock(symbol);  
        break;  
    }  
    catch(WebException exc)  
    {  
        recommendations.Remove(recommendation);  
    }  
}  
```  
  
 <span data-ttu-id="e131d-203">En outre, même si une première tâche se termine avec succès, les tâches suivantes peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="e131d-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="e131d-204">À ce stade, vous avez plusieurs options pour traiter les exceptions : vous pouvez attendre que toutes les tâches lancées terminées, auquel cas vous pouvez utiliser la <xref:System.Threading.Tasks.Task.WhenAll%2A> (méthode), ou vous pouvez décider que toutes les exceptions sont importantes et doivent être journalisées.</span><span class="sxs-lookup"><span data-stu-id="e131d-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="e131d-205">Dans ce cas, vous pouvez utiliser les continuations de recevoir une notification lorsque des tâches se sont terminées de manière asynchrone :</span><span class="sxs-lookup"><span data-stu-id="e131d-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 <span data-ttu-id="e131d-206">ou :</span><span class="sxs-lookup"><span data-stu-id="e131d-206">or:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 <span data-ttu-id="e131d-207">ou même :</span><span class="sxs-lookup"><span data-stu-id="e131d-207">or even:</span></span>  
  
```  
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)  
{  
    foreach(var task in tasks)  
    {  
        try { await task; }  
        catch(Exception exc) { Log(exc); }  
    }  
}  
…  
LogCompletionIfFailed(recommendations);  
```  
  
 <span data-ttu-id="e131d-208">Enfin, vous souhaiterez peut-être annuler toutes les opérations restantes :</span><span class="sxs-lookup"><span data-stu-id="e131d-208">Finally, you may want to cancel all the remaining operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol, cts.Token),   
    GetBuyRecommendation2Async(symbol, cts.Token),  
    GetBuyRecommendation3Async(symbol, cts.Token)  
};  
  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
cts.Cancel();  
if (await recommendation) BuyStock(symbol);  
```  
  
#### <a name="interleaving"></a><span data-ttu-id="e131d-209">Entrelacement</span><span class="sxs-lookup"><span data-stu-id="e131d-209">Interleaving</span></span>  
 <span data-ttu-id="e131d-210">Prenons un cas où vous téléchargez des images à partir du web et traitez chaque image (par exemple, en ajoutant l’image à un contrôle d’interface utilisateur).</span><span class="sxs-lookup"><span data-stu-id="e131d-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="e131d-211">Vous devez effectuer le traitement de manière séquentielle sur le thread d’interface utilisateur, mais vous souhaitez télécharger autant d’images en même temps que possible.</span><span class="sxs-lookup"><span data-stu-id="e131d-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="e131d-212">En outre, vous ne voulez pas retarder l’ajout d’images à l’interface utilisateur jusqu'à ce qu’elles soient toutes téléchargées : vous souhaitez les ajouter quand elles sont prêtes :</span><span class="sxs-lookup"><span data-stu-id="e131d-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
 <span data-ttu-id="e131d-213">Vous pouvez également appliquer d’entrelacement à un scénario qui implique un traitement de nombreuses ressources de calcul intensif sur le <xref:System.Threading.ThreadPool> des images téléchargées, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)  
         .ContinueWith(t => ConvertImage(t.Result)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
#### <a name="throttling"></a><span data-ttu-id="e131d-214">Throttling</span><span class="sxs-lookup"><span data-stu-id="e131d-214">Throttling</span></span>  
 <span data-ttu-id="e131d-215">Prenons l’exemple de l’entrelacement, sauf qu’ici l’utilisateur télécharge tant d’images que les téléchargements doivent être limités. Par exemple, vous ne souhaitez qu’un certain nombre de téléchargements simultanés.</span><span class="sxs-lookup"><span data-stu-id="e131d-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="e131d-216">Pour ce faire, vous pouvez démarrer un sous-ensemble d’opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e131d-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="e131d-217">Lorsque les opérations sont terminées, vous pouvez démarrer des opérations supplémentaires pour prendre leur place :</span><span class="sxs-lookup"><span data-stu-id="e131d-217">As operations complete, you can start additional operations to take their place:</span></span>  
  
```csharp  
const int CONCURRENCY_LEVEL = 15;  
Uri [] urls = …;  
int nextIndex = 0;  
var imageTasks = new List<Task<Bitmap>>();  
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)  
{  
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
    nextIndex++;  
}  
  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch(Exception exc) { Log(exc); }  
  
    if (nextIndex < urls.Length)  
    {  
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
        nextIndex++;  
    }  
}  
```  
  
#### <a name="early-bailout"></a><span data-ttu-id="e131d-218">Interruption anticipée</span><span class="sxs-lookup"><span data-stu-id="e131d-218">Early Bailout</span></span>  
 <span data-ttu-id="e131d-219">Considérez que vous attendez de façon asynchrone qu’une opération se termine tout en répondant simultanément à la demande d’annulation d’un utilisateur (par exemple, lorsque l’utilisateur clique sur un bouton Annuler).</span><span class="sxs-lookup"><span data-stu-id="e131d-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="e131d-220">Le code suivant illustre ce scénario :</span><span class="sxs-lookup"><span data-stu-id="e131d-220">The following code illustrates this scenario:</span></span>  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        if (imageDownload.IsCompleted)  
        {  
            Bitmap image = await imageDownload;  
            panel.AddImage(image);  
        }  
        else imageDownload.ContinueWith(t => Log(t));  
    }  
    finally { btnRun.Enabled = true; }  
}  
  
private static async Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
```  
  
 <span data-ttu-id="e131d-221">Cette implémentation réactive l’interface utilisateur dès que vous décidez de quitter la procédure, mais n’annule pas les opérations asynchrones sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="e131d-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="e131d-222">Une autre solution serait d’annuler les opérations en attente lorsque vous décidez de quitter la procédure, mais de ne pas rétablir l’interface utilisateur avant que les opérations soient réellement terminées, éventuellement en raison d’une fin anticipée suite à une demande d’annulation :</span><span class="sxs-lookup"><span data-stu-id="e131d-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        Bitmap image = await imageDownload;  
        panel.AddImage(image);  
    }  
    catch(OperationCanceledException) {}  
    finally { btnRun.Enabled = true; }  
}  
```  
  
 <span data-ttu-id="e131d-223">Un autre exemple d’une interruption anticipée implique l’utilisation de la <xref:System.Threading.Tasks.Task.WhenAny%2A> méthode conjointement avec la <xref:System.Threading.Tasks.Task.Delay%2A> méthode, comme indiqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="e131d-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>  
  
### <a name="taskdelay"></a><span data-ttu-id="e131d-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="e131d-224">Task.Delay</span></span>  
 <span data-ttu-id="e131d-225">Vous pouvez utiliser la <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> méthode introduire une pause dans l’exécution d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="e131d-226">Cela est utile pour de nombreux types de fonctionnalités, notamment la création de boucles d’interrogation et le retardement du traitement des entrées d’utilisateur pour une période prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="e131d-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="e131d-227">Le <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> méthode peut également être utile en combinaison avec <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pour la mise en œuvre de délais d’expiration sur attend.</span><span class="sxs-lookup"><span data-stu-id="e131d-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>  
  
 <span data-ttu-id="e131d-228">Si une tâche qui fait partie d’une opération asynchrone plus vaste (par exemple, un service web ASP.NET) prend trop de temps, l’opération globale peut en pâtir, en particulier si elle ne se termine jamais.</span><span class="sxs-lookup"><span data-stu-id="e131d-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="e131d-229">Pour cette raison, il est important d’être en mesure de quitter la procédure lors de l’attente sur une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="e131d-230">Synchrones <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, et <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> méthodes acceptent des valeurs de délai d’attente, mais correspondant <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> et mentionnées précédemment <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>méthodes ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="e131d-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="e131d-231">Au lieu de cela, vous pouvez utiliser <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> conjointement pour implémenter un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="e131d-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>  
  
 <span data-ttu-id="e131d-232">Par exemple, dans votre application d’interface utilisateur, supposons que vous souhaitez télécharger une image et désactivez l’interface utilisateur pendant le téléchargement de l’image.</span><span class="sxs-lookup"><span data-stu-id="e131d-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="e131d-233">Toutefois, si le téléchargement est trop long, vous souhaitez réactiver l’interface utilisateur et ignorer le téléchargement :</span><span class="sxs-lookup"><span data-stu-id="e131d-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>  
  
```csharp  
public async void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = "Timed out";  
            var ignored = download.ContinueWith(  
                t => Trace("Task finally completed"));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
 <span data-ttu-id="e131d-234">La même règle s’applique à plusieurs téléchargements, car <xref:System.Threading.Tasks.Task.WhenAll%2A> retourne une tâche :</span><span class="sxs-lookup"><span data-stu-id="e131d-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>  
  
```csharp  
public async void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            status.Text = "Timed out";  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
## <a name="building-task-based-combinators"></a><span data-ttu-id="e131d-235">Création de combinateurs basés sur les tâches</span><span class="sxs-lookup"><span data-stu-id="e131d-235">Building Task-based Combinators</span></span>  
 <span data-ttu-id="e131d-236">Une tâche étant en mesure de représenter une opération asynchrone et de fournir des fonctions synchrones et asynchrones pour effectuer la liaison avec l’opération, récupérer ses résultats et ainsi de suite, vous pouvez créer des bibliothèques utiles de combinateurs qui composent les tâches pour créer des modèles plus grands.</span><span class="sxs-lookup"><span data-stu-id="e131d-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="e131d-237">Comme expliqué dans la section précédente, .NET Framework inclut plusieurs combinateurs intégrés, mais vous pouvez également créer les vôtres.</span><span class="sxs-lookup"><span data-stu-id="e131d-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="e131d-238">Les sections suivantes fournissent plusieurs exemples de types et méthodes de combinateurs potentiels.</span><span class="sxs-lookup"><span data-stu-id="e131d-238">The following sections provide several examples of potential combinator methods and types.</span></span>  
  
### <a name="retryonfault"></a><span data-ttu-id="e131d-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="e131d-239">RetryOnFault</span></span>  
 <span data-ttu-id="e131d-240">Dans de nombreuses situations, vous souhaiterez peut-être retenter une opération si une tentative précédente échoue.</span><span class="sxs-lookup"><span data-stu-id="e131d-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="e131d-241">Pour le code synchrone, vous pouvez créer une méthode d’assistance telle que `RetryOnFault` dans l’exemple suivant pour y parvenir :</span><span class="sxs-lookup"><span data-stu-id="e131d-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>  
  
```csharp  
public static T RetryOnFault<T>(  
    Func<T> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return function(); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="e131d-242">Vous pouvez créer une méthode d’assistance presque identique pour les opérations asynchrones qui sont implémentées avec TAP et donc renvoyer des tâches :</span><span class="sxs-lookup"><span data-stu-id="e131d-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="e131d-243">Vous pouvez ensuite utiliser ce combinateur pour encoder les nouvelles tentatives dans la logique de l’application ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 <span data-ttu-id="e131d-244">Vous pouvez étendre la fonction `RetryOnFault`.</span><span class="sxs-lookup"><span data-stu-id="e131d-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="e131d-245">Par exemple, la fonction peut accepter une autre `Func<Task>` qui sera appelée entre chaque tentative pour déterminer quand recommencer l’opération, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
        await retryWhen().ConfigureAwait(false);  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="e131d-246">Vous pouvez ensuite utiliser la fonction comme suit pour attendre une seconde avant de recommencer l’opération :</span><span class="sxs-lookup"><span data-stu-id="e131d-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a><span data-ttu-id="e131d-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="e131d-247">NeedOnlyOne</span></span>  
 <span data-ttu-id="e131d-248">Parfois, vous pouvez tirer parti de la redondance pour améliorer la latence et les chances de réussite d’une opération.</span><span class="sxs-lookup"><span data-stu-id="e131d-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="e131d-249">Supposons que nous avons plusieurs services web qui fournissent des cotations boursières, mais qu’à différents moments de la journée, chaque service peut fournir différents niveaux de qualité et de réactivité.</span><span class="sxs-lookup"><span data-stu-id="e131d-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="e131d-250">Pour faire face à ces variations, vous pouvez émettre des demandes pour tous les services web et, dès que vous obtenez une réponse à partir d’un d’entre eux, annuler les demandes restantes.</span><span class="sxs-lookup"><span data-stu-id="e131d-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="e131d-251">Vous pouvez implémenter une fonction d’assistance pour faciliter l’implémentation de ce modèle commun de lancement de plusieurs opérations, d’attente qu’une d’entre elles se termine et d’annulation du reste.</span><span class="sxs-lookup"><span data-stu-id="e131d-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="e131d-252">La fonction `NeedOnlyOne` dans l’exemple suivant illustre ce scénario :</span><span class="sxs-lookup"><span data-stu-id="e131d-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>  
  
```csharp  
public static async Task<T> NeedOnlyOne(  
    params Func<CancellationToken,Task<T>> [] functions)  
{  
    var cts = new CancellationTokenSource();  
    var tasks = (from function in functions  
                 select function(cts.Token)).ToArray();  
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);  
    cts.Cancel();  
    foreach(var task in tasks)   
    {  
        var ignored = task.ContinueWith(  
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);  
    }  
    return completed;  
}  
```  
  
 <span data-ttu-id="e131d-253">Vous pouvez ensuite utiliser cette fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="e131d-253">You can then use this function as follows:</span></span>  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a><span data-ttu-id="e131d-254">Opérations entrelacées</span><span class="sxs-lookup"><span data-stu-id="e131d-254">Interleaved Operations</span></span>  
 <span data-ttu-id="e131d-255">Il existe un problème potentiel de performances à l’utilisation de la <xref:System.Threading.Tasks.Task.WhenAny%2A> méthode pour prendre en charge un entrelacement de scénario lorsque vous travaillez avec très grands ensembles de tâches.</span><span class="sxs-lookup"><span data-stu-id="e131d-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="e131d-256">Chaque appel à <xref:System.Threading.Tasks.Task.WhenAny%2A> entraîne une continuation avec chaque tâche en cours d’inscription.</span><span class="sxs-lookup"><span data-stu-id="e131d-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="e131d-257">Pour un nombre N de tâches, cela entraîne des continuations O(N2) créées sur la durée de vie de l’opération d’entrelacement.</span><span class="sxs-lookup"><span data-stu-id="e131d-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="e131d-258">Si vous travaillez avec un large éventail de tâches, vous pouvez utiliser un combinateur (`Interleaved` dans l’exemple suivant) pour résoudre le problème de performances :</span><span class="sxs-lookup"><span data-stu-id="e131d-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>  
  
```csharp  
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputTasks = tasks.ToList();  
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)   
                   select new TaskCompletionSource<T>()).ToList();  
    int nextTaskIndex = -1;  
    foreach (var inputTask in inputTasks)  
    {  
        inputTask.ContinueWith(completed =>  
        {  
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];  
            if (completed.IsFaulted)   
                source.TrySetException(completed.Exception.InnerExceptions);  
            else if (completed.IsCanceled)   
                source.TrySetCanceled();  
            else   
                source.TrySetResult(completed.Result);  
        }, CancellationToken.None,   
           TaskContinuationOptions.ExecuteSynchronously,   
           TaskScheduler.Default);  
    }  
    return from source in sources   
           select source.Task;  
}  
```  
  
 <span data-ttu-id="e131d-259">Vous pouvez ensuite utiliser le combinateur pour traiter les résultats des tâches terminées ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="e131d-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a><span data-ttu-id="e131d-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="e131d-260">WhenAllOrFirstException</span></span>  
 <span data-ttu-id="e131d-261">Dans certains scénarios de dispersion/regroupement, vous souhaiterez attendre toutes les tâches dans un jeu, à moins qu’une d’elles rencontre une erreur, auquel cas vous souhaiterez cesser d’attendre dès que l’exception se produit.</span><span class="sxs-lookup"><span data-stu-id="e131d-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="e131d-262">Vous pouvez accomplir cela avec une méthode de combinateur comme `WhenAllOrFirstException` dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e131d-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
```  
  
## <a name="building-task-based-data-structures"></a><span data-ttu-id="e131d-263">Création de structures de données basées sur les tâches</span><span class="sxs-lookup"><span data-stu-id="e131d-263">Building Task-based Data Structures</span></span>  
 <span data-ttu-id="e131d-264">Outre la possibilité de build personnalisées combinateurs basé sur des tâches, ayant une structure de données dans <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui représente les résultats d’une opération asynchrone et la synchronisation nécessaire pour joindre avec elle rend très puissants type sur lequel vous créez des structures de données personnalisées à utiliser dans les scénarios asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e131d-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>  
  
### <a name="asynccache"></a><span data-ttu-id="e131d-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="e131d-265">AsyncCache</span></span>  
 <span data-ttu-id="e131d-266">Un aspect important d’une tâche est qu’il peut être remis à plusieurs consommateurs, qui peut l’attendre, les continuations de Registre, obtenir des résultats ou des exceptions (dans le cas de <xref:System.Threading.Tasks.Task%601>), et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e131d-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="e131d-267">Cela rend <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> parfaitement adaptés pour être utilisés dans une infrastructure de mise en cache asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e131d-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="e131d-268">Voici un exemple d’un petit mais puissant cache asynchrone construit sur <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="e131d-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
```csharp  
public class AsyncCache<TKey, TValue>  
{  
    private readonly Func<TKey, Task<TValue>> _valueFactory;  
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;  
  
    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)  
    {  
        if (valueFactory == null) throw new ArgumentNullException("loader");  
        _valueFactory = valueFactory;  
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();  
    }  
  
    public Task<TValue> this[TKey key]  
    {  
        get  
        {  
            if (key == null) throw new ArgumentNullException("key");  
            return _map.GetOrAdd(key, toAdd =>   
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e131d-269">Le [AsyncCache\<TKey, TValue >](http://go.microsoft.com/fwlink/p/?LinkId=251941) classe accepte en tant que délégué pour son constructeur, une fonction qui accepte un `TKey` et retourne un <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e131d-269">The [AsyncCache\<TKey,TValue>](http://go.microsoft.com/fwlink/p/?LinkId=251941) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="e131d-270">Toutes les valeurs précédemment accessibles à partir du cache sont stockées dans le dictionnaire interne, et `AsyncCache` garantit qu’une seule tâche est générée par clé, même en cas d’accès simultané au cache.</span><span class="sxs-lookup"><span data-stu-id="e131d-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>  
  
 <span data-ttu-id="e131d-271">Par exemple, vous pouvez créer un cache de pages web téléchargées :</span><span class="sxs-lookup"><span data-stu-id="e131d-271">For example, you can build a cache for downloaded web pages:</span></span>  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 <span data-ttu-id="e131d-272">Vous pouvez ensuite utiliser ce cache dans les méthodes asynchrones chaque fois que vous avez besoin du contenu d’une page web.</span><span class="sxs-lookup"><span data-stu-id="e131d-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="e131d-273">La classe `AsyncCache` garantit que vous téléchargez aussi peu de pages que possible, et met les résultats en cache.</span><span class="sxs-lookup"><span data-stu-id="e131d-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="e131d-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="e131d-274">AsyncProducerConsumerCollection</span></span>  
 <span data-ttu-id="e131d-275">Vous pouvez également utiliser des tâches pour créer des structures de données pour la coordination des activités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e131d-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="e131d-276">Considérez un des modèles de conception parallèle classiques : le modèle producteur/consommateur.</span><span class="sxs-lookup"><span data-stu-id="e131d-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="e131d-277">Dans ce modèle, les producteurs génèrent des données qui sont utilisées par les consommateurs, et les producteurs et les consommateurs peuvent s’exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="e131d-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="e131d-278">Par exemple, le consommateur traite l’élément 1, qui a été généré précédemment par un producteur qui produit maintenant l’élément 2.</span><span class="sxs-lookup"><span data-stu-id="e131d-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="e131d-279">Dans le modèle producteur/consommateur, vous avez toujours besoin d’une structure de données pour stocker les données créées par les producteurs afin que les consommateurs puissent être informés des nouvelles données et le trouver lorsqu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="e131d-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>  
  
 <span data-ttu-id="e131d-280">Voici une structure de données simple basée sur les tâches qui permet d’utiliser des méthodes asynchrones en tant que producteurs et consommateurs :</span><span class="sxs-lookup"><span data-stu-id="e131d-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>  
  
```csharp  
public class AsyncProducerConsumerCollection<T>  
{  
    private readonly Queue<T> m_collection = new Queue<T>();  
    private readonly Queue<TaskCompletionSource<T>> m_waiting =   
        new Queue<TaskCompletionSource<T>>();  
  
    public void Add(T item)  
    {  
        TaskCompletionSource<T> tcs = null;  
        lock (m_collection)  
        {  
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();  
            else m_collection.Enqueue(item);  
        }  
        if (tcs != null) tcs.TrySetResult(item);  
    }  
  
    public Task<T> Take()  
    {  
        lock (m_collection)  
        {  
            if (m_collection.Count > 0)   
            {  
                return Task.FromResult(m_collection.Dequeue());   
            }  
            else   
            {  
                var tcs = new TaskCompletionSource<T>();  
                m_waiting.Enqueue(tcs);  
                return tcs.Task;  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e131d-281">Avec cette structure de données en place, vous pouvez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e131d-281">With that data structure in place, you can write code such as the following:</span></span>  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.Take();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Add(data);  
}  
```  
  
 <span data-ttu-id="e131d-282">Le <xref:System.Threading.Tasks.Dataflow> espace de noms inclut la <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, ce qui vous permet d’une manière similaire, mais sans avoir à créer un type de collection personnalisé :</span><span class="sxs-lookup"><span data-stu-id="e131d-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.ReceiveAsync();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Post(data);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="e131d-283">Le <xref:System.Threading.Tasks.Dataflow> espace de noms est disponible dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] via **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="e131d-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] through **NuGet**.</span></span> <span data-ttu-id="e131d-284">Pour installer l’assembly qui contient le <xref:System.Threading.Tasks.Dataflow> espace de noms, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **gérer les Packages NuGet** à partir du menu projet, puis recherchez en ligne le package Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="e131d-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e131d-285">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e131d-285">See Also</span></span>  
 [<span data-ttu-id="e131d-286">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="e131d-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="e131d-287">Implémentation du modèle asynchrone basé sur des tâches</span><span class="sxs-lookup"><span data-stu-id="e131d-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="e131d-288">Interopérabilité avec d’autres types et modèles asynchrones</span><span class="sxs-lookup"><span data-stu-id="e131d-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
