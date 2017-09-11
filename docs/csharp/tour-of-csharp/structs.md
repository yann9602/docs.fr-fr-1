---
title: "Structs C# - Visite guidée du langage C#"
description: "Apprendre les bases des types valeur de C#, appelés structs"
keywords: .NET, C#, struct, type valeur
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="structs"></a><span data-ttu-id="85852-104">Structs</span><span class="sxs-lookup"><span data-stu-id="85852-104">Structs</span></span>

<span data-ttu-id="85852-105">Comme les classes, les ***structs*** sont des structures de données qui peuvent contenir des membres de données et des fonctions membres. Mais contrairement aux classes, les structures sont des types valeur et ne nécessitent pas d’allocation de tas.</span><span class="sxs-lookup"><span data-stu-id="85852-105">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="85852-106">Une variable de type struct stocke directement les données de la structure, alors qu’une variable de type class stocke une référence à un objet alloué dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="85852-106">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="85852-107">Les types struct ne prennent pas en charge l’héritage spécifié par l’utilisateur, et tous les types struct héritent implicitement du type <xref:System.ValueType>, qui à son tour hérite implicitement de `object`.</span><span class="sxs-lookup"><span data-stu-id="85852-107">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="85852-108">Les structures sont particulièrement utiles pour les petites structures de données qui ont une sémantique par rapport à leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="85852-108">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="85852-109">Les nombres complexes, les points dans un système de coordonnées ou les paires clé-valeur dans un dictionnaire sont de bons exemples de structures.</span><span class="sxs-lookup"><span data-stu-id="85852-109">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="85852-110">L’utilisation de structures plutôt que de classes pour les petites structures de données peut faire une grande différence dans le nombre d’allocations de mémoire effectuées par une application.</span><span class="sxs-lookup"><span data-stu-id="85852-110">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="85852-111">Par exemple, le programme suivant crée et initialise un tableau de 100 points.</span><span class="sxs-lookup"><span data-stu-id="85852-111">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="85852-112">Avec `Point` implémenté en tant que classe, 101 objets séparés sont instanciés : un pour le tableau et un pour chacun des 100 éléments.</span><span class="sxs-lookup"><span data-stu-id="85852-112">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

<span data-ttu-id="85852-113">[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]</span><span class="sxs-lookup"><span data-stu-id="85852-113">[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]</span></span>

<span data-ttu-id="85852-114">Une alternative consiste à faire du Point une struct.</span><span class="sxs-lookup"><span data-stu-id="85852-114">An alternative is to make Point a struct.</span></span>

<span data-ttu-id="85852-115">[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]</span><span class="sxs-lookup"><span data-stu-id="85852-115">[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]</span></span>

<span data-ttu-id="85852-116">Maintenant, un seul objet est instancié, celui du tableau, et les instances `Point` sont stockées à la suite dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="85852-116">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="85852-117">Vous appelez les constructeurs de struct avec l’opérateur new, mais cela n’implique pas que la mémoire est allouée.</span><span class="sxs-lookup"><span data-stu-id="85852-117">Struct constructors are invoked with the new operator, but that does not imply that memory is being allocated.</span></span> <span data-ttu-id="85852-118">Au lieu d’allouer dynamiquement un objet et de renvoyer une référence à cet objet, un constructeur de struct retourne simplement la valeur du struct (généralement dans un emplacement temporaire sur la pile), et cette valeur est ensuite copiée si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="85852-118">Instead of dynamically allocating an object and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="85852-119">Avec les classes, deux variables peuvent faire référence au même objet et, par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="85852-119">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="85852-120">Avec les structs, les variables disposent chacune de leur propre copie des données, et il n’est pas possible pour les opérations sur une d’affecter les autres.</span><span class="sxs-lookup"><span data-stu-id="85852-120">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="85852-121">Par exemple, la sortie générée par le code suivant varie selon que Point est une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="85852-121">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

<span data-ttu-id="85852-122">[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]</span><span class="sxs-lookup"><span data-stu-id="85852-122">[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]</span></span>

<span data-ttu-id="85852-123">Si `Point` est une classe, la sortie est de 20, car a et b font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="85852-123">If `Point` is a class, the output is 20 because a and b reference the same object.</span></span> <span data-ttu-id="85852-124">Si Point est un struct, le résultat est 10, car l’attribution de `a` à `b` crée une copie de la valeur, et cette copie n’est pas affectée par l’assignation consécutive de `a.x`.</span><span class="sxs-lookup"><span data-stu-id="85852-124">If Point is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="85852-125">L’exemple précédent illustre deux des limitations des structs.</span><span class="sxs-lookup"><span data-stu-id="85852-125">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="85852-126">Tout d’abord, la copie d’un struct entier est généralement moins efficace que la copie d’une référence d’objet, aussi le passage de paramètres d’affectation et de valeur peut être plus coûteux avec les structures qu’avec les types référence.</span><span class="sxs-lookup"><span data-stu-id="85852-126">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="85852-127">Ensuite, à l’exception des paramètres `ref` et `out`, il n’est pas possible de créer des références aux structures, ce qui rend leur utilisation impossible dans un certain nombre de situations.</span><span class="sxs-lookup"><span data-stu-id="85852-127">Second, except for `ref` and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="85852-128">[Précédent](classes-and-objects.md)
[Suivant](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="85852-128">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>

