---
title: Utilisation de LINQ
description: "Ce didacticiel vous apprend à générer des séquences avec LINQ, à écrire des méthodes pour les requêtes LINQ et à faire la distinction entre l’évaluation stricte et l’évaluation paresseuse."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.translationtype: Human Translation
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ec86c558b9aa9c6269fcf9890978f61a934c081f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="working-with-linq"></a><span data-ttu-id="4b493-104">Utilisation de LINQ</span><span class="sxs-lookup"><span data-stu-id="4b493-104">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="4b493-105">Introduction</span><span class="sxs-lookup"><span data-stu-id="4b493-105">Introduction</span></span>

<span data-ttu-id="4b493-106">Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.</span><span class="sxs-lookup"><span data-stu-id="4b493-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="4b493-107">Vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="4b493-107">You’ll learn:</span></span>

*   <span data-ttu-id="4b493-108">générer des séquences avec LINQ ;</span><span class="sxs-lookup"><span data-stu-id="4b493-108">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="4b493-109">écrire des méthodes utilisables dans des requêtes LINQ ;</span><span class="sxs-lookup"><span data-stu-id="4b493-109">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="4b493-110">faire la distinction entre l’évaluation stricte et l’évaluation paresseuse.</span><span class="sxs-lookup"><span data-stu-id="4b493-110">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="4b493-111">Vous apprendrez ces techniques en créant une application qui illustre l’une des compétences de base de tout magicien : le [mélange faro](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="4b493-111">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="4b493-112">En quelques mots, le mélange faro est une technique qui consiste à diviser un paquet de cartes en deux moitiés exactes, puis à intercaler une carte sur deux de chacune des deux moitiés de façon à reconstruire le jeu d’origine.</span><span class="sxs-lookup"><span data-stu-id="4b493-112">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="4b493-113">Les magiciens utilisent cette technique parce que chaque carte se trouve à un emplacement connu après chaque mélange, suivant un motif répétitif.</span><span class="sxs-lookup"><span data-stu-id="4b493-113">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="4b493-114">Dans notre cas, c’est une façon plaisante d’envisager la manipulation de séquences de données.</span><span class="sxs-lookup"><span data-stu-id="4b493-114">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="4b493-115">L’application que vous allez créer construira un jeu de cartes, puis effectuera une suite de mélanges, en affichant la séquence à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="4b493-115">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="4b493-116">Vous comparerez également le nouvel ordre à l’ordre d’origine.</span><span class="sxs-lookup"><span data-stu-id="4b493-116">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="4b493-117">Ce didacticiel comporte plusieurs étapes.</span><span class="sxs-lookup"><span data-stu-id="4b493-117">This tutorial has multiple steps.</span></span> <span data-ttu-id="4b493-118">Après chaque étape, vous pourrez exécuter l’application et voir la progression.</span><span class="sxs-lookup"><span data-stu-id="4b493-118">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="4b493-119">Vous pouvez également voir l’[exemple terminé](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) dans le dépôt GitHub dotnet/doc.</span><span class="sxs-lookup"><span data-stu-id="4b493-119">You can also see the [completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) in the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="4b493-120">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4b493-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b493-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4b493-121">Prerequisites</span></span>

<span data-ttu-id="4b493-122">Vous devez configurer votre ordinateur pour exécuter .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b493-122">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="4b493-123">Vous trouverez les instructions d’installation sur la page [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="4b493-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="4b493-124">Vous pouvez exécuter cette application sous Windows, Ubuntu Linux, OS X ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="4b493-124">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="4b493-125">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="4b493-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="4b493-126">Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), éditeur open source et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="4b493-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="4b493-127">Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.</span><span class="sxs-lookup"><span data-stu-id="4b493-127">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="4b493-128">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="4b493-128">Create the Application</span></span>

<span data-ttu-id="4b493-129">La première étape consiste à créer une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="4b493-129">The first step is to create a new application.</span></span> <span data-ttu-id="4b493-130">Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="4b493-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="4b493-131">Réglez-le comme répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="4b493-131">Make that the current directory.</span></span> <span data-ttu-id="4b493-132">Saisissez la commande `dotnet new console` à l’invite.</span><span class="sxs-lookup"><span data-stu-id="4b493-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="4b493-133">Elle crée les fichiers de démarrage d’une application « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="4b493-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="4b493-134">Si vous n’avez jamais utilisé C#, [ce didacticiel](console-teleprompter.md) explique la structure d’un programme C#.</span><span class="sxs-lookup"><span data-stu-id="4b493-134">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="4b493-135">Vous pouvez le lire, puis revenir ici pour en savoir plus sur LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b493-135">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="4b493-136">Création du jeu de données</span><span class="sxs-lookup"><span data-stu-id="4b493-136">Creating the Data Set</span></span>

<span data-ttu-id="4b493-137">Commençons par créer un jeu de cartes.</span><span class="sxs-lookup"><span data-stu-id="4b493-137">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="4b493-138">Vous allez pour cela utiliser une requête LINQ qui a deux sources (l’une pour les quatre couleurs, l’autre pour les treize valeurs).</span><span class="sxs-lookup"><span data-stu-id="4b493-138">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="4b493-139">Vous combinerez ces sources de façon à produire un jeu de 52 cartes.</span><span class="sxs-lookup"><span data-stu-id="4b493-139">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="4b493-140">Une instruction `Console.WriteLine` à l’intérieur d’une boucle `foreach` affiche les cartes.</span><span class="sxs-lookup"><span data-stu-id="4b493-140">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="4b493-141">Voici la requête :</span><span class="sxs-lookup"><span data-stu-id="4b493-141">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="4b493-142">Les clauses `from` multiples produisent un `SelectMany`, qui crée une séquence unique en combinant chaque élément de la première séquence avec chaque élément de la deuxième séquence.</span><span class="sxs-lookup"><span data-stu-id="4b493-142">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="4b493-143">L’ordre est important ici.</span><span class="sxs-lookup"><span data-stu-id="4b493-143">The order is important for our purposes.</span></span> <span data-ttu-id="4b493-144">Le premier élément de la première séquence source (couleurs) est associé à chacun des éléments de la deuxième séquence (valeurs).</span><span class="sxs-lookup"><span data-stu-id="4b493-144">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="4b493-145">Cette opération génère les treize cartes de la première couleur.</span><span class="sxs-lookup"><span data-stu-id="4b493-145">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="4b493-146">Ce processus est reproduit pour chaque élément de la première séquence (couleurs).</span><span class="sxs-lookup"><span data-stu-id="4b493-146">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="4b493-147">Le résultat final est un jeu de cartes classé par couleurs, puis par valeurs.</span><span class="sxs-lookup"><span data-stu-id="4b493-147">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="4b493-148">Vous devrez ensuite créer les méthodes Suits() et Ranks().</span><span class="sxs-lookup"><span data-stu-id="4b493-148">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="4b493-149">Commençons par un ensemble très simple de *méthodes d’itération* qui génèrent la séquence sous la forme d’une collection énumérable de chaînes :</span><span class="sxs-lookup"><span data-stu-id="4b493-149">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="4b493-150">Les deux méthodes utilisent la syntaxe `yield return` pour produire une séquence lors de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="4b493-150">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="4b493-151">Le compilateur génère un objet qui implémente `IEnumerable<T>` et génère la séquence de chaînes au fur et à mesure.</span><span class="sxs-lookup"><span data-stu-id="4b493-151">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="4b493-152">Ensuite, exécutez l’exemple que vous avez commencé à élaborer.</span><span class="sxs-lookup"><span data-stu-id="4b493-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="4b493-153">Il affiche les 52 cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="4b493-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="4b493-154">Il peut être très utile d’exécuter cet exemple avec un débogueur pour observer la façon dont les méthodes `Suits()` et `Values()` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="4b493-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="4b493-155">Vous pouvez clairement voir que chaque chaîne de chaque séquence est générée uniquement au moment requis.</span><span class="sxs-lookup"><span data-stu-id="4b493-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Fenêtre console montrant l’application produisant les 52 cartes](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="4b493-157">Manipulation de l’ordre</span><span class="sxs-lookup"><span data-stu-id="4b493-157">Manipulating the Order</span></span>

<span data-ttu-id="4b493-158">Ensuite, nous allons créer une méthode utilitaire pour effectuer le mélange.</span><span class="sxs-lookup"><span data-stu-id="4b493-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="4b493-159">La première étape consiste à couper le jeu en deux.</span><span class="sxs-lookup"><span data-stu-id="4b493-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="4b493-160">Les méthodes `Take()` et `Skip()`, qui font partie de l’API LINQ, nous fournissent cette fonctionnalité :</span><span class="sxs-lookup"><span data-stu-id="4b493-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="4b493-161">La méthode de mélange n’existe pas dans la bibliothèque standard ; vous devez donc écrire la vôtre.</span><span class="sxs-lookup"><span data-stu-id="4b493-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="4b493-162">Cette nouvelle méthode illustre plusieurs techniques que vous allez utiliser avec des programmes LINQ. Nous allons expliquer les différentes parties de la méthode au fil des étapes.</span><span class="sxs-lookup"><span data-stu-id="4b493-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="4b493-163">La signature de la méthode crée une *méthode d’extension* :</span><span class="sxs-lookup"><span data-stu-id="4b493-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="4b493-164">Une méthode d’extension est une *méthode statique* qui répond à un objectif spécifique.</span><span class="sxs-lookup"><span data-stu-id="4b493-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="4b493-165">On peut voir l’ajout du modificateur `this` au premier argument de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4b493-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="4b493-166">Cela signifie que vous appelez la méthode comme s’il s’agissait d’une méthode membre du type du premier argument.</span><span class="sxs-lookup"><span data-stu-id="4b493-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="4b493-167">Les méthodes d’extension ne peuvent être déclarées qu’à l’intérieur de classes `static` : nous allons donc créer une nouvelle classe statique appelée `extensions` pour cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="4b493-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="4b493-168">Vous ajouterez d’autres méthodes d’extension au fur et à mesure de ce didacticiel, et toutes seront placées dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="4b493-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="4b493-169">Cette déclaration de méthode suit également un idiome standard selon lequel les types d’entrée et de sortie sont `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="4b493-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="4b493-170">Cette pratique permet d’enchaîner les méthodes LINQ afin d’exécuter des requêtes plus complexes.</span><span class="sxs-lookup"><span data-stu-id="4b493-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="4b493-171">Vous allez énumérer les deux séquences à la fois, en intercalant les éléments et en créant un seul objet.</span><span class="sxs-lookup"><span data-stu-id="4b493-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="4b493-172">Pour écrire une méthode LINQ qui fonctionne avec deux séquences, vous devez comprendre comment `IEnumerable` fonctionne.</span><span class="sxs-lookup"><span data-stu-id="4b493-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="4b493-173">L’interface `IEnumerable` possède une seule méthode : `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="4b493-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="4b493-174">L’objet retourné par `GetEnumerator()` a une méthode permettant d’atteindre l’élément suivant et une propriété qui récupère l’élément actif dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="4b493-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="4b493-175">Vous allez utiliser ces deux membres pour énumérer la collection et retourner les éléments.</span><span class="sxs-lookup"><span data-stu-id="4b493-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="4b493-176">Cette méthode Interleave sera une méthode d’itération ; par conséquent, au lieu de créer une collection et de la retourner, vous allez utiliser la syntaxe `yield return` présentée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="4b493-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="4b493-177">Voici l’implémentation de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="4b493-177">Here's the implementation of that method:</span></span>

<span data-ttu-id="4b493-178">[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]</span><span class="sxs-lookup"><span data-stu-id="4b493-178">[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]</span></span>

<span data-ttu-id="4b493-179">Maintenant que vous avez écrit cette méthode, revenez à la méthode `Main` et mélangez le jeu une fois :</span><span class="sxs-lookup"><span data-stu-id="4b493-179">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="4b493-180">Comparaisons</span><span class="sxs-lookup"><span data-stu-id="4b493-180">Comparisons</span></span>

<span data-ttu-id="4b493-181">Nous allons voir combien de mélanges sont nécessaires pour remettre le jeu dans l’ordre d’origine.</span><span class="sxs-lookup"><span data-stu-id="4b493-181">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="4b493-182">Vous devrez écrire une méthode qui détermine si deux séquences sont égales.</span><span class="sxs-lookup"><span data-stu-id="4b493-182">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="4b493-183">Ensuite, il vous faudra placer le code qui mélange le jeu dans une boucle et vérifier si le jeu est de nouveau dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="4b493-183">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="4b493-184">Vous ne devriez pas avoir de problèmes à écrire une méthode qui détermine si deux séquences sont égales.</span><span class="sxs-lookup"><span data-stu-id="4b493-184">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="4b493-185">La structure est similaire à celle de la méthode que vous avez écrite pour mélanger le jeu.</span><span class="sxs-lookup"><span data-stu-id="4b493-185">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="4b493-186">Seulement, cette fois, au lieu de retourner chaque élément, vous allez comparer les éléments correspondants de chaque séquence.</span><span class="sxs-lookup"><span data-stu-id="4b493-186">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="4b493-187">Une fois que la séquence aura été énumérée en entier, si tous les éléments correspondent, les séquences sont les mêmes :</span><span class="sxs-lookup"><span data-stu-id="4b493-187">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

<span data-ttu-id="4b493-188">[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]</span><span class="sxs-lookup"><span data-stu-id="4b493-188">[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]</span></span>

<span data-ttu-id="4b493-189">Cet exemple montre un autre idiome Linq : les méthodes terminales.</span><span class="sxs-lookup"><span data-stu-id="4b493-189">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="4b493-190">Elles prennent une séquence en entrée (ou, dans ce cas, deux séquences) et retournent une valeur scalaire unique.</span><span class="sxs-lookup"><span data-stu-id="4b493-190">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="4b493-191">Ces méthodes, lorsqu’elles sont utilisées, sont toujours les dernières méthodes d’une requête.</span><span class="sxs-lookup"><span data-stu-id="4b493-191">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="4b493-192">(D’où leur nom.)</span><span class="sxs-lookup"><span data-stu-id="4b493-192">(Hence the name).</span></span> 

<span data-ttu-id="4b493-193">Vous pourrez les voir en action lorsque vous les utiliserez pour déterminer si le jeu est dans l’ordre d’origine.</span><span class="sxs-lookup"><span data-stu-id="4b493-193">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="4b493-194">Placez le code de mélange à l’intérieur d’une boucle, et arrêtez-la lorsque la séquence est à nouveau dans l’ordre d’origine en appliquant la méthode `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="4b493-194">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="4b493-195">Vous pouvez voir qu’il s’agit toujours de la dernière méthode d’une requête, parce qu’elle retourne une valeur unique plutôt qu’une séquence :</span><span class="sxs-lookup"><span data-stu-id="4b493-195">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="4b493-196">Exécutez l’exemple, et regardez comment le jeu se réorganise à chaque mélange, jusqu’à ce qu’il revienne à sa configuration d’origine après huit itérations.</span><span class="sxs-lookup"><span data-stu-id="4b493-196">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="4b493-197">Optimisations</span><span class="sxs-lookup"><span data-stu-id="4b493-197">Optimizations</span></span>

<span data-ttu-id="4b493-198">L’exemple que vous avez produit jusque-là exécute un *mélange intérieur*, où les cartes du haut et du bas restent les mêmes à chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="4b493-198">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="4b493-199">Faisons une modification, et exécutons un *mélange extérieur*, où les 52 cartes changent toutes de position.</span><span class="sxs-lookup"><span data-stu-id="4b493-199">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="4b493-200">Dans le cas d’un mélange extérieur, on intercale les deux moitiés du jeu de sorte que la première carte de la moitié du dessous devienne la première carte du jeu.</span><span class="sxs-lookup"><span data-stu-id="4b493-200">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="4b493-201">Cela signifie que la dernière carte de la moitié du dessus devient la carte du bas.</span><span class="sxs-lookup"><span data-stu-id="4b493-201">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="4b493-202">Il n’y a qu’une ligne à modifier.</span><span class="sxs-lookup"><span data-stu-id="4b493-202">That's just a one line change.</span></span> <span data-ttu-id="4b493-203">Mettez à jour l’appel à la fonction de mélange pour modifier l’ordre des moitiés du dessus et du dessous du jeu :</span><span class="sxs-lookup"><span data-stu-id="4b493-203">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="4b493-204">Réexécutez le programme : vous verrez qu’il faut 52 itérations pour que le jeu se réorganise.</span><span class="sxs-lookup"><span data-stu-id="4b493-204">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="4b493-205">Vous commencerez également à remarquer de sérieuses dégradations des performances lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="4b493-205">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="4b493-206">Il y a plusieurs raisons à cela.</span><span class="sxs-lookup"><span data-stu-id="4b493-206">There are a number of reasons for this.</span></span> <span data-ttu-id="4b493-207">Attaquons-nous à l’une des causes principales : l’utilisation inefficace de *l’évaluation paresseuse*.</span><span class="sxs-lookup"><span data-stu-id="4b493-207">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="4b493-208">Les requêtes LINQ sont évaluées de façon retardée.</span><span class="sxs-lookup"><span data-stu-id="4b493-208">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="4b493-209">Les séquences sont générées uniquement au moment où les éléments sont demandés.</span><span class="sxs-lookup"><span data-stu-id="4b493-209">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="4b493-210">En règle générale, c’est un avantage majeur de LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b493-210">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="4b493-211">Toutefois, dans une utilisation du type de ce programme, cela entraîne une croissance exponentielle de la durée d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4b493-211">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="4b493-212">Le jeu d’origine a été généré à l’aide d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b493-212">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="4b493-213">Chaque mélange est généré en effectuant trois requêtes LINQ sur le jeu précédent.</span><span class="sxs-lookup"><span data-stu-id="4b493-213">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="4b493-214">Toutes ces opérations sont effectuées de façon retardée.</span><span class="sxs-lookup"><span data-stu-id="4b493-214">All these are performed lazily.</span></span> <span data-ttu-id="4b493-215">Cela signifie également qu’elles sont effectuées à chaque fois que la séquence est demandée.</span><span class="sxs-lookup"><span data-stu-id="4b493-215">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="4b493-216">À la 52e itération, vous aurez régénéré le jeu d’origine de nombreuses fois.</span><span class="sxs-lookup"><span data-stu-id="4b493-216">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="4b493-217">Nous allons écrire dans un journal pour illustrer ce comportement.</span><span class="sxs-lookup"><span data-stu-id="4b493-217">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="4b493-218">Ensuite, vous résoudrez le problème.</span><span class="sxs-lookup"><span data-stu-id="4b493-218">Then, you'll fix it.</span></span>

<span data-ttu-id="4b493-219">Voici une méthode de journalisation qui peut être ajoutée aux requêtes pour marquer la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="4b493-219">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

<span data-ttu-id="4b493-220">[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]</span><span class="sxs-lookup"><span data-stu-id="4b493-220">[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]</span></span>

<span data-ttu-id="4b493-221">Instrumentez ensuite la définition de chaque requête avec un message de journalisation :</span><span class="sxs-lookup"><span data-stu-id="4b493-221">Next, instrument the definition of each query with a log message:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="4b493-222">Remarquez que vous n’écrivez pas dans le journal à chaque fois que vous accédez à une requête,</span><span class="sxs-lookup"><span data-stu-id="4b493-222">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="4b493-223">mais seulement lors de la création de la requête d’origine.</span><span class="sxs-lookup"><span data-stu-id="4b493-223">You log only when you create the original query.</span></span> <span data-ttu-id="4b493-224">Le programme met toujours longtemps à s’exécuter, mais vous pouvez maintenant voir pourquoi.</span><span class="sxs-lookup"><span data-stu-id="4b493-224">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="4b493-225">Si vous perdez patience au cours de l’exécution du mélange extérieur avec journalisation, revenez au mélange intérieur.</span><span class="sxs-lookup"><span data-stu-id="4b493-225">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="4b493-226">Vous verrez quand même les effets de l’évaluation paresseuse.</span><span class="sxs-lookup"><span data-stu-id="4b493-226">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="4b493-227">Sur une itération, elle exécute 2 592 requêtes, génération de toutes les valeurs et couleurs comprise.</span><span class="sxs-lookup"><span data-stu-id="4b493-227">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="4b493-228">Il y a un moyen simple de mettre à jour ce programme afin d’éviter toutes ces exécutions.</span><span class="sxs-lookup"><span data-stu-id="4b493-228">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="4b493-229">Les méthodes LINQ `ToArray()` et `ToList()` provoquent l’exécution de la requête et stockent les résultats respectivement dans un tableau ou dans une liste.</span><span class="sxs-lookup"><span data-stu-id="4b493-229">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="4b493-230">On utilise ces méthodes pour mettre en cache les données résultant d’une requête plutôt que de réexécuter la requête source.</span><span class="sxs-lookup"><span data-stu-id="4b493-230">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="4b493-231">Ajoutez les requêtes qui génèrent les jeux de cartes avec un appel à `ToArray()` et réexécutez la requête :</span><span class="sxs-lookup"><span data-stu-id="4b493-231">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

<span data-ttu-id="4b493-232">[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]</span><span class="sxs-lookup"><span data-stu-id="4b493-232">[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]</span></span>

<span data-ttu-id="4b493-233">Réexécutez-la : le mélange intérieur est descendu à 30 requêtes.</span><span class="sxs-lookup"><span data-stu-id="4b493-233">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="4b493-234">Si vous repassez au mélange extérieur, vous constaterez des améliorations similaires.</span><span class="sxs-lookup"><span data-stu-id="4b493-234">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="4b493-235">(Il exécute à présent 162 requêtes.)</span><span class="sxs-lookup"><span data-stu-id="4b493-235">(It now executes 162 queries).</span></span>

<span data-ttu-id="4b493-236">Ne déduisez pas de cet exemple que toutes les requêtes devraient s’exécuter de façon stricte.</span><span class="sxs-lookup"><span data-stu-id="4b493-236">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="4b493-237">Cet exemple est conçu pour mettre en évidence les cas d’usage où l’évaluation paresseuse peut causer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="4b493-237">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="4b493-238">La raison en est que chaque nouvelle disposition du jeu de cartes est construite à partir de la configuration précédente.</span><span class="sxs-lookup"><span data-stu-id="4b493-238">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="4b493-239">Avec l’évaluation paresseuse, chaque nouvelle configuration du jeu est générée à partir du jeu d’origine, y compris l’exécution du code qui a construit `startingDeck`,</span><span class="sxs-lookup"><span data-stu-id="4b493-239">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="4b493-240">ce qui entraîne une grande quantité de travail supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="4b493-240">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="4b493-241">Dans la pratique, certains algorithmes fonctionnent beaucoup mieux avec l’évaluation stricte, d’autres avec l’évaluation paresseuse.</span><span class="sxs-lookup"><span data-stu-id="4b493-241">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="4b493-242">(En général, l’évaluation paresseuse est un bien meilleur choix lorsque la source de données est un processus distinct, comme un moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="4b493-242">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="4b493-243">Dans ce cas, l’évaluation paresseuse permet d’exécuter des requêtes plus complexes avec un seul aller-retour vers le processus de base de données.) LINQ permet à la fois l’évaluation paresseuse et l’évaluation stricte.</span><span class="sxs-lookup"><span data-stu-id="4b493-243">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="4b493-244">Évaluez et choisissez la meilleure des deux.</span><span class="sxs-lookup"><span data-stu-id="4b493-244">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="4b493-245">Préparation des nouvelles fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="4b493-245">Preparing for New Features</span></span>

<span data-ttu-id="4b493-246">Le code que vous avez écrit pour cet exemple est un prototype simple qui remplit sa fonction.</span><span class="sxs-lookup"><span data-stu-id="4b493-246">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="4b493-247">C’est un excellent moyen d’explorer un problème d’espace ; pour de nombreuses fonctionnalités, il s’agit peut-être de la meilleure solution permanente.</span><span class="sxs-lookup"><span data-stu-id="4b493-247">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="4b493-248">Vous avez tiré profit des *types anonymes* pour les cartes, et chaque carte est représentée par des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b493-248">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="4b493-249">Les *types anonymes* présentent de nombreux avantages du point de vue de la productivité.</span><span class="sxs-lookup"><span data-stu-id="4b493-249">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="4b493-250">Vous n’avez pas besoin de définir vous-même une classe pour représenter le stockage.</span><span class="sxs-lookup"><span data-stu-id="4b493-250">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="4b493-251">Le compilateur génère le type à votre place.</span><span class="sxs-lookup"><span data-stu-id="4b493-251">The compiler generates the type for you.</span></span> <span data-ttu-id="4b493-252">Le type généré par le compilateur utilise plusieurs des bonnes pratiques pour les objets de données simples.</span><span class="sxs-lookup"><span data-stu-id="4b493-252">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="4b493-253">Il est *non modifiable*, ce qui signifie qu’aucune de ses propriétés ne peut être modifiée une fois qu’il a été construit.</span><span class="sxs-lookup"><span data-stu-id="4b493-253">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="4b493-254">Les types anonymes sont internes à un assembly ; ainsi, ils ne sont pas visibles dans le cadre de l’API publique de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="4b493-254">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="4b493-255">Les types anonymes contiennent également une substitution de la méthode `ToString()` qui retourne une chaîne mise en forme avec chacune des valeurs.</span><span class="sxs-lookup"><span data-stu-id="4b493-255">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="4b493-256">Les types anonymes présentent également des inconvénients.</span><span class="sxs-lookup"><span data-stu-id="4b493-256">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="4b493-257">Ils n’ont pas de nom accessible ; vous ne pouvez donc pas les utiliser comme valeurs renvoyées ou comme arguments.</span><span class="sxs-lookup"><span data-stu-id="4b493-257">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="4b493-258">Vous remarquerez que toutes les méthodes ci-dessus qui ont utilisé ces types anonymes sont des méthodes génériques.</span><span class="sxs-lookup"><span data-stu-id="4b493-258">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="4b493-259">La substitution de `ToString()` peut ne pas être idéale lorsque l’application gagne en fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="4b493-259">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="4b493-260">L’exemple utilise également des chaînes pour la couleur et le rang de chaque carte.</span><span class="sxs-lookup"><span data-stu-id="4b493-260">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="4b493-261">C’est un système très ouvert.</span><span class="sxs-lookup"><span data-stu-id="4b493-261">That's quite open ended.</span></span> <span data-ttu-id="4b493-262">Le système de type C# peut nous permettre d’améliorer le code, en tirant profit des types `enum` pour ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4b493-262">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="4b493-263">Commencez par les couleurs.</span><span class="sxs-lookup"><span data-stu-id="4b493-263">Start with the suits.</span></span> <span data-ttu-id="4b493-264">C’est le moment idéal pour utiliser `enum` :</span><span class="sxs-lookup"><span data-stu-id="4b493-264">This is a perfect time to use an `enum`:</span></span>

<span data-ttu-id="4b493-265">[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]</span><span class="sxs-lookup"><span data-stu-id="4b493-265">[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]</span></span>

<span data-ttu-id="4b493-266">La méthode `Suits()` modifie également le type et l’implémentation :</span><span class="sxs-lookup"><span data-stu-id="4b493-266">The `Suits()` method also changes type and implementation:</span></span>

<span data-ttu-id="4b493-267">[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]</span><span class="sxs-lookup"><span data-stu-id="4b493-267">[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]</span></span>

<span data-ttu-id="4b493-268">Ensuite, effectuez la même modification avec le rang des cartes :</span><span class="sxs-lookup"><span data-stu-id="4b493-268">Next, do the same change with the Rank of the cards:</span></span>

<span data-ttu-id="4b493-269">[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]</span><span class="sxs-lookup"><span data-stu-id="4b493-269">[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]</span></span>

<span data-ttu-id="4b493-270">Et la méthode qui les génère :</span><span class="sxs-lookup"><span data-stu-id="4b493-270">And the method that generates them:</span></span>

<span data-ttu-id="4b493-271">[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]</span><span class="sxs-lookup"><span data-stu-id="4b493-271">[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]</span></span>

<span data-ttu-id="4b493-272">En guise de nettoyage final, créons un type pour représenter la carte, au lieu d’utiliser un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="4b493-272">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="4b493-273">Les types anonymes sont parfaits comme types légers et locaux ; mais, dans cet exemple, la carte à jouer représente l’un des principaux concepts.</span><span class="sxs-lookup"><span data-stu-id="4b493-273">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="4b493-274">Elle doit avoir un type concret.</span><span class="sxs-lookup"><span data-stu-id="4b493-274">It should be a concrete type.</span></span>

<span data-ttu-id="4b493-275">[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]</span><span class="sxs-lookup"><span data-stu-id="4b493-275">[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]</span></span>

<span data-ttu-id="4b493-276">Ce type utilise des *propriétés en lecture seule implémentées automatiquement* qui sont définies dans le constructeur et ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="4b493-276">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="4b493-277">Il utilise également la nouvelle fonctionnalité *d’interpolation de chaîne*, qui facilite le formatage des chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b493-277">It also makes use of the new *string interpolation* feature that makes it easier to format string output.</span></span>

<span data-ttu-id="4b493-278">Mettez à jour la requête qui génère le jeu de départ pour qu’elle utilise le nouveau type :</span><span class="sxs-lookup"><span data-stu-id="4b493-278">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="4b493-279">Compilez, puis réexécutez-la.</span><span class="sxs-lookup"><span data-stu-id="4b493-279">Compile and run again.</span></span> <span data-ttu-id="4b493-280">La sortie est un peu plus propre, et le code est un peu plus clair et peut être étendu plus facilement.</span><span class="sxs-lookup"><span data-stu-id="4b493-280">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="4b493-281">Conclusion</span><span class="sxs-lookup"><span data-stu-id="4b493-281">Conclusion</span></span>

<span data-ttu-id="4b493-282">Cet exemple vous a montré quelques-unes des méthodes utilisées dans LINQ, comment créer vos propres méthodes, faciles à utiliser avec du code compatible LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b493-282">This sample should you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="4b493-283">Il vous a également montré les différences entre l’évaluation paresseuse et l’évaluation stricte, ainsi que l’impact de cette décision sur les performances.</span><span class="sxs-lookup"><span data-stu-id="4b493-283">It also showed you the differences between lazy and eager evaluation, and the affect that decision can have on performance.</span></span>

<span data-ttu-id="4b493-284">Vous avez appris une technique de magicien.</span><span class="sxs-lookup"><span data-stu-id="4b493-284">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="4b493-285">Les magiciens utilisent le mélange faro pour pouvoir contrôler le déplacement de chaque carte dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="4b493-285">Magician's use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="4b493-286">Dans certains tours, le magicien invite un spectateur à placer une carte au-dessus du jeu et le mélange plusieurs fois, tout en sachant l’emplacement de la carte.</span><span class="sxs-lookup"><span data-stu-id="4b493-286">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="4b493-287">D’autres illusions nécessitent que le jeu soit préparé d’une certaine manière.</span><span class="sxs-lookup"><span data-stu-id="4b493-287">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="4b493-288">Le magicien prépare le jeu avant de réaliser le tour.</span><span class="sxs-lookup"><span data-stu-id="4b493-288">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="4b493-289">Ensuite, il effectue cinq mélanges intérieurs.</span><span class="sxs-lookup"><span data-stu-id="4b493-289">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="4b493-290">Sur scène, il peut montrer que le jeu paraît mélangé, le mélanger trois fois de plus et se retrouver avec le jeu organisé de la façon souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4b493-290">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>

