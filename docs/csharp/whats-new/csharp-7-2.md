---
title: "Quelles sont les nouveautés dans c# 7.2"
description: "Vue d’ensemble des nouvelles fonctionnalités de c# 7.2."
keywords: Conception du langage c#, 7.2, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="79808-104">Quelles sont les nouveautés dans c# 7.2</span><span class="sxs-lookup"><span data-stu-id="79808-104">What's new in C# 7.2</span></span>

<span data-ttu-id="79808-105">7.2 c# est un autre point de mise à jour d’ajoute un nombre de fonctionnalités utiles.</span><span class="sxs-lookup"><span data-stu-id="79808-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="79808-106">Un thème pour cette version fonctionne plus efficacement avec les types valeur en évitant de copies non nécessaires ou des allocations.</span><span class="sxs-lookup"><span data-stu-id="79808-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="79808-107">Les fonctionnalités restantes sont petites, agréable pour lesquels des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="79808-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="79808-108">7.2 c# utilise le [sélection de la version linguistique](csharp-7-1.md#language-version-selection) élément de configuration pour sélectionner la version de langue du compilateur.</span><span class="sxs-lookup"><span data-stu-id="79808-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="79808-109">Les nouvelles fonctionnalités de langage dans cette version sont :</span><span class="sxs-lookup"><span data-stu-id="79808-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="79808-110">Sémantique de référence avec les types valeur</span><span class="sxs-lookup"><span data-stu-id="79808-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="79808-111">Une combinaison des améliorations de la syntaxe qui permettent de travailler avec les types de valeur à l’aide de la sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="79808-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="79808-112">Arguments nommé non-fin</span><span class="sxs-lookup"><span data-stu-id="79808-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="79808-113">Arguments nommés peuvent être suivis par des arguments de position.</span><span class="sxs-lookup"><span data-stu-id="79808-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="79808-114">Début des traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="79808-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="79808-115">Littéraux numériques peuvent avoir maintenant au début des traits de soulignement avant tous les chiffres imprimés.</span><span class="sxs-lookup"><span data-stu-id="79808-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="79808-116">`private protected`modificateur d’accès</span><span class="sxs-lookup"><span data-stu-id="79808-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="79808-117">Le `private protected` modificateur d’accès permet l’accès pour les classes dérivées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="79808-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="79808-118">Sémantique de référence avec les types valeur</span><span class="sxs-lookup"><span data-stu-id="79808-118">Reference semantics with value types</span></span>

<span data-ttu-id="79808-119">Les fonctionnalités de langage introduites dans 7.2 vous permettent de travailler avec les types valeur lors de l’utilisation d’une sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="79808-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="79808-120">Elles sont conçues pour améliorer les performances en réduisant les types valeur copie sans avoir aux allocations de mémoire associées à l’aide des types référence.</span><span class="sxs-lookup"><span data-stu-id="79808-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="79808-121">Les fonctionnalités incluent :</span><span class="sxs-lookup"><span data-stu-id="79808-121">The features include:</span></span>

 - <span data-ttu-id="79808-122">Le `in` modificateur de paramètres, pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="79808-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="79808-123">Le `ref readonly` modificateur sur la méthode retourne, pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures à cet objet.</span><span class="sxs-lookup"><span data-stu-id="79808-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="79808-124">Le `readonly struct` déclaration, pour indiquer qu’un struct est immuable et doit être passé comme un `in` paramètre aux méthodes de ses membres.</span><span class="sxs-lookup"><span data-stu-id="79808-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="79808-125">Le `ref struct` déclaration, pour indiquer qu’un type struct accède directement aux mémoire managée et doit toujours être pile allouée.</span><span class="sxs-lookup"><span data-stu-id="79808-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="79808-126">Vous pouvez en savoir plus sur ces modifications dans [à l’aide de types valeur avec la sémantique de référence](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="79808-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="79808-127">Arguments nommé non-fin</span><span class="sxs-lookup"><span data-stu-id="79808-127">Non-trailing named arguments</span></span>

<span data-ttu-id="79808-128">Appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments positionnels lorsque les arguments nommés se trouvent dans les positions appropriées.</span><span class="sxs-lookup"><span data-stu-id="79808-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="79808-129">Pour plus d’informations, consultez [arguments nommés et optionnels](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="79808-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="79808-130">Début des traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="79808-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="79808-131">L’implémentation de la prise en charge pour les séparateurs de chiffres dans c# 7.0 n’a pas autorisé le `_` pour être le premier caractère de la valeur littérale.</span><span class="sxs-lookup"><span data-stu-id="79808-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="79808-132">Les littéraux numériques binaires et hex peuvent maintenant commencer par une `_`.</span><span class="sxs-lookup"><span data-stu-id="79808-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="79808-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="79808-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="79808-134">Enfin, un modificateur d’accès composés nouvelle : `private protected` indique qu’un membre peut être accessible par les classes dérivées qui sont déclarés dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="79808-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="79808-135">Alors que `protected internal` autorise l’accès à des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclaré dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="79808-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="79808-136">Pour plus d’informations, consultez [les modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans la référence du langage.</span><span class="sxs-lookup"><span data-stu-id="79808-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
