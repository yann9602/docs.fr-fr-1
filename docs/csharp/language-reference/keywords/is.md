---
title: "is (référence C#)"
keywords: "mot clé is (C#), is (C#)"
ms.date: 2017-02-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
dev_langs:
- CSharp
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
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
ms.openlocfilehash: 58b18284b12ca0c636ed3fa923c43d94f202597f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="is-c-reference"></a><span data-ttu-id="71122-103">is (référence C#)</span><span class="sxs-lookup"><span data-stu-id="71122-103">is (C# Reference)</span></span> #

<span data-ttu-id="71122-104">Vérifie si un objet est compatible avec un type donné, ou (avec C# 7) teste une expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="71122-104">Checks if an object is compatible with a given type, or (starting with C# 7) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="71122-105">Test de compatibilité de type</span><span class="sxs-lookup"><span data-stu-id="71122-105">Testing for type compatibility</span></span> ##

<span data-ttu-id="71122-106">Le mot clé `is` évalue la compatibilité de type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="71122-106">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="71122-107">Il détermine si une instance d’objet ou le résultat d’une expression peuvent être convertis en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="71122-107">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="71122-108">Sa syntaxe est</span><span class="sxs-lookup"><span data-stu-id="71122-108">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="71122-109">où *expr* est une expression qui correspond à une instance d’un type, et où *type* est le nom du type dans lequel le résultat de *expr* doit être converti.</span><span class="sxs-lookup"><span data-stu-id="71122-109">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="71122-110">L’instruction `is` est `true` si *expr* est non-Null et si l’objet qui résulte de l’évaluation de l’expression peut être converti en *type* ; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="71122-110">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="71122-111">Par exemple, le code suivant détermine si `obj` peut être casté en une instance de type `Person` :</span><span class="sxs-lookup"><span data-stu-id="71122-111">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

<span data-ttu-id="71122-112">[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="71122-112">[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]</span></span>

<span data-ttu-id="71122-113">L’instruction `is` a la valeur true si :</span><span class="sxs-lookup"><span data-stu-id="71122-113">The `is` statement is true if:</span></span>

- <span data-ttu-id="71122-114">*expr* est une instance du même type que *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-114">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="71122-115">*expr* est une instance d’un type qui dérive de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-115">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="71122-116">En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-116">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="71122-117">*expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-117">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="71122-118">Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="71122-118">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="71122-119">Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.</span><span class="sxs-lookup"><span data-stu-id="71122-119">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="71122-120">*expr* est une instance d’un type qui implémente l’interface *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-120">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="71122-121">L’exemple suivant montre que l’expression `is` a la valeur `true` pour chacune de ces conversions.</span><span class="sxs-lookup"><span data-stu-id="71122-121">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

<span data-ttu-id="71122-122">[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="71122-122">[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]</span></span>

<span data-ttu-id="71122-123">Le mot clé `is` génère un avertissement au moment de la compilation si l’expression est connue pour être toujours soit `true`, soit `false`.</span><span class="sxs-lookup"><span data-stu-id="71122-123">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="71122-124">Il tient compte uniquement des conversions de référence, des conversions boxing et des conversions unboxing. Il ne tient pas compte des conversions définies par l’utilisateur ni des conversions définies par les opérateurs [implicit](implicit.md) et [explicit](explicit.md) d’un type.</span><span class="sxs-lookup"><span data-stu-id="71122-124">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="71122-125">L’exemple suivant génère des avertissements, car le résultat de la conversion est connu au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="71122-125">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="71122-126">Notez que l’expression `is` pour les conversions de `int` à `long` et `double` retourne la valeur false, puisque ces conversions sont gérées par l’opérateur [implicit](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="71122-126">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

<span data-ttu-id="71122-127">[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="71122-127">[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]</span></span>

<span data-ttu-id="71122-128">`expr` peut correspondre à toute expression qui retourne une valeur, à l’exception des méthodes anonymes et des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="71122-128">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="71122-129">L’exemple suivant utilise `is` pour évaluer la valeur de retour d’un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="71122-129">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
<span data-ttu-id="71122-130">[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]</span><span class="sxs-lookup"><span data-stu-id="71122-130">[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]</span></span>

<span data-ttu-id="71122-131">Avec C# 7, vous pouvez utiliser les critères spéciaux avec le [modèle de type](#type) pour écrire du code plus concis qui utilise l’instruction `is`.</span><span class="sxs-lookup"><span data-stu-id="71122-131">Starting with C# 7, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="71122-132">Utilisation des critères spéciaux avec `is`</span><span class="sxs-lookup"><span data-stu-id="71122-132">Pattern matching with `is`</span></span> ##

<span data-ttu-id="71122-133">Avec C# 7, les instructions `is` et [switch](../../../csharp/language-reference/keywords/switch.md) prennent en charge les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="71122-133">Starting with C# 7, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="71122-134">Le mot clé `is` prend en charge les modèles suivants :</span><span class="sxs-lookup"><span data-stu-id="71122-134">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="71122-135">[Modèle de type](#type) : permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, caste l’expression en une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="71122-135">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="71122-136">[Modèle de constante](#constant) : teste si une expression correspond à une valeur de constante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="71122-136">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="71122-137">[Modèle de variable](#var) : correspondance qui réussit toujours et lie la valeur d’une expression à une variable locale.</span><span class="sxs-lookup"><span data-stu-id="71122-137">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="71122-138"><a name="type" /> Modèle de type </a></span><span class="sxs-lookup"><span data-stu-id="71122-138"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="71122-139">Lorsque vous utilisez le modèle de type pour rechercher des critères spéciaux, `is` permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, effectuer un cast de l’expression en une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="71122-139">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="71122-140">Il s’agit d’une extension simple de l’instruction `is` qui permet une évaluation et une conversion de type concises.</span><span class="sxs-lookup"><span data-stu-id="71122-140">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="71122-141">La forme générale du modèle de type `is` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="71122-141">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="71122-142">où *expr* est une expression qui correspond à une instance d’un type, où *type* est le nom du type dans lequel le résultat de *expr* doit être converti, et où *varname* est l’objet dans lequel le résultat de *expr* est converti si le test `is` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="71122-142">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="71122-143">L’expression `is` est `true` si l’une des affirmations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="71122-143">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="71122-144">*expr* est une instance du même type que *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-144">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="71122-145">*expr* est une instance d’un type qui dérive de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-145">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="71122-146">En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-146">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="71122-147">*expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-147">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="71122-148">Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="71122-148">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="71122-149">Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.</span><span class="sxs-lookup"><span data-stu-id="71122-149">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="71122-150">*expr* est une instance d’un type qui implémente l’interface *type*.</span><span class="sxs-lookup"><span data-stu-id="71122-150">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="71122-151">Si *exp* est `true` et si `is` est utilisé avec une instruction `if`, *varname* est assigné et sa portée locale se limite à l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="71122-151">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="71122-152">L’exemple suivant utilise le modèle de type `is` pour fournir l’implémentation de la méthode <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> d’un type.</span><span class="sxs-lookup"><span data-stu-id="71122-152">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> method.</span></span>

<span data-ttu-id="71122-153">[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]</span><span class="sxs-lookup"><span data-stu-id="71122-153">[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]</span></span>

<span data-ttu-id="71122-154">Sans critères spéciaux, ce code peut être écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="71122-154">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="71122-155">L’utilisation de critères spéciaux de type génère un code lisible plus compact en éliminant la nécessité de tester si le résultat d’une conversion est un `null`.</span><span class="sxs-lookup"><span data-stu-id="71122-155">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

<span data-ttu-id="71122-156">[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]</span><span class="sxs-lookup"><span data-stu-id="71122-156">[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]</span></span>

<span data-ttu-id="71122-157">Le modèle de type `is` génère également du code plus compact lorsqu’il détermine le type d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="71122-157">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="71122-158">L’exemple suivant utilise le modèle de type `is` pour déterminer si un objet est une instance `Person` ou `Dog` avant d’afficher la valeur d’une propriété appropriée.</span><span class="sxs-lookup"><span data-stu-id="71122-158">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

<span data-ttu-id="71122-159">[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]</span><span class="sxs-lookup"><span data-stu-id="71122-159">[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]</span></span>

<span data-ttu-id="71122-160">Le code équivalent sans critères spéciaux nécessite une attribution distincte comprenant un cast explicite.</span><span class="sxs-lookup"><span data-stu-id="71122-160">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

<span data-ttu-id="71122-161">[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]</span><span class="sxs-lookup"><span data-stu-id="71122-161">[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]</span></span>

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="71122-162"><a name="constant" /> Modèle de constante</span><span class="sxs-lookup"><span data-stu-id="71122-162"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="71122-163">Lorsque vous utilisez des critères spéciaux avec le modèle de constante, `is` teste si une expression est égale à une constante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="71122-163">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="71122-164">Avec C# 6 et les versions antérieures, le modèle de constante est pris en charge par l’instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="71122-164">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="71122-165">À compter de C# 7, ce modèle est également pris en charge par l’instruction `is`.</span><span class="sxs-lookup"><span data-stu-id="71122-165">Starting with C# 7, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="71122-166">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="71122-166">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="71122-167">où *expr* est l’expression à évaluer, et où *constant* est la valeur à tester.</span><span class="sxs-lookup"><span data-stu-id="71122-167">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="71122-168">*constant* peut correspondre à l’une des expressions constantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="71122-168">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="71122-169">Une valeur littérale</span><span class="sxs-lookup"><span data-stu-id="71122-169">A literal value.</span></span>

- <span data-ttu-id="71122-170">Le nom d’une variable `const` déclarée</span><span class="sxs-lookup"><span data-stu-id="71122-170">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="71122-171">Une constante d’énumération</span><span class="sxs-lookup"><span data-stu-id="71122-171">An enumeration constant.</span></span>

<span data-ttu-id="71122-172">L’expression constante est évaluée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="71122-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="71122-173">Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="71122-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="71122-174">Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="71122-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="71122-175">L’exemple suivant combine le modèle de type et le modèle de constante pour tester si un objet est une instance `Dice` et, si c’est le cas, pour déterminer si la valeur obtenue après un lancer de dés est de 6.</span><span class="sxs-lookup"><span data-stu-id="71122-175">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

<span data-ttu-id="71122-176">[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]</span><span class="sxs-lookup"><span data-stu-id="71122-176">[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]</span></span>
 
### <span data-ttu-id="71122-177"><a name="var" /> Modèle de variable </a></span><span class="sxs-lookup"><span data-stu-id="71122-177"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="71122-178">Une recherche de critères spéciaux qui utilise le modèle de variable réussit toujours.</span><span class="sxs-lookup"><span data-stu-id="71122-178">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="71122-179">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="71122-179">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="71122-180">où la valeur de *expr* est toujours assignée à une variable locale nommée *varname*.</span><span class="sxs-lookup"><span data-stu-id="71122-180">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="71122-181">*varname* est une variable statique du même type que *expr*.</span><span class="sxs-lookup"><span data-stu-id="71122-181">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="71122-182">L’exemple suivant utilise le modèle de variable pour assigner une expression à une variable nommée `obj`.</span><span class="sxs-lookup"><span data-stu-id="71122-182">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="71122-183">Il affiche ensuite la valeur et le type de `obj`.</span><span class="sxs-lookup"><span data-stu-id="71122-183">It then displays the value and the type of `obj`.</span></span>

<span data-ttu-id="71122-184">[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]</span><span class="sxs-lookup"><span data-stu-id="71122-184">[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]</span></span>

<span data-ttu-id="71122-185">Notez que si *expr* est `null`, l’expression `is` a toujours la valeur true et attribue `null` à *varname*.</span><span class="sxs-lookup"><span data-stu-id="71122-185">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="71122-186">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="71122-186">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71122-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71122-187">See also</span></span>  
 <span data-ttu-id="71122-188">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="71122-188">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="71122-189">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="71122-189">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="71122-190">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span><span class="sxs-lookup"><span data-stu-id="71122-190">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span></span>  
 <span data-ttu-id="71122-191">[as](../../../csharp/language-reference/keywords/as.md) </span><span class="sxs-lookup"><span data-stu-id="71122-191">[as](../../../csharp/language-reference/keywords/as.md) </span></span>  
 [<span data-ttu-id="71122-192">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="71122-192">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

