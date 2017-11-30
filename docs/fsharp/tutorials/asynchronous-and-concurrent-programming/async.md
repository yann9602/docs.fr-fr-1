---
title: 'Programmation asynchrone en F #'
description: "Découvrez comment F # de programmation asynchrone est effectuée via un modèle de programmation au niveau du langage qui est facile à utiliser et naturelle à la langue."
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: 23528d84d0f28283868a1ea316953543d0fd566a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="async-programming-in-f"></a><span data-ttu-id="8e290-104">Programmation asynchrone en F #</span><span class="sxs-lookup"><span data-stu-id="8e290-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="8e290-105">Certaines inexactitudes ont été détectés dans cet article.</span><span class="sxs-lookup"><span data-stu-id="8e290-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="8e290-106">Il est en cours de réécriture.</span><span class="sxs-lookup"><span data-stu-id="8e290-106">It is being rewritten.</span></span>  <span data-ttu-id="8e290-107">Consultez [problème #666](https://github.com/dotnet/docs/issues/666) pour en savoir plus sur les modifications.</span><span class="sxs-lookup"><span data-stu-id="8e290-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="8e290-108">Programmation F # asynchrone peut être obtenue via un modèle de programmation au niveau du langage conçu pour être facile à utiliser et naturelle à la langue.</span><span class="sxs-lookup"><span data-stu-id="8e290-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="8e290-109">Le cœur de la programmation asynchrone en F # est `Async<'T>`, une représentation sous forme de travail qui peut être déclenchée pour s’exécuter en arrière-plan, où `'T` est soit le type retourné via spéciale `return` mot clé ou `unit` si le flux de travail asynchrone n’a pas résultat à retourner.</span><span class="sxs-lookup"><span data-stu-id="8e290-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="8e290-110">Comprendre le concept essentiel est que le type d’une expression async est `Async<'T>`, qui est simplement un _spécification_ de travail à faire dans un contexte asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8e290-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="8e290-111">Il n’est pas exécuté jusqu'à ce que vous le démarrez explicitement avec une des fonctions de départ (tel que `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="8e290-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="8e290-112">Bien qu’il s’agit d’une autre façon de réfléchir à travailler, il finit par être très simple dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="8e290-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="8e290-113">Par exemple, que vous vouliez télécharger le code HTML à partir de dotnetfoundation.org sans bloquer le thread principal.</span><span class="sxs-lookup"><span data-stu-id="8e290-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="8e290-114">Vous pouvez l’atteindre comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e290-114">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="8e290-115">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="8e290-115">And that’s it!</span></span> <span data-ttu-id="8e290-116">À l’exception de l’utilisation de `async`, `let!`, et `return`, il s’agit simplement normale du code F #.</span><span class="sxs-lookup"><span data-stu-id="8e290-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="8e290-117">Il existe quelques constructions syntaxiques qui sont à noter :</span><span class="sxs-lookup"><span data-stu-id="8e290-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="8e290-118">`let!`lie le résultat d’une expression async (qui s’exécute sur un autre contexte).</span><span class="sxs-lookup"><span data-stu-id="8e290-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="8e290-119">`use!`fonctionne comme `let!`, mais supprime ses ressources liées lorsqu’il devient hors de portée.</span><span class="sxs-lookup"><span data-stu-id="8e290-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="8e290-120">`do!`un flux de travail asynchrone qui ne retourne rien attendra.</span><span class="sxs-lookup"><span data-stu-id="8e290-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="8e290-121">`return`simplement retourne un résultat d’une expression asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8e290-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="8e290-122">`return!`exécute un autre flux de travail asynchrone et retourne sa valeur de retour comme résultat.</span><span class="sxs-lookup"><span data-stu-id="8e290-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="8e290-123">En outre, normal `let`, `use`, et `do` mots clés peuvent être utilisés avec les versions asynchrones, comme ils le feraient dans une fonction normale.</span><span class="sxs-lookup"><span data-stu-id="8e290-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="8e290-124">Comment démarrer le Code asynchrone en F #</span><span class="sxs-lookup"><span data-stu-id="8e290-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="8e290-125">Comme mentionné précédemment, code asynchrone est une spécification de travail à effectuer dans un autre contexte, qui doit être démarrée explicitement.</span><span class="sxs-lookup"><span data-stu-id="8e290-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="8e290-126">Voici deux façons d’y parvenir :</span><span class="sxs-lookup"><span data-stu-id="8e290-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="8e290-127">`Async.RunSynchronously`démarre un flux de travail asynchrone sur un autre thread et attend son résultat.</span><span class="sxs-lookup"><span data-stu-id="8e290-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="8e290-128">`Async.Start`démarre un flux de travail asynchrone sur un autre thread et seront **pas** attend son résultat.</span><span class="sxs-lookup"><span data-stu-id="8e290-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="8e290-129">Autres manières de démarrer un flux de travail asynchrones disponible pour des scénarios plus spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8e290-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="8e290-130">Elles sont décrites en détail [dans la référence Async](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="8e290-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="8e290-131">Remarque sur les Threads</span><span class="sxs-lookup"><span data-stu-id="8e290-131">A Note on Threads</span></span>

