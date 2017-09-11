---
title: "Délégués fortement typés"
description: "Découvrez comment utiliser des types délégués génériques pour déclarer des types personnalisés lors de la création d’une fonctionnalité nécessitant des délégués."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0a8185c21e129c91b2c3ecb1f74f8ce2f75c5db9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="strongly-typed-delegates"></a><span data-ttu-id="e5312-104">Délégués fortement typés</span><span class="sxs-lookup"><span data-stu-id="e5312-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="e5312-105">Précédent</span><span class="sxs-lookup"><span data-stu-id="e5312-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="e5312-106">Dans l’article précédent, vous avez vu que vous pouviez créer des types délégués spécifiques à l’aide du mot clé `delegate`.</span><span class="sxs-lookup"><span data-stu-id="e5312-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="e5312-107">La classe abstraite Delegate fournit l’infrastructure pour l’invocation et le couplage faible.</span><span class="sxs-lookup"><span data-stu-id="e5312-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="e5312-108">Les types délégués concrets deviennent beaucoup plus utiles en adoptant et en appliquant la sécurité de type pour les méthodes qui sont ajoutées à la liste d’invocation d’un objet délégué.</span><span class="sxs-lookup"><span data-stu-id="e5312-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="e5312-109">Quand vous utilisez le mot clé `delegate` et que vous définissez un type délégué concret, le compilateur génère ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="e5312-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="e5312-110">Dans la pratique, cela conduirait à la création de types délégués chaque fois que vous avez besoin d’une signature de méthode différente.</span><span class="sxs-lookup"><span data-stu-id="e5312-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="e5312-111">Ce travail peut devenir fastidieux au bout d’un moment.</span><span class="sxs-lookup"><span data-stu-id="e5312-111">This work could get tedious after a time.</span></span> <span data-ttu-id="e5312-112">Chaque nouvelle fonctionnalité nécessite de nouveaux types délégués.</span><span class="sxs-lookup"><span data-stu-id="e5312-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="e5312-113">Heureusement, cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e5312-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="e5312-114">Le framework .NET Core contient plusieurs types que vous pouvez réutiliser chaque fois que vous avez besoin de types délégués.</span><span class="sxs-lookup"><span data-stu-id="e5312-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="e5312-115">Il s’agit de définitions [génériques](programming-guide/generics/index.md). Vous pouvez ainsi déclarer des personnalisations quand vous avez besoin de nouvelles déclarations de méthode.</span><span class="sxs-lookup"><span data-stu-id="e5312-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="e5312-116">Le premier de ces types est le type @System.Action et plusieurs variantes :</span><span class="sxs-lookup"><span data-stu-id="e5312-116">The first of these types is the @System.Action type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="e5312-117">Le modificateur `in` sur l’argument de type générique est traité dans l’article sur la covariance.</span><span class="sxs-lookup"><span data-stu-id="e5312-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e5312-118">Il existe des variantes du délégué `Action` qui contiennent jusqu’à 16 arguments comme @System.Action%6016.</span><span class="sxs-lookup"><span data-stu-id="e5312-118">There are variations of the `Action` delegate that contain up to 16 arguments such as @System.Action%6016 .</span></span>
<span data-ttu-id="e5312-119">Il est important que ces définitions utilisent différents arguments génériques pour chacun des arguments de délégués : cela offre une flexibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="e5312-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="e5312-120">Les arguments de méthode ne doivent pas obligatoirement être du même type, mais il peuvent l’être.</span><span class="sxs-lookup"><span data-stu-id="e5312-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="e5312-121">Utilisez l’un des types `Action` pour tout type délégué ayant un type de retour void.</span><span class="sxs-lookup"><span data-stu-id="e5312-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="e5312-122">Le framework inclut également plusieurs types délégués génériques que vous pouvez utiliser pour les types délégués qui retournent des valeurs :</span><span class="sxs-lookup"><span data-stu-id="e5312-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="e5312-123">Le modificateur `out` sur l’argument de type générique de résultat est traité dans l’article sur la covariance.</span><span class="sxs-lookup"><span data-stu-id="e5312-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e5312-124">Il existe des variantes du délégué `Func` qui contiennent jusqu’à 16 arguments d’entrée comme @System.Func%6017.</span><span class="sxs-lookup"><span data-stu-id="e5312-124">There are variations of the `Func` delegate with up to 16 input arguments such as @System.Func%6017 .</span></span>
<span data-ttu-id="e5312-125">Par convention, le type du résultat est toujours le dernier paramètre de type dans toutes les déclarations `Func`.</span><span class="sxs-lookup"><span data-stu-id="e5312-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="e5312-126">Utilisez l’un des types `Func` pour tout type délégué qui retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="e5312-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="e5312-127">Il existe aussi un type @System.Predicate%601 spécialisé pour un délégué qui retourne un test sur une valeur unique :</span><span class="sxs-lookup"><span data-stu-id="e5312-127">There's also a specialized @System.Predicate%601 type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="e5312-128">Vous remarquerez que pour tout type `Predicate`, il existe un type `Func` structurellement équivalent, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e5312-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="e5312-129">Ces deux types peuvent vous sembler équivalents,</span><span class="sxs-lookup"><span data-stu-id="e5312-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="e5312-130">mais ils ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="e5312-130">They are not.</span></span>
<span data-ttu-id="e5312-131">Ces deux variables ne sont pas interchangeables.</span><span class="sxs-lookup"><span data-stu-id="e5312-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="e5312-132">Une variable d’un type ne peut pas être assignée à l’autre type.</span><span class="sxs-lookup"><span data-stu-id="e5312-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="e5312-133">Le système de type C# utilise les noms des types définis, pas la structure.</span><span class="sxs-lookup"><span data-stu-id="e5312-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="e5312-134">Toutes ces définitions de types délégués dans la bibliothèque .NET Core doivent signifier que vous n’avez pas besoin de définir un nouveau type délégué pour toute nouvelle fonctionnalité que vous créez et qui nécessite des délégués.</span><span class="sxs-lookup"><span data-stu-id="e5312-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="e5312-135">Ces définitions génériques doivent fournir tous les types délégués dont vous avez besoin dans la plupart des situations.</span><span class="sxs-lookup"><span data-stu-id="e5312-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="e5312-136">Il vous suffit d’instancier l’un de ces types avec les paramètres de type nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e5312-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="e5312-137">Dans le cas des algorithmes qui peuvent être rendus génériques, ces délégués peuvent être utilisés en tant que types génériques.</span><span class="sxs-lookup"><span data-stu-id="e5312-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="e5312-138">Cela devrait vous procurer un gain de temps et réduire le nombre de nouveaux types que vous devez créer pour travailler avec des délégués.</span><span class="sxs-lookup"><span data-stu-id="e5312-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="e5312-139">Dans l’article suivant, vous verrez plusieurs schémas d’utilisation courants des délégués.</span><span class="sxs-lookup"><span data-stu-id="e5312-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="e5312-140">Suivant</span><span class="sxs-lookup"><span data-stu-id="e5312-140">Next</span></span>](delegates-patterns.md)

