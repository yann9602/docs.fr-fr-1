---
title: Utilisation de types Nullable (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="448d5-102">Utilisation de types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="448d5-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="448d5-103">Les types Nullable peuvent représenter toutes les valeurs d’un type sous-jacent ainsi qu’une autre valeur [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="448d5-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="448d5-104">Les types Nullable sont déclarés de l’une des deux façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="448d5-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="448d5-105">ou</span><span class="sxs-lookup"><span data-stu-id="448d5-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="448d5-106">`T` est le type sous-jacent du type Nullable.</span><span class="sxs-lookup"><span data-stu-id="448d5-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="448d5-107">`T` peut être n’importe quel type valeur, notamment `struct` ; il ne peut pas être un type référence.</span><span class="sxs-lookup"><span data-stu-id="448d5-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="448d5-108">Voici un exemple d’utilisation de type Nullable. Prenons une variable booléenne ordinaire. Elle peut avoir deux valeurs : true et false.</span><span class="sxs-lookup"><span data-stu-id="448d5-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="448d5-109">Il n’existe aucune valeur qui signifie « indéfini ».</span><span class="sxs-lookup"><span data-stu-id="448d5-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="448d5-110">Dans de nombreuses applications de programmation, notamment dans les interactions de base de données, les variables peuvent se produire dans un état indéfini.</span><span class="sxs-lookup"><span data-stu-id="448d5-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="448d5-111">Par exemple, un champ dans une base de données peut contenir les valeurs true ou false, mais peut aussi ne contenir aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="448d5-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="448d5-112">De même, les types référence peuvent être définis sur `null` pour indiquer qu’ils ne sont pas initialisés.</span><span class="sxs-lookup"><span data-stu-id="448d5-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="448d5-113">Cette disparité peut surcharger le travail de programmation, avec des variables supplémentaires pour stocker les informations d’état, l’utilisation de valeurs spéciales et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="448d5-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="448d5-114">Le modificateur de type Nullable permet à C# de créer des variables de type valeur qui indiquent une valeur indéfinie.</span><span class="sxs-lookup"><span data-stu-id="448d5-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="448d5-115">Exemples de types Nullable</span><span class="sxs-lookup"><span data-stu-id="448d5-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="448d5-116">Tout type valeur peut être utilisé comme base d’un type Nullable.</span><span class="sxs-lookup"><span data-stu-id="448d5-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="448d5-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="448d5-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="448d5-118">Membres de types Nullable</span><span class="sxs-lookup"><span data-stu-id="448d5-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="448d5-119">Chaque instance d’un type Nullable a deux propriétés publiques en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="448d5-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="448d5-120">`HasValue` est de type `bool`.</span><span class="sxs-lookup"><span data-stu-id="448d5-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="448d5-121">Elle est définie sur `true` quand la variable contient une valeur non-null.</span><span class="sxs-lookup"><span data-stu-id="448d5-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="448d5-122">`Value` est du même type que le type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="448d5-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="448d5-123">Si `HasValue` est `true`, `Value` contient une valeur significative.</span><span class="sxs-lookup"><span data-stu-id="448d5-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="448d5-124">Si `HasValue` est `false`, l’accès à `Value` lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="448d5-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="448d5-125">Dans cet exemple, le membre `HasValue` est utilisé pour tester si la variable contient une valeur avant d’essayer de l’afficher.</span><span class="sxs-lookup"><span data-stu-id="448d5-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="448d5-126">Vous pouvez aussi tester une valeur comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="448d5-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="448d5-127">Conversions explicites</span><span class="sxs-lookup"><span data-stu-id="448d5-127">Explicit Conversions</span></span>  
 <span data-ttu-id="448d5-128">Un type Nullable peut être casté en type normal explicitement par un cast ou à l’aide de la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="448d5-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="448d5-129">Exemple :</span><span class="sxs-lookup"><span data-stu-id="448d5-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="448d5-130">Si une conversion définie par l’utilisateur est définie entre deux types de données, la même conversion peut également être utilisée avec les versions Nullable de ces types de données.</span><span class="sxs-lookup"><span data-stu-id="448d5-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="448d5-131">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="448d5-131">Implicit Conversions</span></span>  
 <span data-ttu-id="448d5-132">Une variable de type Nullable peut être définie sur null avec le mot clé `null`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="448d5-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="448d5-133">La conversion d’un type ordinaire en type Nullable est implicite.</span><span class="sxs-lookup"><span data-stu-id="448d5-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="448d5-134">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="448d5-134">Operators</span></span>  
 <span data-ttu-id="448d5-135">Les opérateurs unaire et binaire prédéfinis et tous les opérateurs définis par l’utilisateur existant pour les types valeur peuvent également être utilisés par les types Nullable.</span><span class="sxs-lookup"><span data-stu-id="448d5-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="448d5-136">Ces opérateurs produisent une valeur null si les opérandes sont null ; sinon, l’opérateur utilise la valeur contenue pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="448d5-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="448d5-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="448d5-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="448d5-138">Quand vous effectuez des comparaisons avec des types Nullable, si la valeur de l’un des types Nullable est null et que l’autre ne l’est pas, toutes les comparaisons donnent la valeur `false` à l’exception de `!=` (différent).</span><span class="sxs-lookup"><span data-stu-id="448d5-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="448d5-139">Ne partez pas du principe que parce qu’une comparaison en particulier retourne `false`, l’inverse retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="448d5-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="448d5-140">Dans l’exemple suivant, 10 n’est ni supérieur, ni inférieur, ni égal à null.</span><span class="sxs-lookup"><span data-stu-id="448d5-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="448d5-141">Seul `num1 != num2` donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="448d5-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="448d5-142">Une comparaison d’égalité de deux types Nullable tous deux null donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="448d5-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="448d5-143">??,</span><span class="sxs-lookup"><span data-stu-id="448d5-143">The ??</span></span> <span data-ttu-id="448d5-144">Opérateur</span><span class="sxs-lookup"><span data-stu-id="448d5-144">Operator</span></span>  
 <span data-ttu-id="448d5-145">L’opérateur `??` définit une valeur par défaut qui est retournée quand un type Nullable est assigné à un type non-Nullable.</span><span class="sxs-lookup"><span data-stu-id="448d5-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="448d5-146">Cet opérateur peut également être utilisé avec plusieurs types Nullable.</span><span class="sxs-lookup"><span data-stu-id="448d5-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="448d5-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="448d5-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="448d5-148">Type bool?</span><span class="sxs-lookup"><span data-stu-id="448d5-148">The bool? type</span></span>  
 <span data-ttu-id="448d5-149">Le type Nullable `bool?` peut contenir trois valeurs différentes : [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) et [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="448d5-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="448d5-150">Pour plus d’informations sur le cast d’une valeur bool? en bool, consultez [Guide pratique pour effectuer sans risque un cast du type bool? en bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="448d5-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="448d5-151">Les types booléens Nullable sont comme le type de variable booléen utilisé dans SQL.</span><span class="sxs-lookup"><span data-stu-id="448d5-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="448d5-152">Pour vérifier que les résultats produits par les opérateurs `&` et `|` sont cohérents avec le type booléen à trois valeurs dans SQL, les opérateurs prédéfinis suivants sont fournis :</span><span class="sxs-lookup"><span data-stu-id="448d5-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="448d5-153">Les résultats de ces opérateurs sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="448d5-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="448d5-154">X</span><span class="sxs-lookup"><span data-stu-id="448d5-154">X</span></span>|<span data-ttu-id="448d5-155">y</span><span class="sxs-lookup"><span data-stu-id="448d5-155">y</span></span>|<span data-ttu-id="448d5-156">x&y</span><span class="sxs-lookup"><span data-stu-id="448d5-156">x&y</span></span>|<span data-ttu-id="448d5-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="448d5-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="448d5-158">true</span><span class="sxs-lookup"><span data-stu-id="448d5-158">true</span></span>|<span data-ttu-id="448d5-159">true</span><span class="sxs-lookup"><span data-stu-id="448d5-159">true</span></span>|<span data-ttu-id="448d5-160">true</span><span class="sxs-lookup"><span data-stu-id="448d5-160">true</span></span>|<span data-ttu-id="448d5-161">true</span><span class="sxs-lookup"><span data-stu-id="448d5-161">true</span></span>|  
|<span data-ttu-id="448d5-162">true</span><span class="sxs-lookup"><span data-stu-id="448d5-162">true</span></span>|<span data-ttu-id="448d5-163">false</span><span class="sxs-lookup"><span data-stu-id="448d5-163">false</span></span>|<span data-ttu-id="448d5-164">false</span><span class="sxs-lookup"><span data-stu-id="448d5-164">false</span></span>|<span data-ttu-id="448d5-165">true</span><span class="sxs-lookup"><span data-stu-id="448d5-165">true</span></span>|  
|<span data-ttu-id="448d5-166">true</span><span class="sxs-lookup"><span data-stu-id="448d5-166">true</span></span>|<span data-ttu-id="448d5-167">null</span><span class="sxs-lookup"><span data-stu-id="448d5-167">null</span></span>|<span data-ttu-id="448d5-168">null</span><span class="sxs-lookup"><span data-stu-id="448d5-168">null</span></span>|<span data-ttu-id="448d5-169">true</span><span class="sxs-lookup"><span data-stu-id="448d5-169">true</span></span>|  
|<span data-ttu-id="448d5-170">false</span><span class="sxs-lookup"><span data-stu-id="448d5-170">false</span></span>|<span data-ttu-id="448d5-171">true</span><span class="sxs-lookup"><span data-stu-id="448d5-171">true</span></span>|<span data-ttu-id="448d5-172">false</span><span class="sxs-lookup"><span data-stu-id="448d5-172">false</span></span>|<span data-ttu-id="448d5-173">true</span><span class="sxs-lookup"><span data-stu-id="448d5-173">true</span></span>|  
|<span data-ttu-id="448d5-174">false</span><span class="sxs-lookup"><span data-stu-id="448d5-174">false</span></span>|<span data-ttu-id="448d5-175">false</span><span class="sxs-lookup"><span data-stu-id="448d5-175">false</span></span>|<span data-ttu-id="448d5-176">false</span><span class="sxs-lookup"><span data-stu-id="448d5-176">false</span></span>|<span data-ttu-id="448d5-177">false</span><span class="sxs-lookup"><span data-stu-id="448d5-177">false</span></span>|  
|<span data-ttu-id="448d5-178">false</span><span class="sxs-lookup"><span data-stu-id="448d5-178">false</span></span>|<span data-ttu-id="448d5-179">null</span><span class="sxs-lookup"><span data-stu-id="448d5-179">null</span></span>|<span data-ttu-id="448d5-180">false</span><span class="sxs-lookup"><span data-stu-id="448d5-180">false</span></span>|<span data-ttu-id="448d5-181">null</span><span class="sxs-lookup"><span data-stu-id="448d5-181">null</span></span>|  
|<span data-ttu-id="448d5-182">null</span><span class="sxs-lookup"><span data-stu-id="448d5-182">null</span></span>|<span data-ttu-id="448d5-183">true</span><span class="sxs-lookup"><span data-stu-id="448d5-183">true</span></span>|<span data-ttu-id="448d5-184">null</span><span class="sxs-lookup"><span data-stu-id="448d5-184">null</span></span>|<span data-ttu-id="448d5-185">true</span><span class="sxs-lookup"><span data-stu-id="448d5-185">true</span></span>|  
|<span data-ttu-id="448d5-186">null</span><span class="sxs-lookup"><span data-stu-id="448d5-186">null</span></span>|<span data-ttu-id="448d5-187">false</span><span class="sxs-lookup"><span data-stu-id="448d5-187">false</span></span>|<span data-ttu-id="448d5-188">false</span><span class="sxs-lookup"><span data-stu-id="448d5-188">false</span></span>|<span data-ttu-id="448d5-189">null</span><span class="sxs-lookup"><span data-stu-id="448d5-189">null</span></span>|  
|<span data-ttu-id="448d5-190">null</span><span class="sxs-lookup"><span data-stu-id="448d5-190">null</span></span>|<span data-ttu-id="448d5-191">null</span><span class="sxs-lookup"><span data-stu-id="448d5-191">null</span></span>|<span data-ttu-id="448d5-192">null</span><span class="sxs-lookup"><span data-stu-id="448d5-192">null</span></span>|<span data-ttu-id="448d5-193">null</span><span class="sxs-lookup"><span data-stu-id="448d5-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="448d5-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="448d5-194">See Also</span></span>  
 [<span data-ttu-id="448d5-195">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="448d5-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="448d5-196">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="448d5-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="448d5-197">Boxing des types Nullable</span><span class="sxs-lookup"><span data-stu-id="448d5-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="448d5-198">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="448d5-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