<span data-ttu-id="8e290-132">La phrase « dans un autre thread » est mentionnée ci-dessus, mais il est important de savoir que **cela ne signifie pas que le flux de travail asynchrone est façade pour le multithreading**.</span><span class="sxs-lookup"><span data-stu-id="8e290-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="8e290-133">Le flux de travail réellement « accède » entre les threads, les emprunts pour une petite quantité de temps nécessaire pour effectuer des tâches utiles.</span><span class="sxs-lookup"><span data-stu-id="8e290-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="8e290-134">Lorsqu’un flux de travail asynchrone est effectivement « en attente » (par exemple, un appel réseau retourner un élément), n’importe quel thread qu'au moment où il a été d’emprunt est libérée jusqu'à accédez effectuez des tâches utiles sur autre chose.</span><span class="sxs-lookup"><span data-stu-id="8e290-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="8e290-135">Cela permet aux workflows asynchrones d’utiliser le système, sur qu'elles s’exécutent aussi efficacement que possible et les rend particulièrement fort pour les scénarios d’e/s élevées.</span><span class="sxs-lookup"><span data-stu-id="8e290-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="8e290-136">L’ajout de parallélisme à Code asynchrone</span><span class="sxs-lookup"><span data-stu-id="8e290-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="8e290-137">Parfois éventuellement besoin pour effectuer plusieurs tâches asynchrones en parallèle, collecter leurs résultats et les interpréter d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="8e290-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="8e290-138">`Async.Parallel`vous permet de faire sans devoir utiliser la bibliothèque parallèle de tâches, ce qui évite d’avoir à forcer `Task<'T>` et `Async<'T>` types.</span><span class="sxs-lookup"><span data-stu-id="8e290-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="8e290-139">L’exemple suivant utilise `Async.Parallel` pour télécharger le code HTML à partir de quatre sites populaires en parallèle, attendez que ces tâches à effectuer, puis l’imprimer le code HTML qui a été téléchargé.</span><span class="sxs-lookup"><span data-stu-id="8e290-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "http://www.microsoft.com"
      "http://www.google.com"
      "http://www.amazon.com"
      "http://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="8e290-140">Informations et conseils importants</span><span class="sxs-lookup"><span data-stu-id="8e290-140">Important Info and Advice</span></span>

*   <span data-ttu-id="8e290-141">Ajoutez « Async » à la fin de toutes les fonctions que vous allez utiliser</span><span class="sxs-lookup"><span data-stu-id="8e290-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="8e290-142">Bien qu’il s’agit simplement d’une convention d’affectation de noms, elle simplifie choses comme les API détectabilité.</span><span class="sxs-lookup"><span data-stu-id="8e290-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="8e290-143">En particulier s’il existe des versions synchrones et asynchrones de la routine de même, il est judicieux de déclarer explicitement qui est asynchrone via le nom.</span><span class="sxs-lookup"><span data-stu-id="8e290-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="8e290-144">Écouter le compilateur !</span><span class="sxs-lookup"><span data-stu-id="8e290-144">Listen to the compiler!</span></span>

 <span data-ttu-id="8e290-145">Compilateur F # est très stricte, rend pratiquement impossible d’effectuer une action troubling comme exécuter « async » code synchrone.</span><span class="sxs-lookup"><span data-stu-id="8e290-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="8e290-146">Si vous avez un avertissement, qui est un signe que le code ne sera pas exécuté comment vous pensez qu’il sera.</span><span class="sxs-lookup"><span data-stu-id="8e290-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="8e290-147">Si le compilateur peut rendre heureux, votre code s’exécutera probablement comme prévu.</span><span class="sxs-lookup"><span data-stu-id="8e290-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="8e290-148">Pour un programmeur C# /Visual Basic A-t-il F #</span><span class="sxs-lookup"><span data-stu-id="8e290-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="8e290-149">Cette section suppose que vous êtes familiarisé avec le modèle asynchrone en C# / VB.</span><span class="sxs-lookup"><span data-stu-id="8e290-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="8e290-150">Si vous n’êtes pas, [de programmation asynchrone en c#](../../../csharp/async.md) est un point de départ.</span><span class="sxs-lookup"><span data-stu-id="8e290-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="8e290-151">Il existe une différence fondamentale entre le modèle d’async C# /Visual Basic et le modèle asynchrone F #.</span><span class="sxs-lookup"><span data-stu-id="8e290-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="8e290-152">Lorsque vous appelez une fonction qui retourne un `Task` ou `Task<'T>`, que le travail a déjà commencé l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8e290-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="8e290-153">Le handle retourné représente une opération asynchrone en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8e290-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="8e290-154">En revanche, lorsque vous appelez une fonction async en F #, le `Async<'a>` retourné représente une tâche qui sera **généré** à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="8e290-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="8e290-155">Présentation de ce modèle est puissante, car elle permet des tâches asynchrones dans F # pour être chaînés ensemble, exécutées de manière conditionnelle et être démarrée avec une granularité plus fine du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8e290-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="8e290-156">Il existe quelques autres similitudes et différences à noter.</span><span class="sxs-lookup"><span data-stu-id="8e290-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="8e290-157">Similitudes</span><span class="sxs-lookup"><span data-stu-id="8e290-157">Similarities</span></span>

