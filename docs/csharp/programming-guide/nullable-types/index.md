---
title: Types Nullable (Guide de programmation C#)
ms.date: 05/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: "44"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: af7de7ea0be5368371e4bb174f6313e98f93ac4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="1ee24-102">Types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1ee24-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="1ee24-103">Les types Nullable sont des instances du struct <xref:System.Nullable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ee24-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="1ee24-104">Un type Nullable peut représenter la plage correcte de valeurs de son type valeur sous-jacent, plus une valeur `null` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1ee24-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="1ee24-105">Par exemple, un `Nullable<Int32>`, prononcé « Nullable d’Int32 », peut se voir affecter n’importe quelle valeur entre -2147483648 et 2147483647, ou la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="1ee24-106">Un `Nullable<bool>` peut se voir affecter les valeurs [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ou [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="1ee24-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="1ee24-107">La capacité à affecter `null` aux types numériques et booléens est particulièrement utile lorsque l’on travaille avec des bases de données et d’autres types de données qui contiennent des éléments potentiellement sans valeur.</span><span class="sxs-lookup"><span data-stu-id="1ee24-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="1ee24-108">Par exemple, un champ booléen dans une base de données peut stocker la valeur `true` ou `false`, ou être indéfini.</span><span class="sxs-lookup"><span data-stu-id="1ee24-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="1ee24-109">Pour plus d’exemples, consultez la page [Utiliser les types Nullable](../../../csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="1ee24-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="1ee24-110">Vue d’ensemble des types Nullable</span><span class="sxs-lookup"><span data-stu-id="1ee24-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="1ee24-111">Les types Nullable possèdent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="1ee24-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="1ee24-112">Les types Nullable représentent des variables de type valeur qui peuvent avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="1ee24-113">Il n’est pas possible de créer un type Nullable à partir d’un type référence.</span><span class="sxs-lookup"><span data-stu-id="1ee24-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="1ee24-114">(Les types référence prennent déjà en charge la valeur `null`.)</span><span class="sxs-lookup"><span data-stu-id="1ee24-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="1ee24-115">La syntaxe `T?` est la forme abrégée de <xref:System.Nullable%601>, où `T` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="1ee24-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="1ee24-116">Les deux formats sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="1ee24-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="1ee24-117">Affectez une valeur à un type Nullable, comme vous le feriez pour un type valeur ordinaire, par exemple `int? x = 10;` ou `double? d = 4.108`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="1ee24-118">Un type Nullable peut également avoir la valeur `null` : `int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="1ee24-118">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="1ee24-119">Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> pour retourner la valeur affectée, ou la valeur par défaut du type sous-jacent si la valeur est `null`, par exemple `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="1ee24-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="1ee24-120">Utilisez les propriétés <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> en lecture seule pour rechercher les valeurs null et récupérer la valeur, comme indiqué dans l’exemple suivant : `if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="1ee24-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="1ee24-121">La propriété `HasValue` retourne `true` si la variable contient une valeur, ou `false` si elle est `null`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="1ee24-122">La propriété `Value` retourne une valeur s’il existe une valeur affectée.</span><span class="sxs-lookup"><span data-stu-id="1ee24-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="1ee24-123">Sinon, une exception <xref:System.InvalidOperationException?displayProperty=nameWithType> est levée.</span><span class="sxs-lookup"><span data-stu-id="1ee24-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="1ee24-124">La valeur par défaut de `HasValue` est `false`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="1ee24-125">La propriété `Value` n’a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ee24-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="1ee24-126">Vous pouvez également utiliser les opérateurs `==` et `!=` avec un type Nullable, comme le montre l’exemple suivant : `if (x != null) y = x;`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="1ee24-127">Utilisez l’opérateur `??` pour affecter une valeur par défaut qui sera appliquée lorsqu’un type Nullable dont la valeur actuelle est `null` sera affecté à un type non Nullable, par exemple `int? x = null; int y = x ?? -1;`.</span><span class="sxs-lookup"><span data-stu-id="1ee24-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="1ee24-128">Les types Nullable imbriqués ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="1ee24-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="1ee24-129">Il n’est pas possible de compiler la ligne suivante : `Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="1ee24-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ee24-130">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="1ee24-130">Related Sections</span></span>  
 <span data-ttu-id="1ee24-131">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="1ee24-131">For more information:</span></span>  
  
-   [<span data-ttu-id="1ee24-132">Utilisation de types Nullable</span><span class="sxs-lookup"><span data-stu-id="1ee24-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="1ee24-133">Boxing des types Nullable</span><span class="sxs-lookup"><span data-stu-id="1ee24-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="1ee24-134">?? Opérateur</span><span class="sxs-lookup"><span data-stu-id="1ee24-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1ee24-135">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1ee24-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ee24-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee24-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="1ee24-137">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1ee24-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1ee24-138">C#</span><span class="sxs-lookup"><span data-stu-id="1ee24-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="1ee24-139">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1ee24-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1ee24-140">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="1ee24-140">What exactly does 'lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112382)
