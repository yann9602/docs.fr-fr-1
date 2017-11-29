---
title: "Délégués et expressions lambda"
description: "Découvrez comment les délégués définissent un type, qui spécifie une signature de méthode particulière, qui peut être appelée directement ou passée à une autre méthode et appelée."
keywords: .NET, .NET Core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: d04a158db4f97a0e37f8a92149a3f237ee2e5434
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="2aa99-104">Délégués et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="2aa99-104">Delegates and lambdas</span></span>

<span data-ttu-id="2aa99-105">Les délégués définissent un type, qui spécifie la signature d’une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="2aa99-105">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="2aa99-106">Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée.</span><span class="sxs-lookup"><span data-stu-id="2aa99-106">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="2aa99-107">L’exemple suivant montre l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="2aa99-107">The following example demonstrates delegate use.</span></span>

```csharp
public class Program
{

  public delegate string Reverse(string s);

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Reverse rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

*   <span data-ttu-id="2aa99-108">Sur la ligne 4, nous créons un type délégué d’une certaine signature, dans notre exemple, une méthode qui accepte un paramètre de chaîne, puis renvoie un paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="2aa99-108">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="2aa99-109">Sur la ligne 6, nous définissons l’implémentation du délégué en fournissant une méthode qui a exactement la même signature.</span><span class="sxs-lookup"><span data-stu-id="2aa99-109">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="2aa99-110">Sur la ligne 13, la méthode est attribuée à un type conforme au délégué `Reverse`.</span><span class="sxs-lookup"><span data-stu-id="2aa99-110">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="2aa99-111">Enfin, sur la ligne 15, nous appelons le délégué en passant une chaîne à inverser.</span><span class="sxs-lookup"><span data-stu-id="2aa99-111">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="2aa99-112">Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer.</span><span class="sxs-lookup"><span data-stu-id="2aa99-112">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="2aa99-113">Il s’agit de `Func<>`, `Action<>` et `Predicate<>`. Ils peuvent être utilisés à plusieurs endroits dans les API .NET, sans avoir à définir de nouveaux types délégués.</span><span class="sxs-lookup"><span data-stu-id="2aa99-113">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="2aa99-114">Bien sûr, il existe certaines différences entre ces trois types, comme vous pouvez le constater dans leurs signatures, qui sont principalement liées à la manière dont ils doivent être utilisés :</span><span class="sxs-lookup"><span data-stu-id="2aa99-114">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="2aa99-115">`Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué.</span><span class="sxs-lookup"><span data-stu-id="2aa99-115">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="2aa99-116">`Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent.</span><span class="sxs-lookup"><span data-stu-id="2aa99-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="2aa99-117">C’est le cas, par exemple, des projections.</span><span class="sxs-lookup"><span data-stu-id="2aa99-117">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="2aa99-118">`Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué.</span><span class="sxs-lookup"><span data-stu-id="2aa99-118">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="2aa99-119">Il peut également être écrit comme un `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="2aa99-119">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="2aa99-120">Nous pouvons maintenant reprendre notre exemple ci-dessus et le réécrire à l’aide du délégué `Func<>` au lieu d’un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2aa99-120">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="2aa99-121">Le programme continue à s’exécuter exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="2aa99-121">The program will continue running exactly the same.</span></span>

```csharp
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

<span data-ttu-id="2aa99-122">Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode Main().</span><span class="sxs-lookup"><span data-stu-id="2aa99-122">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="2aa99-123">C’est pourquoi .NET Framework 2.0 a introduit le concept des **délégués anonymes**.</span><span class="sxs-lookup"><span data-stu-id="2aa99-123">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="2aa99-124">Grâce à eux, vous pouvez créer des délégués « inline », sans avoir à spécifier un autre type ou méthode.</span><span class="sxs-lookup"><span data-stu-id="2aa99-124">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="2aa99-125">Vous insérez simplement la définition du délégué là où vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="2aa99-125">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="2aa99-126">En guise d’exemple, nous allons utiliser notre délégué anonyme pour filtrer une liste uniquement sur les nombres pairs et les imprimer dans la console.</span><span class="sxs-lookup"><span data-stu-id="2aa99-126">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="2aa99-127">Notez les lignes en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="2aa99-127">Notice the highlighted lines.</span></span> <span data-ttu-id="2aa99-128">Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué.</span><span class="sxs-lookup"><span data-stu-id="2aa99-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="2aa99-129">Mais au lieu d’être une définition séparée, nous l’avons introduit _ad hoc_ dans notre appel à la méthode `FindAll()` du type `List<T>`.</span><span class="sxs-lookup"><span data-stu-id="2aa99-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="2aa99-130">Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile.</span><span class="sxs-lookup"><span data-stu-id="2aa99-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="2aa99-131">C’est là que les **expressions lambda** interviennent.</span><span class="sxs-lookup"><span data-stu-id="2aa99-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="2aa99-132">Les expressions lambda ont été initialement introduites dans C# 3.0 comme l’un des principaux blocs de construction de la requête LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="2aa99-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="2aa99-133">Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="2aa99-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="2aa99-134">Elles déclarent une signature et un corps de méthode, mais n’ont pas d’identité formelle propre, sauf si elles sont attribuées à un délégué.</span><span class="sxs-lookup"><span data-stu-id="2aa99-134">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="2aa99-135">Contrairement aux délégués, elles peuvent être directement attribuées comme côté gauche de l’inscription d’événement, ou dans plusieurs clauses et méthodes Linq.</span><span class="sxs-lookup"><span data-stu-id="2aa99-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="2aa99-136">Dans la mesure où une expression lambda est simplement une autre façon de spécifier un délégué, nous pouvons réécrire l’exemple ci-dessus pour utiliser une expression lambda au lieu d’un délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="2aa99-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(i => i % 2 == 0);

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="2aa99-137">Si vous jetez un œil aux lignes en surbrillance, vous pouvez voir à quoi ressemble une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="2aa99-137">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="2aa99-138">Là encore, il s’agit simplement d’une syntaxe **très** pratique pour l’utilisation des délégués. Par conséquent, ce qui se passe en coulisses est très proche de ce qui se passe avec le délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="2aa99-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="2aa99-139">Comme les expressions lambda sont juste des délégués, elles peuvent servir de gestionnaire d’événements sans aucun problème, comme l’illustre l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2aa99-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

## <a name="further-reading-and-resources"></a><span data-ttu-id="2aa99-140">Ressources et informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2aa99-140">Further reading and resources</span></span>

*   [<span data-ttu-id="2aa99-141">Délégués</span><span class="sxs-lookup"><span data-stu-id="2aa99-141">Delegates</span></span>](https://msdn.microsoft.com/library/ms173171.aspx)
*   [<span data-ttu-id="2aa99-142">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="2aa99-142">Anonymous Functions</span></span>](https://msdn.microsoft.com/library/bb882516.aspx)
*   [<span data-ttu-id="2aa99-143">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="2aa99-143">Lambda expressions</span></span>](https://msdn.microsoft.com/library/bb397687.aspx)
