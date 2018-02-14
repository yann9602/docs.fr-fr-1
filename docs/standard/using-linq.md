---
title: LINQ (Language Integrated Query)
description: "Découvrez comment LINQ fournit des fonctionnalités de requête au niveau du langage, ainsi qu’une API pour C# et VB qui permet d’écrire du code déclaratif expressif."
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb9bc30c31ab02df7c04c885f59cadfcc1f00253
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="80c27-104">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="80c27-104">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="80c27-105">Qu’est-ce que c’est ?</span><span class="sxs-lookup"><span data-stu-id="80c27-105">What is it?</span></span>

<span data-ttu-id="80c27-106">LINQ fournit des fonctionnalités d’interrogation au niveau du langage et une API de [fonction d’ordre supérieur](https://en.wikipedia.org/wiki/Higher-order_function) pour C# et VB pour pouvoir écrire du code déclaratif, expressif.</span><span class="sxs-lookup"><span data-stu-id="80c27-106">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="80c27-107">Syntaxe de requête au niveau du langage :</span><span class="sxs-lookup"><span data-stu-id="80c27-107">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="80c27-108">Même exemple en utilisant l’API `IEnumerable<T>` :</span><span class="sxs-lookup"><span data-stu-id="80c27-108">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="80c27-109">LINQ est expressif</span><span class="sxs-lookup"><span data-stu-id="80c27-109">LINQ is Expressive</span></span>

<span data-ttu-id="80c27-110">Imaginez que vous avez une liste d’animaux domestiques, mais que vous voulez la convertir en dictionnaire dans lequel vous pouvez accéder à un animal directement par sa valeur `RFID`.</span><span class="sxs-lookup"><span data-stu-id="80c27-110">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="80c27-111">Code impératif traditionnel :</span><span class="sxs-lookup"><span data-stu-id="80c27-111">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="80c27-112">L’intention du code n’est pas de créer un `Dictionary<int, Pet>` et d’y ajouter des éléments par une boucle, c’est de convertir une liste existante en dictionnaire !</span><span class="sxs-lookup"><span data-stu-id="80c27-112">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="80c27-113">LINQ conserve l’intention contrairement au code impératif.</span><span class="sxs-lookup"><span data-stu-id="80c27-113">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="80c27-114">Expression LINQ équivalente :</span><span class="sxs-lookup"><span data-stu-id="80c27-114">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="80c27-115">Le code qui utilise LINQ est utile, car il égalise le terrain entre l’intention et le code dans un contexte de programmation.</span><span class="sxs-lookup"><span data-stu-id="80c27-115">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="80c27-116">Un autre bonus est la concision du code.</span><span class="sxs-lookup"><span data-stu-id="80c27-116">Another bonus is code brevity.</span></span> <span data-ttu-id="80c27-117">Imaginez que vous pouvez réduire d’un tiers les grandes parties d’un code Base comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="80c27-117">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="80c27-118">Intéressant, n’est-ce pas ?</span><span class="sxs-lookup"><span data-stu-id="80c27-118">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="80c27-119">Les fournisseurs LINQ simplifient l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="80c27-119">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="80c27-120">Pour la plupart des logiciels en général, tout tourne autour du traitement de données à partir d’une source (bases de données, JSON, XML, etc.).</span><span class="sxs-lookup"><span data-stu-id="80c27-120">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="80c27-121">Cela implique souvent d’apprendre une nouvelle API par source de données, ce qui peut s’avérer fastidieux.</span><span class="sxs-lookup"><span data-stu-id="80c27-121">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="80c27-122">LINQ simplifie le problème en faisant abstraction de l’accès aux éléments de donnée communs dans une syntaxe de requête qui semble la même, quelle que soit la source de données choisie.</span><span class="sxs-lookup"><span data-stu-id="80c27-122">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="80c27-123">Imaginons que vous recherchez tous les éléments XML avec une valeur d’attribut spécifique.</span><span class="sxs-lookup"><span data-stu-id="80c27-123">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="80c27-124">Écrire du code pour parcourir manuellement le document XML afin de rechercher ces éléments est une tâche très complexe.</span><span class="sxs-lookup"><span data-stu-id="80c27-124">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="80c27-125">Les fournisseurs LINQ ne vous permettent pas seulement d’interagir avec le XML.</span><span class="sxs-lookup"><span data-stu-id="80c27-125">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="80c27-126">[LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) est un mappeur ORM (Object-Relational Mapper) de base de données MSSQL relativement minimaliste.</span><span class="sxs-lookup"><span data-stu-id="80c27-126">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="80c27-127">La bibliothèque [JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fournit un balayage efficace du document JSON via LINQ.</span><span class="sxs-lookup"><span data-stu-id="80c27-127">The [JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="80c27-128">Par ailleurs, si vous n’avez pas de bibliothèque pour faire ce dont vous avez besoin, vous pouvez également [écrire votre propre fournisseur LINQ](https://msdn.microsoft.com/library/Bb546158.aspx) !</span><span class="sxs-lookup"><span data-stu-id="80c27-128">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="80c27-129">Pourquoi utiliser la syntaxe de requête ?</span><span class="sxs-lookup"><span data-stu-id="80c27-129">Why Use the Query Syntax?</span></span>

<span data-ttu-id="80c27-130">C’est une question qui revient souvent.</span><span class="sxs-lookup"><span data-stu-id="80c27-130">This is a question which often comes up.</span></span> <span data-ttu-id="80c27-131">Après tout,</span><span class="sxs-lookup"><span data-stu-id="80c27-131">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="80c27-132">est beaucoup plus concis que ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="80c27-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="80c27-133">La syntaxe d’API n’est-elle pas simplement un moyen plus concis d’effectuer la syntaxe de requête ?</span><span class="sxs-lookup"><span data-stu-id="80c27-133">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="80c27-134">Non.</span><span class="sxs-lookup"><span data-stu-id="80c27-134">No.</span></span> <span data-ttu-id="80c27-135">La syntaxe de requête permet d’utiliser la clause **let**, ce qui vous permet d’introduire et de lier une variable dans la portée de l’expression, en l’utilisant dans les parties suivantes de l’expression.</span><span class="sxs-lookup"><span data-stu-id="80c27-135">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="80c27-136">Vous pouvez reproduire le même code avec la seule syntaxe d’API, mais vous obtiendrez très probablement du code difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="80c27-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="80c27-137">Ce qui nous amène à la question suivante : **devez-vous vous contenter d’utiliser la syntaxe de requête ?**</span><span class="sxs-lookup"><span data-stu-id="80c27-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="80c27-138">La réponse à cette question est **oui**, si...</span><span class="sxs-lookup"><span data-stu-id="80c27-138">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="80c27-139">Votre code Base utilise déjà la syntaxe de requête</span><span class="sxs-lookup"><span data-stu-id="80c27-139">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="80c27-140">Vous devez définir l’étendue des variables dans vos requêtes en raison de la complexité</span><span class="sxs-lookup"><span data-stu-id="80c27-140">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="80c27-141">Vous préférez la syntaxe de requête et elle ne vous détournera pas de votre code Base</span><span class="sxs-lookup"><span data-stu-id="80c27-141">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="80c27-142">La réponse à cette question est **non**, si...</span><span class="sxs-lookup"><span data-stu-id="80c27-142">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="80c27-143">Votre code Base utilise déjà la syntaxe d’API</span><span class="sxs-lookup"><span data-stu-id="80c27-143">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="80c27-144">Vous n’avez pas besoin de définir l’étendue des variables dans vos requêtes</span><span class="sxs-lookup"><span data-stu-id="80c27-144">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="80c27-145">Vous préférez la syntaxe d’API et elle ne vous détournera pas de votre code Base</span><span class="sxs-lookup"><span data-stu-id="80c27-145">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="80c27-146">Exemples essentiels</span><span class="sxs-lookup"><span data-stu-id="80c27-146">Essential Samples</span></span>

<span data-ttu-id="80c27-147">Pour obtenir la liste complète des exemples LINQ, consultez [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b) (101 exemples LINQ).</span><span class="sxs-lookup"><span data-stu-id="80c27-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="80c27-148">Voici une démonstration rapide de quelques-uns des éléments essentiels de LINQ.</span><span class="sxs-lookup"><span data-stu-id="80c27-148">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="80c27-149">Ces exemples ne sont pas exhaustifs, car LINQ fournit beaucoup plus de fonctionnalités que ce qui est présenté ici.</span><span class="sxs-lookup"><span data-stu-id="80c27-149">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="80c27-150">Les indispensables : `Where`, `Select` et `Aggregate` :</span><span class="sxs-lookup"><span data-stu-id="80c27-150">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing then lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   <span data-ttu-id="80c27-151">Aplanissement d’une liste de listes :</span><span class="sxs-lookup"><span data-stu-id="80c27-151">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="80c27-152">Union entre deux ensembles (avec un comparateur personnalisé) :</span><span class="sxs-lookup"><span data-stu-id="80c27-152">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // default hashcode is enough here, as these are simple objects.
        return b.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="80c27-153">Intersection entre deux ensembles :</span><span class="sxs-lookup"><span data-stu-id="80c27-153">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="80c27-154">Tri :</span><span class="sxs-lookup"><span data-stu-id="80c27-154">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="80c27-155">Enfin, un exemple plus avancé : déterminer si les valeurs des propriétés de deux instances du même type sont égales (emprunté à [ce billet StackOverflow](http://stackoverflow.com/a/844855) et modifié) :</span><span class="sxs-lookup"><span data-stu-id="80c27-155">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self != null && to != null)
    {
        var type = typeof(T);
        var ignoreList = new List<string>(ignore);

        // Selects the properties which have unequal values into a sequence of those properties.
        var unequalProperties = from pi in type.GetProperties(BindingFlags.Public | BindingFlags.Instance)
                                where !ignoreList.Contains(pi.Name)
                                let selfValue = type.GetProperty(pi.Name).GetValue(self, null)
                                let toValue = type.GetProperty(pi.Name).GetValue(to, null)
                                where selfValue != toValue && (selfValue == null || !selfValue.Equals(toValue))
                                select new { Prop = pi.Name, selfValue, toValue };
        return !unequalProperties.Any();
    }

    return self == to;
}
```

## <a name="plinq"></a><span data-ttu-id="80c27-156">PLINQ</span><span class="sxs-lookup"><span data-stu-id="80c27-156">PLINQ</span></span>

<span data-ttu-id="80c27-157">PLINQ, ou Parallel LINQ, est un moteur d’exécution parallèle pour les expressions LINQ.</span><span class="sxs-lookup"><span data-stu-id="80c27-157">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="80c27-158">En d’autres termes, des expressions régulières LINQ peuvent être parallélisées de manière simple sur n’importe quel nombre de threads.</span><span class="sxs-lookup"><span data-stu-id="80c27-158">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="80c27-159">Cela s’effectue par un appel à `AsParallel()` avant l’expression.</span><span class="sxs-lookup"><span data-stu-id="80c27-159">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="80c27-160">Considérez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="80c27-160">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

<span data-ttu-id="80c27-161">Ce code partitionne `facebookUsers` entre les threads système si nécessaire, additionne le nombre total de mentions J’aime sur chaque thread en parallèle, additionne les résultats calculés par chaque thread et projette ce résultat dans une chaîne très pratique.</span><span class="sxs-lookup"><span data-stu-id="80c27-161">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="80c27-162">Sous forme de diagramme :</span><span class="sxs-lookup"><span data-stu-id="80c27-162">In diagram form:</span></span>

![Diagramme PLINQ](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="80c27-164">Les tâches parallèles utilisant le processeur qui peuvent être facilement exprimées par LINQ (en d’autres termes, qui sont des fonctions pures et n’ont aucun effet secondaire) sont parfaites pour PLINQ.</span><span class="sxs-lookup"><span data-stu-id="80c27-164">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="80c27-165">Pour les tâches qui _ont_ un effet secondaire, utilisez la [bibliothèque parallèle de tâches](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="80c27-165">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="80c27-166">Ressources supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="80c27-166">Further Resources:</span></span>

*   [<span data-ttu-id="80c27-167">101 exemples LINQ</span><span class="sxs-lookup"><span data-stu-id="80c27-167">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="80c27-168">[Linqpad](https://www.linqpad.net/), environnement de laboratoire et moteur d’interrogation de base de données pour C#/F#/VB</span><span class="sxs-lookup"><span data-stu-id="80c27-168">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="80c27-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), livre électronique pour apprendre comment LINQ-to-objects est implémenté</span><span class="sxs-lookup"><span data-stu-id="80c27-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
