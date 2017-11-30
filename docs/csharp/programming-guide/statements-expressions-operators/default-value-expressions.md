---
title: "Expressions de valeur par défaut (Guide de programmation C#)"
description: "Les expressions de valeur par défaut produisent la valeur par défaut des types référence et des types valeur"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="233d9-103">Expressions de valeur par défaut (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="233d9-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="233d9-104">Une expression de valeur par défaut produit la valeur par défaut d’un type.</span><span class="sxs-lookup"><span data-stu-id="233d9-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="233d9-105">Les expressions de valeur par défaut sont particulièrement utiles dans les méthodes et classes génériques.</span><span class="sxs-lookup"><span data-stu-id="233d9-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="233d9-106">Le problème qui se pose avec l’utilisation des génériques est de savoir comment assigner une valeur par défaut à un type paramétrable `T` quand vous ne connaissez pas les éléments suivants à l’avance :</span><span class="sxs-lookup"><span data-stu-id="233d9-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="233d9-107">Si `T` est un type référence ou un type valeur.</span><span class="sxs-lookup"><span data-stu-id="233d9-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="233d9-108">Si `T` est un type valeur, s’il s’agit d’une valeur numérique ou d’un struct défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="233d9-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="233d9-109">Avec une variable `t` d’un type paramétré `T`, l’instruction `t = null` est valide uniquement si `T` est un type référence.</span><span class="sxs-lookup"><span data-stu-id="233d9-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="233d9-110">L’affectation de `t = 0` fonctionne uniquement pour les types valeur numériques mais pas pour les structs.</span><span class="sxs-lookup"><span data-stu-id="233d9-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="233d9-111">La solution consiste à utiliser une expression de valeur par défaut, qui retourne `null` pour les types référence (types de classes et types interface) et zéro pour les types valeur numériques.</span><span class="sxs-lookup"><span data-stu-id="233d9-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="233d9-112">Pour des structs définis par l’utilisateur, elle retourne le struct initialisé sur le modèle de bit zéro qui produit 0 ou `null` pour chaque membre, selon que ce membre est un type valeur ou référence.</span><span class="sxs-lookup"><span data-stu-id="233d9-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="233d9-113">Pour les types valeur Nullable, `default` retourne <xref:System.Nullable%601?displayProperty=nameWithType>, initialisé comme n’importe quel struct.</span><span class="sxs-lookup"><span data-stu-id="233d9-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=nameWithType>, which is initialized like any struct.</span></span>

<span data-ttu-id="233d9-114">L’expression `default(T)` n’est pas limitée aux classes et aux méthodes génériques.</span><span class="sxs-lookup"><span data-stu-id="233d9-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="233d9-115">Vous pouvez utiliser les expressions de valeur par défaut avec n’importe quel type managé.</span><span class="sxs-lookup"><span data-stu-id="233d9-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="233d9-116">Toutes ces expressions sont valides :</span><span class="sxs-lookup"><span data-stu-id="233d9-116">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="233d9-117">L’exemple suivant de la classe `GenericList<T>` montre comment utiliser l’opérateur `default(T)` dans une classe générique.</span><span class="sxs-lookup"><span data-stu-id="233d9-117">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="233d9-118">Pour plus d’informations, consultez [Introduction aux génériques](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="233d9-118">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="233d9-119">Littéral par défaut et inférence de type</span><span class="sxs-lookup"><span data-stu-id="233d9-119">default literal and type inference</span></span>

<span data-ttu-id="233d9-120">À partir de C# 7.1, vous pouvez utiliser les littéraux `default` pour les expressions de valeur par défaut quand le compilateur peut déduire le type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="233d9-120">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="233d9-121">Le littéral `default` génère la même valeur que l’équivalent `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="233d9-121">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="233d9-122">Vous pouvez ainsi alléger votre code en réduisant la redondance de déclarer un type plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="233d9-122">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="233d9-123">Vous pouvez utiliser le littéral `default` dans l’un des emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="233d9-123">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="233d9-124">initialiseur de variable</span><span class="sxs-lookup"><span data-stu-id="233d9-124">variable initializer</span></span>
- <span data-ttu-id="233d9-125">assignation de variable</span><span class="sxs-lookup"><span data-stu-id="233d9-125">variable assignment</span></span>
- <span data-ttu-id="233d9-126">déclaration de la valeur par défaut d’un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="233d9-126">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="233d9-127">valeur pour un argument d’appel de méthode</span><span class="sxs-lookup"><span data-stu-id="233d9-127">providing the value for a method call argument</span></span>
- <span data-ttu-id="233d9-128">instruction return (ou expression dans un membre expression-bodied)</span><span class="sxs-lookup"><span data-stu-id="233d9-128">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="233d9-129">L’exemple suivant illustre plusieurs utilisations du littéral `default` dans une expression de valeur par défaut :</span><span class="sxs-lookup"><span data-stu-id="233d9-129">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="233d9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="233d9-130">See also</span></span>

 <span data-ttu-id="233d9-131"><xref:System.Collections.Generic>[Guide de programmation c#](../index.md)</span><span class="sxs-lookup"><span data-stu-id="233d9-131"><xref:System.Collections.Generic> [C# Programming Guide](../index.md)</span></span>  
 [<span data-ttu-id="233d9-132">Génériques</span><span class="sxs-lookup"><span data-stu-id="233d9-132">Generics</span></span>](../generics/index.md)  
 [<span data-ttu-id="233d9-133">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="233d9-133">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="233d9-134">Génériques</span><span class="sxs-lookup"><span data-stu-id="233d9-134">Generics</span></span>](~/docs/standard/generics/index.md)  
