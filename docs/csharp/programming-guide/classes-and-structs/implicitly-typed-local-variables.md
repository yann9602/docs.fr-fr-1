---
title: "Variables locales implicitement typées (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="bb6cf-102">Variables locales implicitement typées (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bb6cf-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="bb6cf-103">Les variables locales peuvent être déclarées sans donner de type explicite.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="bb6cf-104">Le mot clé `var` indique au compilateur de déduire le type de la variable à partir de l’expression située à droite de l’instruction d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="bb6cf-105">Le type déduit peut être un type intégré, un type anonyme, un type défini par l’utilisateur ou un type défini dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="bb6cf-106">Pour plus d’informations sur l’initialisation des tableaux avec `var`, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bb6cf-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="bb6cf-107">Les exemples suivants montrent différentes manières de déclarer des variables locales avec `var` :</span><span class="sxs-lookup"><span data-stu-id="bb6cf-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="bb6cf-108">Il est important de comprendre que le mot clé `var` n’est pas « variant » et qu’il n’indique pas que la variable est peu typée ou à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="bb6cf-109">Cela signifie simplement que le compilateur détermine et assigne le type qui convient le mieux.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="bb6cf-110">Le mot clé `var` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="bb6cf-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="bb6cf-111">Dans des variables locales (variables déclarées dans la portée de la méthode), comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="bb6cf-112">Dans une instruction d’initialisation [for](../../../csharp/language-reference/keywords/for.md)</span><span class="sxs-lookup"><span data-stu-id="bb6cf-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="bb6cf-113">Dans une instruction d’initialisation [foreach](../../../csharp/language-reference/keywords/foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="bb6cf-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="bb6cf-114">Dans une instruction [using](../../../csharp/language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bb6cf-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="bb6cf-115">Pour plus d’informations, consultez [Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="bb6cf-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="bb6cf-116">Types de variables et types anonymes</span><span class="sxs-lookup"><span data-stu-id="bb6cf-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="bb6cf-117">Dans de nombreux cas, l’utilisation de `var` est facultative et sert uniquement à simplifier la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="bb6cf-118">Toutefois, lorsqu’une variable est initialisée avec un type anonyme, vous devez déclarer la variable en tant que `var` si vous savez déjà que vous aurez besoin d’accéder aux propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="bb6cf-119">Il s’agit d’un scénario courant avec les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb6cf-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="bb6cf-120">Pour plus d’informations, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="bb6cf-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="bb6cf-121">Du point de vue de votre code source, un type anonyme n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="bb6cf-122">Par conséquent, si une variable de requête a été initialisée avec `var`, la seule façon d’accéder aux propriétés de la séquence d’objets retournée consiste à utiliser `var` comme type pour la variable d’itération de l’instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="bb6cf-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb6cf-123">Remarks</span></span>  
 <span data-ttu-id="bb6cf-124">Les restrictions suivantes s’appliquent aux déclarations de variables implicitement typées :</span><span class="sxs-lookup"><span data-stu-id="bb6cf-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="bb6cf-125">`var` peut être utilisé uniquement lorsqu’une variable locale est déclarée et initialisée dans la même instruction. La variable ne peut pas être initialisée vers la valeur Null, vers un groupe de méthodes ou vers une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="bb6cf-126">`var` ne peut pas être utilisé dans les champs situés dans la portée de la classe.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="bb6cf-127">Les variables déclarées à l’aide de `var` ne peuvent pas être utilisées dans l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="bb6cf-128">En d’autres termes, l’expression `: int i = (i = 20);` est légale, mais l’expression `var i = (i = 20);` génère une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="bb6cf-129">Il n’est pas possible d’initialiser plusieurs variables implicitement typées dans la même instruction.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="bb6cf-130">Si un type nommé `var` se trouve dans la portée, le mot clé `var` est résolu en ce nom de type et n’est pas considéré comme faisant partie d’une déclaration de variable locale implicitement typée.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="bb6cf-131">`var` peut également être utile avec les expressions de requête dans lesquelles il est difficile de déterminer le type construit exact de la variable de requête.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="bb6cf-132">Cela peut se produire avec les opérations de regroupement et de classement.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="bb6cf-133">Le mot clé `var` peut également être utile lorsque le type de la variable est fastidieux à taper, ou bien lorsqu’il est évident ou lorsqu’il n’aide pas à la lisibilité du code.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="bb6cf-134">Par exemple, `var` est utile avec les types génériques imbriqués tels que ceux utilisés avec les opérations de groupe.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="bb6cf-135">Dans la requête suivante, le type de la variable de requête est `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="bb6cf-136">Tant que les personnes qui doivent gérer votre code comprennent ceci, le typage implicite peut tout à fait être utilisé pour rendre votre code plus concis et simplifier sa gestion.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="bb6cf-137">Toutefois, l’utilisation de `var` risque de rendre votre code plus difficile à comprendre pour les autres développeurs.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="bb6cf-138">C’est pourquoi, en général, la documentation C# utilise `var` uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="bb6cf-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6cf-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb6cf-139">See Also</span></span>  
 [<span data-ttu-id="bb6cf-140">Référence C#</span><span class="sxs-lookup"><span data-stu-id="bb6cf-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bb6cf-141">Tableaux implicitement typés</span><span class="sxs-lookup"><span data-stu-id="bb6cf-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="bb6cf-142">Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="bb6cf-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="bb6cf-143">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="bb6cf-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="bb6cf-144">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="bb6cf-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="bb6cf-145">var</span><span class="sxs-lookup"><span data-stu-id="bb6cf-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="bb6cf-146">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="bb6cf-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="bb6cf-147">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="bb6cf-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="bb6cf-148">for</span><span class="sxs-lookup"><span data-stu-id="bb6cf-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="bb6cf-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="bb6cf-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="bb6cf-150">using, instruction</span><span class="sxs-lookup"><span data-stu-id="bb6cf-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