*   <span data-ttu-id="8e290-158">`let!`, `use!`, et `do!` sont analogues aux `await` lors de l’appel d’une tâche asynchrone à partir d’un `async{ }` bloc.</span><span class="sxs-lookup"><span data-stu-id="8e290-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="8e290-159">Les trois mots clés ne peuvent être utilisées dans un `async { }` bloc, similaire à la `await` peut uniquement être appelée à l’intérieur d’un `async` (méthode).</span><span class="sxs-lookup"><span data-stu-id="8e290-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="8e290-160">En bref, `let!` concerne lorsque vous souhaitez capturer et utiliser un résultat, `use!` est similaire, mais pour un élément dont les ressources doivent obtenir nettoyées après leur utilisation, et `do!` concerne lorsque vous souhaitez attendre d’un flux de travail asynchrone sans valeur de retour à la fin avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8e290-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="8e290-161">F # prend en charge de parallélisme de données de la même façon.</span><span class="sxs-lookup"><span data-stu-id="8e290-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="8e290-162">Bien qu’il fonctionne très différemment, `Async.Parallel` correspond à `Task.WhenAll` pour le scénario de souhaitant les résultats d’un ensemble de travaux d’async lorsque toutes les fois terminées.</span><span class="sxs-lookup"><span data-stu-id="8e290-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="8e290-163">Différences</span><span class="sxs-lookup"><span data-stu-id="8e290-163">Differences</span></span>

*   <span data-ttu-id="8e290-164">Imbriqué `let!` n’est pas autorisé, contrairement aux imbriqué`await`</span><span class="sxs-lookup"><span data-stu-id="8e290-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="8e290-165">Contrairement aux `await`, qui peut être imbriqué indéfiniment, `let!` ne peut pas et doit avoir son résultat à lié avant de l’utiliser à l’intérieur d’un autre `let!`, `do!`, ou `use!`.</span><span class="sxs-lookup"><span data-stu-id="8e290-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="8e290-166">Prise en charge l’annulation est plus simple en F # à en C# / VB.</span><span class="sxs-lookup"><span data-stu-id="8e290-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="8e290-167">Prise en charge de l’annulation d’une tâche au milieu son exécution dans C# /Visual Basic requiert une vérification de la `IsCancellationRequested` propriété ou l’appel `ThrowIfCancellationRequested()` sur un `CancellationToken` objet qui est passé à la méthode async.</span><span class="sxs-lookup"><span data-stu-id="8e290-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="8e290-168">En revanche, les workflows asynchrones F # sont plus naturellement pouvant être annulés.</span><span class="sxs-lookup"><span data-stu-id="8e290-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="8e290-169">L’annulation est un processus en trois étapes simple.</span><span class="sxs-lookup"><span data-stu-id="8e290-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="8e290-170">Créez un `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="8e290-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="8e290-171">Passer à une fonction de départ.</span><span class="sxs-lookup"><span data-stu-id="8e290-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="8e290-172">Appeler `Cancel` sur le jeton.</span><span class="sxs-lookup"><span data-stu-id="8e290-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="8e290-173">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8e290-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="8e290-174">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="8e290-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="8e290-175">Ressources supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="8e290-175">Further resources:</span></span>

*   [<span data-ttu-id="8e290-176">Flux de travail asynchrone sur MSDN</span><span class="sxs-lookup"><span data-stu-id="8e290-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="8e290-177">Séquences asynchrones pour F #</span><span class="sxs-lookup"><span data-stu-id="8e290-177">Asynchronous Sequences for F#</span></span>](http://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="8e290-178">Utilitaires de F # de données HTTP</span><span class="sxs-lookup"><span data-stu-id="8e290-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
