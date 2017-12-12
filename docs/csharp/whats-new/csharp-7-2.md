---
title: "Nouveautés de C# 7.2"
description: "Vue d’ensemble des nouvelles fonctionnalités de C# 7.2."
keywords: conception de langage C#, 7.2, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="d34f2-104">Nouveautés de C# 7.2</span><span class="sxs-lookup"><span data-stu-id="d34f2-104">What's new in C# 7.2</span></span>

<span data-ttu-id="d34f2-105">C# 7.2 est une autre version intermédiaire qui ajoute un certain nombre de fonctionnalités utiles.</span><span class="sxs-lookup"><span data-stu-id="d34f2-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="d34f2-106">Cette version a notamment pour but d’utiliser plus efficacement les types valeur en évitant des copies ou allocations inutiles.</span><span class="sxs-lookup"><span data-stu-id="d34f2-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="d34f2-107">Les fonctionnalités restantes sont des fonctionnalités réduites, mais pratiques.</span><span class="sxs-lookup"><span data-stu-id="d34f2-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="d34f2-108">C# 7.2 utilise l’élément de configuration de [sélection de la version du langage](csharp-7-1.md#language-version-selection) pour sélectionner la version du langage du compilateur.</span><span class="sxs-lookup"><span data-stu-id="d34f2-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="d34f2-109">Les nouvelles fonctionnalités de langage de cette version sont :</span><span class="sxs-lookup"><span data-stu-id="d34f2-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="d34f2-110">Sémantique de référence avec les types valeur</span><span class="sxs-lookup"><span data-stu-id="d34f2-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="d34f2-111">Une combinaison des améliorations de la syntaxe qui permettent d’utiliser les types valeur avec la sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="d34f2-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="d34f2-112">Arguments nommés non placés en position de fin</span><span class="sxs-lookup"><span data-stu-id="d34f2-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="d34f2-113">Les arguments nommés peuvent être suivis par des arguments de position.</span><span class="sxs-lookup"><span data-stu-id="d34f2-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="d34f2-114">Traits de soulignement de début dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="d34f2-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="d34f2-115">Les littéraux numériques peuvent maintenant comporter des traits de soulignement de début avant tout chiffre affiché.</span><span class="sxs-lookup"><span data-stu-id="d34f2-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="d34f2-116">Modificateur d’accès `private protected`</span><span class="sxs-lookup"><span data-stu-id="d34f2-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="d34f2-117">Le modificateur d’accès `private protected` active l’accès pour les classes dérivées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="d34f2-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="d34f2-118">Sémantique de référence avec les types valeur</span><span class="sxs-lookup"><span data-stu-id="d34f2-118">Reference semantics with value types</span></span>

<span data-ttu-id="d34f2-119">Les fonctionnalités de langage introduites dans 7.2 vous permettent de travailler avec les types valeur tout en utilisant la sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="d34f2-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="d34f2-120">Elles sont conçues pour améliorer les performances en réduisant la copie des types valeur sans impliquer les allocations de mémoire associées à l’utilisation des types référence.</span><span class="sxs-lookup"><span data-stu-id="d34f2-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="d34f2-121">Les fonctionnalités incluent :</span><span class="sxs-lookup"><span data-stu-id="d34f2-121">The features include:</span></span>

 - <span data-ttu-id="d34f2-122">Le modificateur `in` sur les paramètres pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="d34f2-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="d34f2-123">Le modificateur `ref readonly` sur les retours de méthode pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="d34f2-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="d34f2-124">La déclaration `readonly struct` pour indiquer qu’un struct est immuable et doit être passé comme un paramètre `in` aux méthodes de ses membres.</span><span class="sxs-lookup"><span data-stu-id="d34f2-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="d34f2-125">La déclaration `ref struct` pour indiquer qu’un type struct accède directement à la mémoire managée et doit toujours être alloué par la pile.</span><span class="sxs-lookup"><span data-stu-id="d34f2-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="d34f2-126">Vous pouvez en savoir plus sur toutes ces modifications dans [Sémantique de référence avec les types valeur](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="d34f2-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="d34f2-127">Arguments nommés non placés en position de fin</span><span class="sxs-lookup"><span data-stu-id="d34f2-127">Non-trailing named arguments</span></span>

<span data-ttu-id="d34f2-128">Les appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments de position quand ces arguments nommés se trouvent dans les positions appropriées.</span><span class="sxs-lookup"><span data-stu-id="d34f2-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="d34f2-129">Pour plus d’informations, consultez [Arguments nommés et facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d34f2-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="d34f2-130">Traits de soulignement de début dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="d34f2-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="d34f2-131">L’implémentation de la prise en charge des séparateurs numériques dans C# 7.0 n’autorisait pas `_` comme premier caractère de la valeur littérale.</span><span class="sxs-lookup"><span data-stu-id="d34f2-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="d34f2-132">Les littéraux numériques binaires et hexadécimaux peuvent maintenant commencer par un caractère `_`.</span><span class="sxs-lookup"><span data-stu-id="d34f2-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="d34f2-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d34f2-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="d34f2-134">Enfin, un nouveau modificateur d’accès composé, `private protected`, indique qu’un membre peut être accessible par la classe conteneur ou les classes dérivées qui sont déclarées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="d34f2-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="d34f2-135">Alors que `protected internal` autorise l’accès par des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclarés dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="d34f2-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="d34f2-136">Pour plus d’informations, consultez [Modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans Informations de référence sur le langage.</span><span class="sxs-lookup"><span data-stu-id="d34f2-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
