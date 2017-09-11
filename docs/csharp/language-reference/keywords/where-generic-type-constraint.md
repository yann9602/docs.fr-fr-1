---
title: "where (contrainte de type générique) (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
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
ms.openlocfilehash: 8e81640ee56ed672bb09242a070fdf167740874b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="c71d3-102">where (contrainte de type générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="c71d3-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="c71d3-103">Dans une définition de type générique, la clause `where` permet de spécifier des contraintes sur les types qui peuvent être utilisés comme arguments pour un paramètre de type défini dans une déclaration générique.</span><span class="sxs-lookup"><span data-stu-id="c71d3-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="c71d3-104">Vous pouvez, par exemple, déclarer une classe générique, `MyGenericClass`, de telle sorte que le paramètre de type `T` implémente l’interface <xref:System.IComparable%601> :</span><span class="sxs-lookup"><span data-stu-id="c71d3-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="c71d3-105">Pour plus d’informations sur la clause where dans une expression de requête, consultez [where, clause](../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c71d3-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="c71d3-106">Outre les contraintes d’interface, une clause `where` peut contenir une contrainte de classe de base qui déclare qu’un type doit avoir la classe spécifiée en tant que classe de base (ou être cette classe) pour être utilisé comme un argument de type pour ce type générique.</span><span class="sxs-lookup"><span data-stu-id="c71d3-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="c71d3-107">Si une telle contrainte est utilisée, elle doit apparaître avant toute autre contrainte pesant sur ce paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="c71d3-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 <span data-ttu-id="c71d3-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c71d3-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span></span>  
  
 <span data-ttu-id="c71d3-109">La clause `where` peut également inclure une contrainte de constructeur.</span><span class="sxs-lookup"><span data-stu-id="c71d3-109">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="c71d3-110">Il est possible de créer une instance d’un paramètre de type à l’aide de l’opérateur new ; toutefois, il est nécessaire que le paramètre de type soit contraint par la contrainte du constructeur, `new()`.</span><span class="sxs-lookup"><span data-stu-id="c71d3-110">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="c71d3-111">La [contrainte new()](../../../csharp/language-reference/keywords/new-constraint.md) fait savoir au compilateur que tout argument de type fourni doit avoir un constructeur accessible sans paramètre, ou par défaut.</span><span class="sxs-lookup"><span data-stu-id="c71d3-111">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="c71d3-112">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c71d3-112">For example:</span></span>  
  
 <span data-ttu-id="c71d3-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c71d3-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="c71d3-114">La contrainte `new()` apparaît en dernier dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="c71d3-114">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="c71d3-115">Avec plusieurs paramètres de type, utilisez une clause `where` pour chaque paramètre de type, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c71d3-115">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 <span data-ttu-id="c71d3-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c71d3-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span></span>  
  
 <span data-ttu-id="c71d3-117">Vous pouvez également joindre des contraintes aux paramètres de type des méthodes génériques, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c71d3-117">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="c71d3-118">Notez que la syntaxe décrivant les contraintes de paramètre de type sur les délégués est la même que celle des méthodes :</span><span class="sxs-lookup"><span data-stu-id="c71d3-118">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="c71d3-119">Pour plus d’informations sur les délégués génériques, consultez [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c71d3-119">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="c71d3-120">Pour plus d’informations sur la syntaxe et l’utilisation de contraintes, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c71d3-120">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c71d3-121">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c71d3-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c71d3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c71d3-122">See Also</span></span>  
 <span data-ttu-id="c71d3-123">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c71d3-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c71d3-124">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c71d3-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c71d3-125">[Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="c71d3-125">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="c71d3-126">[new, contrainte](../../../csharp/language-reference/keywords/new-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="c71d3-126">[new Constraint](../../../csharp/language-reference/keywords/new-constraint.md) </span></span>  
 [<span data-ttu-id="c71d3-127">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="c71d3-127">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)

