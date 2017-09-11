---
title: Indexeurs
description: "Découvrez les indexeurs C# et la façon d’implémenter des propriétés indexées, qui sont des propriétés référencées à l’aide d’un ou plusieurs arguments."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 468c86f36fe71558dcd7a9150337f5a3cce066b8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="indexers"></a><span data-ttu-id="0cc7b-104">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="0cc7b-104">Indexers</span></span>

<span data-ttu-id="0cc7b-105">Les *indexeurs* sont similaires aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-105">*Indexers* are similar to properties.</span></span> <span data-ttu-id="0cc7b-106">Les indexeurs sont souvent construits à l’aide des mêmes fonctionnalités de langage que les [propriétés](properties.md).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-106">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="0cc7b-107">Il permettent l’utilisation de propriétés *indexées*, qui sont référencées à l’aide d’un ou plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-107">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="0cc7b-108">Ces arguments fournissent un index dans une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-108">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="0cc7b-109">Syntaxe de l’indexeur</span><span class="sxs-lookup"><span data-stu-id="0cc7b-109">Indexer Syntax</span></span>

<span data-ttu-id="0cc7b-110">Vous pouvez accéder à un indexeur via un nom de variable et des crochets.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-110">You access an indexer through a variable name and square brackets .</span></span> <span data-ttu-id="0cc7b-111">Vous devez placer les arguments de l’indexeur entre crochets :</span><span class="sxs-lookup"><span data-stu-id="0cc7b-111">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="0cc7b-112">Déclarez les indexeurs en utilisant le mot clé `this` comme nom de propriété et en déclarant les arguments entre crochets.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-112">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="0cc7b-113">Cette déclaration correspond à l’utilisation abordée dans le paragraphe précédent :</span><span class="sxs-lookup"><span data-stu-id="0cc7b-113">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="0cc7b-114">Dans ce premier exemple, vous pouvez voir la relation entre la syntaxe des propriétés et celle des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-114">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="0cc7b-115">Cette analogie s’applique à la plupart des règles de syntaxe des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-115">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="0cc7b-116">Les indexeurs peuvent avoir n’importe quel modificateur d’accès valide (public, protected internal, protected, internal ou private).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-116">Indexers can have any valid access modifiers (public, protected internal, protected, internal, or private).</span></span> <span data-ttu-id="0cc7b-117">Ils peuvent être sealed, virtual ou abstract.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-117">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="0cc7b-118">Comme pour les propriétés, vous pouvez spécifier des modificateurs d’accès différents pour les accesseurs get et set d’un indexeur.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-118">As with properties, you can specify different access modifiers for the get and set accesssors in an indexer.</span></span>
<span data-ttu-id="0cc7b-119">Vous pouvez également spécifier des indexeurs en lecture seule (en omettant l’accesseur set) ou des indexeurs en écriture seule (en omettant l’accesseur get).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-119">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="0cc7b-120">Vous pouvez appliquer aux indexeurs quasiment tout ce que vous avez appris de l’utilisation des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-120">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="0cc7b-121">La seule exception à cette règle sont les *propriétés implémentées automatiquement*.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-121">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="0cc7b-122">Le compilateur ne peut pas toujours générer le stockage adapté à l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-122">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="0cc7b-123">C’est la présence d’arguments référençant un élément dans un ensemble d’éléments qui distingue les indexeurs des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-123">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="0cc7b-124">Vous pouvez définir plusieurs indexeurs sur un type, tant que chaque indexeur a sa propre liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-124">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="0cc7b-125">Nous allons explorer différents scénarios où vous pourrez utiliser un ou plusieurs indexeurs dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-125">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="0cc7b-126">Scénarios</span><span class="sxs-lookup"><span data-stu-id="0cc7b-126">Scenarios</span></span>

<span data-ttu-id="0cc7b-127">Vous définissez des *indexeurs* dans votre type quand son API modélise une collection dans laquelle vous définissez des arguments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-127">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="0cc7b-128">Vos indexeurs peuvent ou non être mappés directement aux types de collection qui font partie du framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-128">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="0cc7b-129">Votre type peut avoir d’autres responsabilités en plus de la modélisation d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-129">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="0cc7b-130">Les indexeurs vous permettent de fournir l’API qui correspond à l’abstraction de votre type sans exposer les détails internes concernant le stockage ou le calcul des valeurs de cette abstraction.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-130">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="0cc7b-131">Examinons quelques-uns des scénarios courants d’utilisation des *indexeurs*.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-131">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="0cc7b-132">Vous pouvez accéder au [dossier d’exemples d’indexeurs](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-132">You can access the [sample folder for indexers](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers).</span></span> <span data-ttu-id="0cc7b-133">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-133">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="0cc7b-134">Tableaux et vecteurs</span><span class="sxs-lookup"><span data-stu-id="0cc7b-134">Arrays and Vectors</span></span>

