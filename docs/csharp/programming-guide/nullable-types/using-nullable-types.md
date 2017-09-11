---
title: Utilisation de types Nullable (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0721d9f60abc4e158135d6b050953b3e63ab8cb5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="136d9-102">Utilisation de types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="136d9-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="136d9-103">Les types Nullable peuvent représenter toutes les valeurs d’un type sous-jacent ainsi qu’une autre valeur [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="136d9-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="136d9-104">Les types Nullable sont déclarés de l’une des deux façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="136d9-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="136d9-105">ou</span><span class="sxs-lookup"><span data-stu-id="136d9-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="136d9-106">`T` est le type sous-jacent du type Nullable.</span><span class="sxs-lookup"><span data-stu-id="136d9-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="136d9-107">`T` peut être n’importe quel type valeur, notamment `struct` ; il ne peut pas être un type référence.</span><span class="sxs-lookup"><span data-stu-id="136d9-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="136d9-108">Voici un exemple d’utilisation de type Nullable. Prenons une variable booléenne ordinaire. Elle peut avoir deux valeurs : true et false.</span><span class="sxs-lookup"><span data-stu-id="136d9-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="136d9-109">Il n’existe aucune valeur qui signifie « indéfini ».</span><span class="sxs-lookup"><span data-stu-id="136d9-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="136d9-110">Dans de nombreuses applications de programmation, notamment dans les interactions de base de données, les variables peuvent se produire dans un état indéfini.</span><span class="sxs-lookup"><span data-stu-id="136d9-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="136d9-111">Par exemple, un champ dans une base de données peut contenir les valeurs true ou false, mais peut aussi ne contenir aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="136d9-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="136d9-112">De même, les types référence peuvent être définis sur `null` pour indiquer qu’ils ne sont pas initialisés.</span><span class="sxs-lookup"><span data-stu-id="136d9-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="136d9-113">Cette disparité peut surcharger le travail de programmation, avec des variables supplémentaires pour stocker les informations d’état, l’utilisation de valeurs spéciales et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="136d9-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="136d9-114">Le modificateur de type Nullable permet à C# de créer des variables de type valeur qui indiquent une valeur indéfinie.</span><span class="sxs-lookup"><span data-stu-id="136d9-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="136d9-115">Exemples de types Nullable</span><span class="sxs-lookup"><span data-stu-id="136d9-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="136d9-116">Tout type valeur peut être utilisé comme base d’un type Nullable.</span><span class="sxs-lookup"><span data-stu-id="136d9-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="136d9-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="136d9-117">For example:</span></span>  
  
 <span data-ttu-id="136d9-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span></span>  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="136d9-119">Membres de types Nullable</span><span class="sxs-lookup"><span data-stu-id="136d9-119">The Members of Nullable Types</span></span>  
 <span data-ttu-id="136d9-120">Chaque instance d’un type Nullable a deux propriétés publiques en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="136d9-120">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="136d9-121">`HasValue` est de type `bool`.</span><span class="sxs-lookup"><span data-stu-id="136d9-121">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="136d9-122">Elle est définie sur `true` quand la variable contient une valeur non-null.</span><span class="sxs-lookup"><span data-stu-id="136d9-122">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="136d9-123">`Value` est du même type que le type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="136d9-123">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="136d9-124">Si `HasValue` est `true`, `Value` contient une valeur significative.</span><span class="sxs-lookup"><span data-stu-id="136d9-124">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="136d9-125">Si `HasValue` est `false`, l’accès à `Value` lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="136d9-125">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="136d9-126">Dans cet exemple, le membre `HasValue` est utilisé pour tester si la variable contient une valeur avant d’essayer de l’afficher.</span><span class="sxs-lookup"><span data-stu-id="136d9-126">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 <span data-ttu-id="136d9-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span></span>  
  
 <span data-ttu-id="136d9-128">Vous pouvez aussi tester une valeur comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="136d9-128">Testing for a value can also be done as in the following example:</span></span>  
  
 <span data-ttu-id="136d9-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span></span>  
  
## <a name="explicit-conversions"></a><span data-ttu-id="136d9-130">Conversions explicites</span><span class="sxs-lookup"><span data-stu-id="136d9-130">Explicit Conversions</span></span>  
 <span data-ttu-id="136d9-131">Un type Nullable peut être casté en type normal explicitement par un cast ou à l’aide de la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="136d9-131">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="136d9-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="136d9-132">For example:</span></span>  
  
 <span data-ttu-id="136d9-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span></span>  
  
 <span data-ttu-id="136d9-134">Si une conversion définie par l’utilisateur est définie entre deux types de données, la même conversion peut également être utilisée avec les versions Nullable de ces types de données.</span><span class="sxs-lookup"><span data-stu-id="136d9-134">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="136d9-135">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="136d9-135">Implicit Conversions</span></span>  
 <span data-ttu-id="136d9-136">Une variable de type Nullable peut être définie sur null avec le mot clé `null`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="136d9-136">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 <span data-ttu-id="136d9-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span></span>  
  
 <span data-ttu-id="136d9-138">La conversion d’un type ordinaire en type Nullable est implicite.</span><span class="sxs-lookup"><span data-stu-id="136d9-138">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 <span data-ttu-id="136d9-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span></span>  
  
## <a name="operators"></a><span data-ttu-id="136d9-140">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="136d9-140">Operators</span></span>  
 <span data-ttu-id="136d9-141">Les opérateurs unaire et binaire prédéfinis et tous les opérateurs définis par l’utilisateur existant pour les types valeur peuvent également être utilisés par les types Nullable.</span><span class="sxs-lookup"><span data-stu-id="136d9-141">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="136d9-142">Ces opérateurs produisent une valeur null si les opérandes sont null ; sinon, l’opérateur utilise la valeur contenue pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="136d9-142">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="136d9-143">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="136d9-143">For example:</span></span>  
  
 <span data-ttu-id="136d9-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span></span>  
  
 <span data-ttu-id="136d9-145">Quand vous effectuez des comparaisons avec des types Nullable, si la valeur de l’un des types Nullable est null et que l’autre ne l’est pas, toutes les comparaisons donnent la valeur `false` à l’exception de `!=` (différent).</span><span class="sxs-lookup"><span data-stu-id="136d9-145">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="136d9-146">Ne partez pas du principe que parce qu’une comparaison en particulier retourne `false`, l’inverse retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="136d9-146">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="136d9-147">Dans l’exemple suivant, 10 n’est ni supérieur, ni inférieur, ni égal à null.</span><span class="sxs-lookup"><span data-stu-id="136d9-147">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="136d9-148">Seul `num1 != num2` donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="136d9-148">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 <span data-ttu-id="136d9-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span></span>  
  
 <span data-ttu-id="136d9-150">Une comparaison d’égalité de deux types Nullable tous deux null donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="136d9-150">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="136d9-151">??,</span><span class="sxs-lookup"><span data-stu-id="136d9-151">The ??</span></span> <span data-ttu-id="136d9-152">Opérateur</span><span class="sxs-lookup"><span data-stu-id="136d9-152">Operator</span></span>  
 <span data-ttu-id="136d9-153">L’opérateur `??` définit une valeur par défaut qui est retournée quand un type Nullable est assigné à un type non-Nullable.</span><span class="sxs-lookup"><span data-stu-id="136d9-153">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 <span data-ttu-id="136d9-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span></span>  
  
 <span data-ttu-id="136d9-155">Cet opérateur peut également être utilisé avec plusieurs types Nullable.</span><span class="sxs-lookup"><span data-stu-id="136d9-155">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="136d9-156">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="136d9-156">For example:</span></span>  
  
 <span data-ttu-id="136d9-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="136d9-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span></span>  
  
## <a name="the-bool-type"></a><span data-ttu-id="136d9-158">Type bool?</span><span class="sxs-lookup"><span data-stu-id="136d9-158">The bool? type</span></span>  
 <span data-ttu-id="136d9-159">Le type Nullable `bool?` peut contenir trois valeurs différentes : [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) et [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="136d9-159">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="136d9-160">Pour plus d’informations sur le cast d’une valeur bool? en bool, consultez [Guide pratique pour effectuer sans risque un cast du type bool? en bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="136d9-160">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="136d9-161">Les types booléens Nullable sont comme le type de variable booléen utilisé dans SQL.</span><span class="sxs-lookup"><span data-stu-id="136d9-161">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="136d9-162">Pour vérifier que les résultats produits par les opérateurs `&` et `|` sont cohérents avec le type booléen à trois valeurs dans SQL, les opérateurs prédéfinis suivants sont fournis :</span><span class="sxs-lookup"><span data-stu-id="136d9-162">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="136d9-163">Les résultats de ces opérateurs sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="136d9-163">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="136d9-164">X</span><span class="sxs-lookup"><span data-stu-id="136d9-164">X</span></span>|<span data-ttu-id="136d9-165">y</span><span class="sxs-lookup"><span data-stu-id="136d9-165">y</span></span>|<span data-ttu-id="136d9-166">x&y</span><span class="sxs-lookup"><span data-stu-id="136d9-166">x&y</span></span>|<span data-ttu-id="136d9-167">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="136d9-167">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="136d9-168">true</span><span class="sxs-lookup"><span data-stu-id="136d9-168">true</span></span>|<span data-ttu-id="136d9-169">true</span><span class="sxs-lookup"><span data-stu-id="136d9-169">true</span></span>|<span data-ttu-id="136d9-170">true</span><span class="sxs-lookup"><span data-stu-id="136d9-170">true</span></span>|<span data-ttu-id="136d9-171">true</span><span class="sxs-lookup"><span data-stu-id="136d9-171">true</span></span>|  
|<span data-ttu-id="136d9-172">true</span><span class="sxs-lookup"><span data-stu-id="136d9-172">true</span></span>|<span data-ttu-id="136d9-173">false</span><span class="sxs-lookup"><span data-stu-id="136d9-173">false</span></span>|<span data-ttu-id="136d9-174">false</span><span class="sxs-lookup"><span data-stu-id="136d9-174">false</span></span>|<span data-ttu-id="136d9-175">true</span><span class="sxs-lookup"><span data-stu-id="136d9-175">true</span></span>|  
|<span data-ttu-id="136d9-176">true</span><span class="sxs-lookup"><span data-stu-id="136d9-176">true</span></span>|<span data-ttu-id="136d9-177">null</span><span class="sxs-lookup"><span data-stu-id="136d9-177">null</span></span>|<span data-ttu-id="136d9-178">null</span><span class="sxs-lookup"><span data-stu-id="136d9-178">null</span></span>|<span data-ttu-id="136d9-179">true</span><span class="sxs-lookup"><span data-stu-id="136d9-179">true</span></span>|  
|<span data-ttu-id="136d9-180">false</span><span class="sxs-lookup"><span data-stu-id="136d9-180">false</span></span>|<span data-ttu-id="136d9-181">true</span><span class="sxs-lookup"><span data-stu-id="136d9-181">true</span></span>|<span data-ttu-id="136d9-182">false</span><span class="sxs-lookup"><span data-stu-id="136d9-182">false</span></span>|<span data-ttu-id="136d9-183">true</span><span class="sxs-lookup"><span data-stu-id="136d9-183">true</span></span>|  
|<span data-ttu-id="136d9-184">false</span><span class="sxs-lookup"><span data-stu-id="136d9-184">false</span></span>|<span data-ttu-id="136d9-185">false</span><span class="sxs-lookup"><span data-stu-id="136d9-185">false</span></span>|<span data-ttu-id="136d9-186">false</span><span class="sxs-lookup"><span data-stu-id="136d9-186">false</span></span>|<span data-ttu-id="136d9-187">false</span><span class="sxs-lookup"><span data-stu-id="136d9-187">false</span></span>|  
|<span data-ttu-id="136d9-188">false</span><span class="sxs-lookup"><span data-stu-id="136d9-188">false</span></span>|<span data-ttu-id="136d9-189">null</span><span class="sxs-lookup"><span data-stu-id="136d9-189">null</span></span>|<span data-ttu-id="136d9-190">false</span><span class="sxs-lookup"><span data-stu-id="136d9-190">false</span></span>|<span data-ttu-id="136d9-191">null</span><span class="sxs-lookup"><span data-stu-id="136d9-191">null</span></span>|  
|<span data-ttu-id="136d9-192">null</span><span class="sxs-lookup"><span data-stu-id="136d9-192">null</span></span>|<span data-ttu-id="136d9-193">true</span><span class="sxs-lookup"><span data-stu-id="136d9-193">true</span></span>|<span data-ttu-id="136d9-194">null</span><span class="sxs-lookup"><span data-stu-id="136d9-194">null</span></span>|<span data-ttu-id="136d9-195">true</span><span class="sxs-lookup"><span data-stu-id="136d9-195">true</span></span>|  
|<span data-ttu-id="136d9-196">null</span><span class="sxs-lookup"><span data-stu-id="136d9-196">null</span></span>|<span data-ttu-id="136d9-197">false</span><span class="sxs-lookup"><span data-stu-id="136d9-197">false</span></span>|<span data-ttu-id="136d9-198">false</span><span class="sxs-lookup"><span data-stu-id="136d9-198">false</span></span>|<span data-ttu-id="136d9-199">null</span><span class="sxs-lookup"><span data-stu-id="136d9-199">null</span></span>|  
|<span data-ttu-id="136d9-200">null</span><span class="sxs-lookup"><span data-stu-id="136d9-200">null</span></span>|<span data-ttu-id="136d9-201">null</span><span class="sxs-lookup"><span data-stu-id="136d9-201">null</span></span>|<span data-ttu-id="136d9-202">null</span><span class="sxs-lookup"><span data-stu-id="136d9-202">null</span></span>|<span data-ttu-id="136d9-203">null</span><span class="sxs-lookup"><span data-stu-id="136d9-203">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="136d9-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="136d9-204">See Also</span></span>  
 <span data-ttu-id="136d9-205">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="136d9-205">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="136d9-206">[Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="136d9-206">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 <span data-ttu-id="136d9-207">[Boxing des types Nullable](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span><span class="sxs-lookup"><span data-stu-id="136d9-207">[Boxing Nullable Types](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span></span>  
 [<span data-ttu-id="136d9-208">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="136d9-208">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

