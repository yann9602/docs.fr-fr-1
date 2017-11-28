---
title: "async (référence C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4a89736822342a9d9a24db6d43435f9795b81b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="async-c-reference"></a><span data-ttu-id="720c2-102">async (référence C#)</span><span class="sxs-lookup"><span data-stu-id="720c2-102">async (C# Reference)</span></span>
<span data-ttu-id="720c2-103">Utilisez le modificateur `async` pour spécifier qu’une méthode, une [expression lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="720c2-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="720c2-104">Si vous utilisez ce modificateur sur une méthode ou une expression, il s’agit d’une *méthode async*.</span><span class="sxs-lookup"><span data-stu-id="720c2-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="720c2-105">L’exemple suivant définit une méthode async nommée `ExampleMethodAsync` :</span><span class="sxs-lookup"><span data-stu-id="720c2-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="720c2-106">Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode async utilise le mot clé `await` pour un travail potentiellement long sans bloquer le thread de l’appelant, lisez l’introduction dans [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="720c2-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="720c2-107">Le code suivant se trouve dans une méthode async et appelle la méthode <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="720c2-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="720c2-108">Une méthode async s’exécute de façon synchrone jusqu’à ce qu’elle atteigne sa première expression `await`, où elle est suspendue jusqu’à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="720c2-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="720c2-109">Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="720c2-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="720c2-110">Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="720c2-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="720c2-111">Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas d’instructions `await`, car cette situation peut indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="720c2-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="720c2-112">Consultez [Avertissement du compilateur (niveau 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="720c2-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="720c2-113">Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="720c2-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="720c2-114">Dans tous les autres contextes, il est interprété comme un identificateur.</span><span class="sxs-lookup"><span data-stu-id="720c2-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="720c2-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="720c2-115">Example</span></span>  
<span data-ttu-id="720c2-116">L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="720c2-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="720c2-117">Le résultat de la méthode async est le nombre de caractères d’une page web.</span><span class="sxs-lookup"><span data-stu-id="720c2-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="720c2-118">Le code convient pour une application WPF (Windows Presentation Foundation) ou une application du Windows Store que vous créez dans Visual Studio ; consultez les commentaires du code pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="720c2-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="720c2-119">Vous pouvez exécuter ce code dans Visual Studio en tant qu’application Windows Presentation Foundation (WPF) ou qu’application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="720c2-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="720c2-120">Vous avez besoin d’un contrôle Button nommé `StartButton` et d’un contrôle Textbox nommé `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="720c2-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="720c2-121">N’oubliez pas de définir les noms et le gestionnaire afin d’obtenir un résultat semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="720c2-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="720c2-122">Pour exécuter le code en tant qu’application WPF :</span><span class="sxs-lookup"><span data-stu-id="720c2-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="720c2-123">Collez ce code dans la classe `MainWindow` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="720c2-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="720c2-124">Ajoutez une référence à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="720c2-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="720c2-125">Ajoutez une directive `using` à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="720c2-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="720c2-126">Pour exécuter le code comme une application du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="720c2-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="720c2-127">Collez ce code dans la classe `MainPage` dans MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="720c2-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="720c2-128">Ajouter des directives using pour System.Net.Http et System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="720c2-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="720c2-129">Pour plus d’informations sur les tâches et sur le code qui s’exécute en attendant une tâche, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="720c2-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="720c2-130">Pour obtenir un exemple WPF complet qui utilise des éléments similaires, consultez [Procédure pas à pas : accès au web avec Async et Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="720c2-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="720c2-131">Types de retours</span><span class="sxs-lookup"><span data-stu-id="720c2-131">Return Types</span></span>  
<span data-ttu-id="720c2-132">Une méthode async peut avoir les types de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="720c2-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="720c2-133">[void](../../../csharp/language-reference/keywords/void.md), qui doit être utilisé uniquement pour les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="720c2-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="720c2-134">À compter de C# 7, tout type ayant une méthode `GetAwaiter` accessible.</span><span class="sxs-lookup"><span data-stu-id="720c2-134">Starting with C# 7, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="720c2-135">Le type `System.Threading.Tasks.ValueTask<TResult>` est une implémentation de ce genre.</span><span class="sxs-lookup"><span data-stu-id="720c2-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="720c2-136">Il est disponible en ajoutant le package NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="720c2-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="720c2-137">La méthode async ne peut déclarer aucun paramètre [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), ni avoir une <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->valeur de retour de référence, mais elle peut appeler des méthodes qui comportent de tels paramètres.</span><span class="sxs-lookup"><span data-stu-id="720c2-137">The async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, nor can it have a <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->reference return value, but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="720c2-138">Vous spécifiez `Task<TResult>` comme type de retour d’une méthode async si l’instruction [return](../../../csharp/language-reference/keywords/return.md) de la méthode spécifie un opérande de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="720c2-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="720c2-139">Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.</span><span class="sxs-lookup"><span data-stu-id="720c2-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="720c2-140">En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.</span><span class="sxs-lookup"><span data-stu-id="720c2-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="720c2-141">Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour.</span><span class="sxs-lookup"><span data-stu-id="720c2-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="720c2-142">L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="720c2-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="720c2-143">À compter de C# 7, vous retournez un autre type, en général un type valeur, qui a une méthode `GetAwaiter` pour limiter les allocations de mémoire dans les sections de code critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="720c2-143">Starting with C# 7, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="720c2-144">Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="720c2-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720c2-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="720c2-145">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="720c2-146">await</span><span class="sxs-lookup"><span data-stu-id="720c2-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="720c2-147">Procédure pas à pas : accès au web avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="720c2-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="720c2-148">Programmation asynchrone avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="720c2-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
