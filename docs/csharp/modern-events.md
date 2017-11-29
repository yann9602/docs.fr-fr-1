---
title: "Modèle d’événement .NET Core mis à jour"
description: "Découvrez toute la souplesse apportée par le modèle d’événement .NET Core et la compatibilité descendante et apprenez à implémenter un traitement sécurisé des événements grâce aux abonnés asynchrones."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="72dcf-104">Modèle d’événement .NET Core mis à jour</span><span class="sxs-lookup"><span data-stu-id="72dcf-104">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="72dcf-105">Précédent</span><span class="sxs-lookup"><span data-stu-id="72dcf-105">Previous</span></span>](event-pattern.md)

<span data-ttu-id="72dcf-106">L’article précédent décrit les modèles d’événements les plus courants.</span><span class="sxs-lookup"><span data-stu-id="72dcf-106">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="72dcf-107">.NET Core a un modèle plus souple.</span><span class="sxs-lookup"><span data-stu-id="72dcf-107">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="72dcf-108">Dans cette version, la définition `EventHandler<TEventArgs>` n’a plus la contrainte selon laquelle `TEventArgs` doit être une classe dérivée de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-108">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="72dcf-109">Ceci accroît la flexibilité pour vous et offre une compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="72dcf-109">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="72dcf-110">Commençons par la flexibilité.</span><span class="sxs-lookup"><span data-stu-id="72dcf-110">Let's start with the flexibility.</span></span> <span data-ttu-id="72dcf-111">La classe System.EventArgs introduit une méthode : `MemberwiseClone()`, qui crée une copie superficielle de l’objet.</span><span class="sxs-lookup"><span data-stu-id="72dcf-111">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="72dcf-112">Cette méthode doit utiliser la réflexion afin d’implémenter ses fonctionnalités pour n’importe quelle classe dérivée de `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-112">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="72dcf-113">Ces fonctionnalités sont plus faciles à créer dans une classe dérivée spécifique.</span><span class="sxs-lookup"><span data-stu-id="72dcf-113">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="72dcf-114">Cela signifie concrètement que la dérivation depuis System.EventArgs est une contrainte qui limite vos conceptions, mais n’offre aucun avantage supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="72dcf-114">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="72dcf-115">En fait, vous pouvez changer les définitions de `FileFoundArgs` et de `SearchDirectoryArgs` de façon à ce qu’ils ne dérivent pas de `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-115">In fact, you can changes the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="72dcf-116">Le programme fonctionnera exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="72dcf-116">The program will work exactly the same.</span></span>

<span data-ttu-id="72dcf-117">Vous pouvez également changer les `SearchDirectoryArgs` en un struct si vous faites une modification de plus :</span><span class="sxs-lookup"><span data-stu-id="72dcf-117">You could also change the `SearchDirectoryArgs` to a struct, if you also make one more change:</span></span>

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

<span data-ttu-id="72dcf-118">La modification supplémentaire consiste à appeler le constructeur par défaut avant d’entrer dans le constructeur qui initialise tous les champs.</span><span class="sxs-lookup"><span data-stu-id="72dcf-118">The additional change is to call the default constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="72dcf-119">Sans cet ajout, les règles de C# signalent que les propriétés sont accessibles avant qu’une valeur leur soit affectée.</span><span class="sxs-lookup"><span data-stu-id="72dcf-119">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="72dcf-120">Vous ne devez pas changer les `FileFoundArgs` d’une classe (type référence) en un struct (type valeur).</span><span class="sxs-lookup"><span data-stu-id="72dcf-120">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="72dcf-121">La raison en est que le protocole de gestion d’annulation nécessite que les arguments de l’événement soient passés par référence.</span><span class="sxs-lookup"><span data-stu-id="72dcf-121">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="72dcf-122">Si vous aviez apporté cette même modification, la classe de recherche de fichier ne pourrait jamais observer les modifications apportées par les abonnés à l’événement.</span><span class="sxs-lookup"><span data-stu-id="72dcf-122">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="72dcf-123">Une nouvelle copie de la structure serait utilisée pour chaque abonné, et cette copie serait une copie différente de celle vue par l’objet de recherche de fichier.</span><span class="sxs-lookup"><span data-stu-id="72dcf-123">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="72dcf-124">Voyons ensuite comment cette modification peut avoir une compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="72dcf-124">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="72dcf-125">La suppression de la contrainte n’affecte aucun code existant.</span><span class="sxs-lookup"><span data-stu-id="72dcf-125">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="72dcf-126">Les types d’arguments d’événement existants dérivent toujours de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-126">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="72dcf-127">La compatibilité descendante est une des raisons principales pour lesquelles ils continueront à dériver de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-127">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="72dcf-128">Les abonnés à l’événement existants seront les abonnés à un événement qui ont suivi le modèle classique.</span><span class="sxs-lookup"><span data-stu-id="72dcf-128">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="72dcf-129">Selon une logique similaire, aucun type d’argument d’événement créé maintenant n’aurait aucun abonné dans aucun des codes base existants.</span><span class="sxs-lookup"><span data-stu-id="72dcf-129">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="72dcf-130">Les nouveaux types d’événements qui ne dérivent pas de `System.EventArgs` ne vont pas arrêter ces codes base.</span><span class="sxs-lookup"><span data-stu-id="72dcf-130">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="72dcf-131">Événements avec des abonnés asynchrones</span><span class="sxs-lookup"><span data-stu-id="72dcf-131">Events with Async subscribers</span></span>

<span data-ttu-id="72dcf-132">Vous avez un modèle final à découvrir : comment écrire correctement des abonnés à l’événement qui appellent du code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="72dcf-132">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="72dcf-133">La difficulté est décrite dans l’article consacré à [async et await](async.md).</span><span class="sxs-lookup"><span data-stu-id="72dcf-133">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="72dcf-134">Les méthodes asynchrones peuvent avoir un type de retour void, mais ceci est fortement déconseillé.</span><span class="sxs-lookup"><span data-stu-id="72dcf-134">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="72dcf-135">Quand votre code pour l’abonné à l’événement appelle une méthode asynchrone, vous n’avez d’autre choix que de créer une méthode `async void`.</span><span class="sxs-lookup"><span data-stu-id="72dcf-135">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="72dcf-136">La signature de gestionnaire d’événements en a besoin.</span><span class="sxs-lookup"><span data-stu-id="72dcf-136">The event handler signature requires it.</span></span>

<span data-ttu-id="72dcf-137">Vous devez rapprocher ces deux nécessités opposées.</span><span class="sxs-lookup"><span data-stu-id="72dcf-137">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="72dcf-138">D’une façon ou d’une autre, vous devez créer une méthode `async void` sécurisée.</span><span class="sxs-lookup"><span data-stu-id="72dcf-138">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="72dcf-139">Les principes de base du modèle que vous devez implémenter sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="72dcf-139">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="72dcf-140">Notez d’abord que le gestionnaire est marqué en tant que gestionnaire asynchrone.</span><span class="sxs-lookup"><span data-stu-id="72dcf-140">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="72dcf-141">Comme il est affecté à un type délégué de gestionnaire d’événements, il a un type de retour void.</span><span class="sxs-lookup"><span data-stu-id="72dcf-141">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="72dcf-142">Cela signifie que vous devez suivre le modèle indiqué dans le gestionnaire et interdire la levée d’exceptions en dehors du contexte du gestionnaire asynchrone.</span><span class="sxs-lookup"><span data-stu-id="72dcf-142">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="72dcf-143">Comme il ne retourne pas une tâche, aucune tâche ne peut signaler l’erreur en passant à l’état d’erreur.</span><span class="sxs-lookup"><span data-stu-id="72dcf-143">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="72dcf-144">Comme la méthode est asynchrone, elle ne peut tout simplement pas lever l’exception.</span><span class="sxs-lookup"><span data-stu-id="72dcf-144">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="72dcf-145">(La méthode appelante a continué l’exécution, car elle est `async`.) Le comportement réel à l’exécution doit être défini différemment pour les différents environnements.</span><span class="sxs-lookup"><span data-stu-id="72dcf-145">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="72dcf-146">Il peut mettre fin au thread, mettre fin au programme ou laisser le programme dans un état indéterminé.</span><span class="sxs-lookup"><span data-stu-id="72dcf-146">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="72dcf-147">Aucune de ces possibilités ne constitue un résultat satisfaisant.</span><span class="sxs-lookup"><span data-stu-id="72dcf-147">None of those are good outcomes.</span></span>

<span data-ttu-id="72dcf-148">C’est pourquoi vous devez encapsuler l’instruction await pour la tâche asynchrone dans votre propre bloc try.</span><span class="sxs-lookup"><span data-stu-id="72dcf-148">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="72dcf-149">Si elle entraîne une erreur dans une tâche, vous pouvez consigner cette erreur.</span><span class="sxs-lookup"><span data-stu-id="72dcf-149">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="72dcf-150">Si c’est une erreur dont votre application ne peut pas récupérer, vous pouvez quitter le programme rapidement et normalement.</span><span class="sxs-lookup"><span data-stu-id="72dcf-150">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="72dcf-151">Ce sont les principales mises à jour du modèle d’événement .NET.</span><span class="sxs-lookup"><span data-stu-id="72dcf-151">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="72dcf-152">Vous pouvez voir de nombreux exemples des versions précédentes dans les bibliothèques avec lesquelles vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="72dcf-152">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="72dcf-153">Il est cependant important de bien comprendre ce que sont les derniers modèles.</span><span class="sxs-lookup"><span data-stu-id="72dcf-153">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="72dcf-154">Le prochain article de cette série vous permet de faire la distinction entre l’utilisation de `delegates` et de `events` dans vos conceptions.</span><span class="sxs-lookup"><span data-stu-id="72dcf-154">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="72dcf-155">Ces sont des concepts similaires : cet article vous aide à prendre la bonne décision pour vos programmes.</span><span class="sxs-lookup"><span data-stu-id="72dcf-155">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="72dcf-156">Suivant</span><span class="sxs-lookup"><span data-stu-id="72dcf-156">Next</span></span>](distinguish-delegates-events.md)
