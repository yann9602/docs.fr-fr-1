---
title: "Vue d’ensemble des types génériques (Génériques)"
description: "Découvrez dans quelle mesure les génériques peuvent faire office de modèles de code qui vous permettent de définir des structures de données de type sécurisé sans vous limiter à un type de données réel."
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.translationtype: HT
ms.sourcegitcommit: 934373d61407c8cc19b7d6424898a582880f9c21
ms.openlocfilehash: 08b8de2fe17a0032a1c1180667f39b1d6ce0feb6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---

# <a name="generic-types-generics-overview"></a><span data-ttu-id="355be-104">Vue d’ensemble des types génériques (Génériques)</span><span class="sxs-lookup"><span data-stu-id="355be-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="355be-105">Nous utilisons les génériques tout le temps en C#, implicitement ou explicitement.</span><span class="sxs-lookup"><span data-stu-id="355be-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="355be-106">Quand vous utilisez LINQ dans C#, avez-vous déjà remarqué que vous utilisez IEnumerable<T> ?</span><span class="sxs-lookup"><span data-stu-id="355be-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="355be-107">Sinon, si vous avez déjà vu un exemple en ligne d’un « dépôt générique » pour communiquer avec les bases de données à l’aide d’Entity Framework, avez-vous remarqué que la plupart des méthodes retournent IQueryable<T> ?</span><span class="sxs-lookup"><span data-stu-id="355be-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="355be-108">Vous vous êtes peut-être demandé ce que signifie le **T** dans ces exemples et pourquoi il s’y trouve ?</span><span class="sxs-lookup"><span data-stu-id="355be-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="355be-109">Présentés pour la première fois dans le .NET Framework 2.0, les génériques impliquaient des modifications du langage C# et du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="355be-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="355be-110">Les **génériques** sont essentiellement un « modèle de code » qui permet aux développeurs de définir des structures de données de [type sécurisé](https://msdn.microsoft.com/library/hbzz1a9a.aspx) sans se limiter à un type de données réel.</span><span class="sxs-lookup"><span data-stu-id="355be-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="355be-111">Par exemple, `List<T>` est une [collection générique](xref:System.Collections.Generic) qui peut être déclarée et utilisée avec n’importe quel type : `List<int>`, `List<string>`, `List<Person>`, etc.</span><span class="sxs-lookup"><span data-stu-id="355be-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="355be-112">Donc, quelle est l’idée ?</span><span class="sxs-lookup"><span data-stu-id="355be-112">So, what’s the point?</span></span> <span data-ttu-id="355be-113">Pourquoi les génériques sont-ils utiles ?</span><span class="sxs-lookup"><span data-stu-id="355be-113">Why are generics useful?</span></span> <span data-ttu-id="355be-114">Pour le comprendre, nous devons jeter un œil à une classe spécifique avant et après l’ajout des génériques.</span><span class="sxs-lookup"><span data-stu-id="355be-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="355be-115">Observons `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="355be-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="355be-116">Dans C# 1.0, les éléments `ArrayList` étaient de type `object`.</span><span class="sxs-lookup"><span data-stu-id="355be-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="355be-117">C’est-à-dire que n’importe quel élément ajouté était converti en `object` en mode silencieux. La même chose se produit quand on lit des éléments de la liste (ce processus est appelé [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) et unboxing, respectivement).</span><span class="sxs-lookup"><span data-stu-id="355be-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) and unboxing respectively).</span></span> <span data-ttu-id="355be-118">Le boxing et l’unboxing ont un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="355be-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="355be-119">Par ailleurs, il est impossible de déterminer au moment de la compilation le type réel des données de la liste.</span><span class="sxs-lookup"><span data-stu-id="355be-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="355be-120">Cela fragilise parfois le code.</span><span class="sxs-lookup"><span data-stu-id="355be-120">This makes for some fragile code.</span></span> <span data-ttu-id="355be-121">Les génériques résolvent ce problème en fournissant des informations supplémentaires sur le type de données que contient chaque instance de liste.</span><span class="sxs-lookup"><span data-stu-id="355be-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="355be-122">Pour faire simple, vous pouvez ajouter uniquement des entiers dans `List<int>` et uniquement des personnes dans `List<Person>`, etc.</span><span class="sxs-lookup"><span data-stu-id="355be-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="355be-123">Les génériques sont également disponibles au moment de l’exécution, ou **réifiés**.</span><span class="sxs-lookup"><span data-stu-id="355be-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="355be-124">Cela signifie que le runtime sait quel type de structure de données vous utilisez et peut le stocker dans la mémoire plus efficacement.</span><span class="sxs-lookup"><span data-stu-id="355be-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="355be-125">Voici un petit programme qui illustre à quel point il est efficace de connaître le type de structure de données au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="355be-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="355be-126">Ce programme produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="355be-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="355be-127">La première chose que vous remarquez ici est que le tri de la liste générique est beaucoup plus rapide que celui de la liste non générique.</span><span class="sxs-lookup"><span data-stu-id="355be-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="355be-128">Vous pouvez également noter que le type de la liste générique est différent ([System.Int32]) alors que le type de la liste non générique est généralisé.</span><span class="sxs-lookup"><span data-stu-id="355be-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="355be-129">Comme le runtime sait que le générique `List<int>` est de type int, il peut stocker les éléments de liste dans un tableau d’entiers sous-jacent dans la mémoire, alors que le non générique `ArrayList` doit effectuer un cast de chaque élément de liste en objet stocké dans un tableau d’objets dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="355be-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="355be-130">Comme le montre cet exemple, les casts supplémentaires prennent du temps et ralentissent le tri de la liste.</span><span class="sxs-lookup"><span data-stu-id="355be-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="355be-131">La dernière chose utile liée au fait que le runtime connaisse le type de votre générique est une meilleure expérience de débogage.</span><span class="sxs-lookup"><span data-stu-id="355be-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="355be-132">Quand vous déboguez un générique en C#, vous connaissez le type de chaque élément dans votre structure de données.</span><span class="sxs-lookup"><span data-stu-id="355be-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="355be-133">Sans les génériques, vous ne pourriez pas connaître le type de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="355be-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="355be-134">Ressources et informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="355be-134">Further reading and resources</span></span>

*   [<span data-ttu-id="355be-135">Présentation des génériques C#</span><span class="sxs-lookup"><span data-stu-id="355be-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="355be-136">Guide de programmation C# - Génériques</span><span class="sxs-lookup"><span data-stu-id="355be-136">C# Programming Guide - Generics</span></span>](https://msdn.microsoft.com/library/512aeb7t.aspx)