<span data-ttu-id="0cc7b-135">L’un des scénarios de création d’indexeur les plus courants est lorsque votre type modélise un tableau ou un vecteur.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-135">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="0cc7b-136">Vous pouvez créer un indexeur pour modéliser une liste de données triées.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-136">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="0cc7b-137">L’avantage de créer votre propre indexeur est que vous pouvez définir le stockage de cette collection en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-137">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="0cc7b-138">Imaginez un scénario où votre type modélise des données d’historique qui sont trop volumineuses pour être chargées en une seule fois dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-138">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="0cc7b-139">Vous devez charger et décharger des sections de la collection selon leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-139">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="0cc7b-140">L’exemple suivant modélise ce comportement.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-140">The example following models this behavior.</span></span> <span data-ttu-id="0cc7b-141">Il signale le nombre de points de données.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-141">It reports on how many data points exist.</span></span> <span data-ttu-id="0cc7b-142">Il crée à la demande des pages contenant des sections de données.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-142">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="0cc7b-143">Il supprime des pages de la mémoire afin de libérer de l’espace pour les pages qui ont fait l’objet de demandes récentes.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-143">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

<span data-ttu-id="0cc7b-144">Vous pouvez suivre cet idiome de conception afin de modéliser toute sorte de collection pour laquelle il existe de bonnes raisons de ne pas charger l’intégralité des données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-144">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="0cc7b-145">Notez que la classe `Page` est une classe privée imbriquée qui ne fait pas partie de l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-145">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="0cc7b-146">Ces détails sont masqués pour tous les utilisateurs de cette classe.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-146">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="0cc7b-147">Dictionnaires</span><span class="sxs-lookup"><span data-stu-id="0cc7b-147">Dictionaries</span></span>

<span data-ttu-id="0cc7b-148">Un autre scénario courant est lorsque vous avez besoin de modéliser un dictionnaire ou un mappage.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-148">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="0cc7b-149">Dans ce cas, votre type stocke des valeurs en fonction des clés, généralement des clés de texte.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-149">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="0cc7b-150">Cet exemple crée un dictionnaire qui mappe les arguments de ligne de commande à des [expressions lambda](delegates-overview.md) qui gèrent ces options.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-150">This example creates a dictionary that maps command line arguments to [lamdba expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="0cc7b-151">L’exemple suivant montre deux classes : une classe `ArgsActions` qui mappe une option de ligne de commande à un délégué `Action`, et un `ArgsProcessor` qui utilise `ArgsActions` pour exécuter chaque `Action` quand il rencontre cette option.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-151">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

<span data-ttu-id="0cc7b-152">Dans cet exemple, la collection `ArgsAction` correspond étroitement à la collection sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-152">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="0cc7b-153">`get` détermine si une option donnée a été configurée.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-153">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="0cc7b-154">Si c’est le cas, il retourne le `Action` associé à cette option.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-154">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="0cc7b-155">Sinon, il retourne un `Action` qui n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-155">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="0cc7b-156">L’accesseur public n’inclut pas d’accesseur `set`,</span><span class="sxs-lookup"><span data-stu-id="0cc7b-156">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="0cc7b-157">mais il comprend la conception qui utilise une méthode publique pour définir des options.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-157">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="0cc7b-158">Mappages multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="0cc7b-158">Multi-Dimensional Maps</span></span>

<span data-ttu-id="0cc7b-159">Vous pouvez créer des indexeurs qui utilisent plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-159">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="0cc7b-160">En outre, ces arguments ne sont pas contraints à être du même type.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-160">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="0cc7b-161">Examinons ces deux exemples.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-161">Let's look at two examples.</span></span>   

