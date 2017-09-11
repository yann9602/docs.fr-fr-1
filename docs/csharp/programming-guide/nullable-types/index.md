---
title: Types Nullable (Guide de programmation C#)
ms.date: 2017-05-15
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 56e22638457017688ff380f6683b463b47c53a17
ms.contentlocale: fr-fr
ms.lasthandoff: 09/02/2017

---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="5f32b-102">Types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5f32b-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="5f32b-103">Les types Nullable sont des instances du struct <xref:System.Nullable%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5f32b-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=fullName> struct.</span></span> <span data-ttu-id="5f32b-104">Un type Nullable peut représenter la plage correcte de valeurs de son type valeur sous-jacent, plus une valeur `null` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5f32b-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="5f32b-105">Par exemple, un `Nullable<Int32>`, prononcé « Nullable d’Int32 », peut se voir affecter n’importe quelle valeur entre -2147483648 et 2147483647, ou la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="5f32b-106">Un `Nullable<bool>` peut se voir affecter les valeurs [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ou [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="5f32b-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="5f32b-107">La capacité à affecter `null` aux types numériques et booléens est particulièrement utile lorsque l’on travaille avec des bases de données et d’autres types de données qui contiennent des éléments potentiellement sans valeur.</span><span class="sxs-lookup"><span data-stu-id="5f32b-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="5f32b-108">Par exemple, un champ booléen dans une base de données peut stocker la valeur `true` ou `false`, ou être indéfini.</span><span class="sxs-lookup"><span data-stu-id="5f32b-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
<span data-ttu-id="5f32b-109">[!code-cs[Types Nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5f32b-109">[!code-cs[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span></span>  
  
<span data-ttu-id="5f32b-110">Pour plus d’exemples, consultez la page [Utiliser les types Nullable](../../../csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="5f32b-110">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="5f32b-111">Vue d’ensemble des types Nullable</span><span class="sxs-lookup"><span data-stu-id="5f32b-111">Nullable Types Overview</span></span>  
 <span data-ttu-id="5f32b-112">Les types Nullable possèdent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f32b-112">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="5f32b-113">Les types Nullable représentent des variables de type valeur qui peuvent avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-113">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="5f32b-114">Il n’est pas possible de créer un type Nullable à partir d’un type référence.</span><span class="sxs-lookup"><span data-stu-id="5f32b-114">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="5f32b-115">(Les types référence prennent déjà en charge la valeur `null`.)</span><span class="sxs-lookup"><span data-stu-id="5f32b-115">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="5f32b-116">La syntaxe `T?` est la forme abrégée de <xref:System.Nullable%601>, où `T` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="5f32b-116">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="5f32b-117">Les deux formats sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="5f32b-117">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="5f32b-118">Affectez une valeur à un type Nullable, comme vous le feriez pour un type valeur ordinaire, par exemple `int? x = 10;` ou `double? d = 4.108`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-118">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="5f32b-119">Un type Nullable peut également avoir la valeur `null` : `int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="5f32b-119">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="5f32b-120">Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> pour retourner la valeur affectée, ou la valeur par défaut du type sous-jacent si la valeur est `null`, par exemple `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="5f32b-120">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="5f32b-121">Utilisez les propriétés <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> en lecture seule pour rechercher les valeurs null et récupérer la valeur, comme indiqué dans l’exemple suivant : `if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="5f32b-121">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="5f32b-122">La propriété `HasValue` retourne `true` si la variable contient une valeur, ou `false` si elle est `null`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-122">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="5f32b-123">La propriété `Value` retourne une valeur s’il existe une valeur affectée.</span><span class="sxs-lookup"><span data-stu-id="5f32b-123">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="5f32b-124">Sinon, une exception <xref:System.InvalidOperationException?displayProperty=fullName> est levée.</span><span class="sxs-lookup"><span data-stu-id="5f32b-124">Otherwise, a <xref:System.InvalidOperationException?displayProperty=fullName> is thrown.</span></span>  
  
    -   <span data-ttu-id="5f32b-125">La valeur par défaut de `HasValue` est `false`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-125">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="5f32b-126">La propriété `Value` n’a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f32b-126">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="5f32b-127">Vous pouvez également utiliser les opérateurs `==` et `!=` avec un type Nullable, comme le montre l’exemple suivant : `if (x != null) y = x;`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-127">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="5f32b-128">Utilisez l’opérateur `??` pour affecter une valeur par défaut qui sera appliquée lorsqu’un type Nullable dont la valeur actuelle est `null` sera affecté à un type non Nullable, par exemple `int? x = null; int y = x ?? -1;`.</span><span class="sxs-lookup"><span data-stu-id="5f32b-128">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="5f32b-129">Les types Nullable imbriqués ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="5f32b-129">Nested nullable types are not allowed.</span></span> <span data-ttu-id="5f32b-130">Il n’est pas possible de compiler la ligne suivante : `Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="5f32b-130">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5f32b-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="5f32b-131">Related Sections</span></span>  
 <span data-ttu-id="5f32b-132">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="5f32b-132">For more information:</span></span>  
  
-   [<span data-ttu-id="5f32b-133">Utilisation de types Nullable</span><span class="sxs-lookup"><span data-stu-id="5f32b-133">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="5f32b-134">Boxing des types Nullable</span><span class="sxs-lookup"><span data-stu-id="5f32b-134">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="5f32b-135">?? Opérateur</span><span class="sxs-lookup"><span data-stu-id="5f32b-135">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5f32b-136">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5f32b-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f32b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f32b-137">See Also</span></span>  
 <span data-ttu-id="5f32b-138"><xref:System.Nullable></span><span class="sxs-lookup"><span data-stu-id="5f32b-138"><xref:System.Nullable></span></span>   
 <span data-ttu-id="5f32b-139">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5f32b-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5f32b-140">[C#](../../../csharp/index.md) </span><span class="sxs-lookup"><span data-stu-id="5f32b-140">[C#](../../../csharp/index.md) </span></span>  
 <span data-ttu-id="5f32b-141">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5f32b-141">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="5f32b-142">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="5f32b-142">What exactly does 'lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112382)

