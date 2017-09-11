---
title: "Expressions de valeur par défaut (Guide de programmation C#)"
description: "Les expressions de valeur par défaut produisent la valeur par défaut des types référence et des types valeur"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="e17ff-103">Expressions de valeur par défaut (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e17ff-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="e17ff-104">Une expression de valeur par défaut produit la valeur par défaut d’un type.</span><span class="sxs-lookup"><span data-stu-id="e17ff-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="e17ff-105">Les expressions de valeur par défaut sont particulièrement utiles dans les méthodes et classes génériques.</span><span class="sxs-lookup"><span data-stu-id="e17ff-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="e17ff-106">Le problème qui se pose avec l’utilisation des génériques est de savoir comment assigner une valeur par défaut à un type paramétrable `T` quand vous ne connaissez pas les éléments suivants à l’avance :</span><span class="sxs-lookup"><span data-stu-id="e17ff-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="e17ff-107">Si `T` est un type référence ou un type valeur.</span><span class="sxs-lookup"><span data-stu-id="e17ff-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="e17ff-108">Si `T` est un type valeur, s’il s’agit d’une valeur numérique ou d’un struct défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e17ff-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="e17ff-109">Avec une variable `t` d’un type paramétré `T`, l’instruction `t = null` est valide uniquement si `T` est un type référence.</span><span class="sxs-lookup"><span data-stu-id="e17ff-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="e17ff-110">L’affectation de `t = 0` fonctionne uniquement pour les types valeur numériques mais pas pour les structs.</span><span class="sxs-lookup"><span data-stu-id="e17ff-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="e17ff-111">La solution consiste à utiliser une expression de valeur par défaut, qui retourne `null` pour les types référence (types de classes et types interface) et zéro pour les types valeur numériques.</span><span class="sxs-lookup"><span data-stu-id="e17ff-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="e17ff-112">Pour des structs définis par l’utilisateur, elle retourne le struct initialisé sur le modèle de bit zéro qui produit 0 ou `null` pour chaque membre, selon que ce membre est un type valeur ou référence.</span><span class="sxs-lookup"><span data-stu-id="e17ff-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="e17ff-113">Pour les types valeur Nullable, `default` retourne <xref:System.Nullable%601?displayProperty=fullName>, initialisé comme n’importe quel struct.</span><span class="sxs-lookup"><span data-stu-id="e17ff-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=fullName>, which is initialized like any struct.</span></span>

<span data-ttu-id="e17ff-114">L’expression `default(T)` n’est pas limitée aux classes et aux méthodes génériques.</span><span class="sxs-lookup"><span data-stu-id="e17ff-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="e17ff-115">Vous pouvez utiliser les expressions de valeur par défaut avec n’importe quel type managé.</span><span class="sxs-lookup"><span data-stu-id="e17ff-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="e17ff-116">Toutes ces expressions sont valides :</span><span class="sxs-lookup"><span data-stu-id="e17ff-116">Any of these expressions are valid:</span></span>

 <span data-ttu-id="e17ff-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span><span class="sxs-lookup"><span data-stu-id="e17ff-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span></span>

 <span data-ttu-id="e17ff-118">L’exemple suivant de la classe `GenericList<T>` montre comment utiliser l’opérateur `default(T)` dans une classe générique.</span><span class="sxs-lookup"><span data-stu-id="e17ff-118">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="e17ff-119">Pour plus d’informations, consultez [Introduction aux génériques](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="e17ff-119">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 <span data-ttu-id="e17ff-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span><span class="sxs-lookup"><span data-stu-id="e17ff-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span></span>

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="e17ff-121">Littéral par défaut et inférence de type</span><span class="sxs-lookup"><span data-stu-id="e17ff-121">default literal and type inference</span></span>

<span data-ttu-id="e17ff-122">À partir de C# 7.1, vous pouvez utiliser les littéraux `default` pour les expressions de valeur par défaut quand le compilateur peut déduire le type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="e17ff-122">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="e17ff-123">Le littéral `default` génère la même valeur que l’équivalent `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="e17ff-123">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="e17ff-124">Vous pouvez ainsi alléger votre code en réduisant la redondance de déclarer un type plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e17ff-124">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="e17ff-125">Vous pouvez utiliser le littéral `default` dans l’un des emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="e17ff-125">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="e17ff-126">initialiseur de variable</span><span class="sxs-lookup"><span data-stu-id="e17ff-126">variable initializer</span></span>
- <span data-ttu-id="e17ff-127">assignation de variable</span><span class="sxs-lookup"><span data-stu-id="e17ff-127">variable assignment</span></span>
- <span data-ttu-id="e17ff-128">déclaration de la valeur par défaut d’un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="e17ff-128">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="e17ff-129">valeur pour un argument d’appel de méthode</span><span class="sxs-lookup"><span data-stu-id="e17ff-129">providing the value for a method call argument</span></span>
- <span data-ttu-id="e17ff-130">instruction return (ou expression dans un membre expression-bodied)</span><span class="sxs-lookup"><span data-stu-id="e17ff-130">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="e17ff-131">L’exemple suivant illustre plusieurs utilisations du littéral `default` dans une expression de valeur par défaut :</span><span class="sxs-lookup"><span data-stu-id="e17ff-131">The following example shows many usages of the `default` literal in a default value expression:</span></span>

<span data-ttu-id="e17ff-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span><span class="sxs-lookup"><span data-stu-id="e17ff-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e17ff-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e17ff-133">See also</span></span>

 <span data-ttu-id="e17ff-134"><xref:System.Collections.Generic> [Guide de programmation C#](../index.md) </span><span class="sxs-lookup"><span data-stu-id="e17ff-134"><xref:System.Collections.Generic> [C# Programming Guide](../index.md) </span></span>  
 <span data-ttu-id="e17ff-135">[Génériques](../generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="e17ff-135">[Generics](../generics/index.md) </span></span>  
 <span data-ttu-id="e17ff-136">[Méthodes génériques](../generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="e17ff-136">[Generic Methods](../generics/generic-methods.md) </span></span>  
 [<span data-ttu-id="e17ff-137">Génériques</span><span class="sxs-lookup"><span data-stu-id="e17ff-137">Generics</span></span>](~/docs/standard/generics/index.md)   