<span data-ttu-id="0cc7b-162">Le premier exemple montre une classe qui génère des valeurs pour un ensemble de Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-162">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="0cc7b-163">Pour plus d’informations sur les mathématiques impliquées par cet ensemble, lisez [cet article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-163">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="0cc7b-164">L’indexeur utilise deux doubles pour définir un point dans le plan X, Y.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-164">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="0cc7b-165">L’accesseur get calcule le nombre d’itérations jusqu’à un point déterminé pour ne pas se trouver dans l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-165">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="0cc7b-166">Si le nombre maximal d’itérations est atteint, le point se trouve dans l’ensemble, et la valeur maxIterations de la classe est retournée.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-166">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="0cc7b-167">Les images générées par ordinateur popularisées par l’ensemble de Mandelbrot définissent des couleurs pour le nombre d’itérations qui sont nécessaires pour déterminer qu’un point se trouve en dehors de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-167">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

<span data-ttu-id="0cc7b-168">L’ensemble de Mandelbrot définit des valeurs à chaque coordonnée (x, y) pour des valeurs de nombres réels.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-168">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="0cc7b-169">Cela définit un dictionnaire qui peut contenir un nombre infini de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-169">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="0cc7b-170">Par conséquent, aucun stockage n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-170">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="0cc7b-171">Cette classe calcule la valeur de chaque point lorsque le code appelle l’accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-171">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="0cc7b-172">Aucun stockage sous-jacent n’est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-172">There's no underlying storage used.</span></span>

<span data-ttu-id="0cc7b-173">Examinons une dernière utilisation d’indexeur, dans laquelle l’indexeur accepte plusieurs arguments de types différents.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-173">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="0cc7b-174">Prenons un programme qui gère des données d’historique des températures.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-174">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="0cc7b-175">Cet indexeur utilise une ville et une date pour définir ou obtenir les températures minimales et maximales de la ville en question :</span><span class="sxs-lookup"><span data-stu-id="0cc7b-175">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

```csharp
using DateMeasurements = 
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = 
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

<span data-ttu-id="0cc7b-176">Cet exemple crée un indexeur qui mappe des données météorologiques sur deux arguments différents : une ville (représentée par un `string`) et une date (représentée par un `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="0cc7b-176">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="0cc7b-177">Le stockage interne utilise deux classes `Dictionary` pour représenter le dictionnaire à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-177">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="0cc7b-178">L’API publique ne représente plus le stockage sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-178">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="0cc7b-179">Les fonctionnalités de langage des indexeurs vous permettent de créer une interface publique qui représente votre abstraction, même si le stockage sous-jacent doit utiliser des types de collections de base différents.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-179">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="0cc7b-180">Ce code comprend deux sections avec lesquelles vous pouvez ne pas être familier.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-180">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="0cc7b-181">Les deux instructions `using`</span><span class="sxs-lookup"><span data-stu-id="0cc7b-181">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="0cc7b-182">créent un *alias* pour un type générique construit.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-182">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="0cc7b-183">Ces instructions permettent au code d’utiliser plus tard les noms plus descriptifs que sont `DateMeasurements` et `CityDateMeasurements`, au lieu de la construction générique de `Dictionary<DateTime, Measurements>` et `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-183">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="0cc7b-184">Cette construction nécessite l’utilisation de noms de types qualifiés complets à droite du signe `=`.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-184">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="0cc7b-185">La deuxième technique consiste à supprimer les sections de date et heure de tous les objets `DateTime` utilisés pour indexer des collections.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-185">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="0cc7b-186">Le .NET Framework ne comprend pas de type de date uniquement.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-186">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="0cc7b-187">Les développeurs utilisent le type `DateTime`, mais utilisent la propriété `Date` pour s’assurer qu’il n’existe pas d’objets `DateTime` égaux pour ce jour-là.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-187">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="0cc7b-188">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="0cc7b-188">Summing Up</span></span>

<span data-ttu-id="0cc7b-189">Vous devez créer des indexeurs chaque fois que vous avez un élément de type propriété dans votre classe, où cette propriété ne représente pas une valeur unique, mais une collection de valeurs dans laquelle chaque élément est identifié par un ensemble d’arguments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-189">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="0cc7b-190">Ces arguments peuvent identifier quel élément de la collection doit être référencé.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-190">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="0cc7b-191">Les indexeurs étendent le concept de [propriété](properties.md), où un membre est considéré comme un élément de données extérieur à la classe, mais aussi comme une méthode supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-191">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="0cc7b-192">Les indexeurs autorisent les arguments à rechercher un élément d’une propriété qui représente un ensemble d’éléments.</span><span class="sxs-lookup"><span data-stu-id="0cc7b-192">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>

