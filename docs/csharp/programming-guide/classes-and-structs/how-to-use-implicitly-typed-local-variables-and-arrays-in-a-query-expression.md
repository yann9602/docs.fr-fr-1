---
title: "Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: 15
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
ms.openlocfilehash: 60e22aacef05ae2fe1b5e7127396cc66f24661d3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="d5c95-102">Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d5c95-102">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression (C# Programming Guide)</span></span>
<span data-ttu-id="d5c95-103">Vous pouvez utiliser des variables locales implicitement typées chaque fois que vous voulez que le compilateur détermine le type d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="d5c95-103">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="d5c95-104">Vous devez utiliser des variables locales implicitement typées pour stocker des types anonymes, qui sont souvent utilisés dans les expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="d5c95-104">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="d5c95-105">Les exemples suivants illustrent des utilisations facultatives et obligatoires de variables locales implicitement typées dans des requêtes.</span><span class="sxs-lookup"><span data-stu-id="d5c95-105">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="d5c95-106">Les variables locales implicitement typées sont déclarées à l’aide du mot clé contextuel [var](../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="d5c95-106">Implicitly typed local variables are declared by using the [var](../../../csharp/language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="d5c95-107">Pour plus d’informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="d5c95-107">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5c95-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5c95-108">Example</span></span>  
 <span data-ttu-id="d5c95-109">L’exemple suivant illustre un scénario courant dans lequel le mot clé `var` est obligatoire : une expression de requête qui produit une séquence de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="d5c95-109">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="d5c95-110">Dans ce scénario, la variable de requête et la variable d’itération figurant dans l’instruction `foreach` doivent être implicitement typées avec `var`, car vous n’avez pas accès à un nom de type pour le type anonyme.</span><span class="sxs-lookup"><span data-stu-id="d5c95-110">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="d5c95-111">Pour plus d’informations sur les types anonymes, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d5c95-111">For more information about anonymous types, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="d5c95-112">[!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5c95-112">[!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5c95-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5c95-113">Example</span></span>  
 <span data-ttu-id="d5c95-114">Dans l’exemple suivant, le mot clé `var` est utilisé dans un cas similaire, à la différence que l’utilisation de `var` est facultative.</span><span class="sxs-lookup"><span data-stu-id="d5c95-114">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="d5c95-115">Comme `student.LastName` est une chaîne, l’exécution de la requête retourne une séquence de chaînes.</span><span class="sxs-lookup"><span data-stu-id="d5c95-115">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="d5c95-116">De ce fait, le type de `queryID` pourrait être déclaré en tant que `System.Collections.Generic.IEnumerable<string>` au lieu de `var`.</span><span class="sxs-lookup"><span data-stu-id="d5c95-116">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="d5c95-117">Le mot clé `var` est utilisé pour des raisons pratiques.</span><span class="sxs-lookup"><span data-stu-id="d5c95-117">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="d5c95-118">Dans l’exemple, la variable d’itération figurant dans l’instruction `foreach` est explicitement typée en tant que chaîne, mais elle aurait pu être déclarée à l’aide de `var`.</span><span class="sxs-lookup"><span data-stu-id="d5c95-118">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="d5c95-119">Comme le type de la variable d’itération n’est pas un type anonyme, l’utilisation de `var` est facultative et non obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5c95-119">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="d5c95-120">Pour rappel, `var` n’est pas en soi un type, mais une instruction indiquant au compilateur de déduire et d’assigner le type.</span><span class="sxs-lookup"><span data-stu-id="d5c95-120">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 <span data-ttu-id="d5c95-121">[!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5c95-121">[!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c95-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c95-122">See Also</span></span>  
 <span data-ttu-id="d5c95-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5c95-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d5c95-124">[Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="d5c95-124">[Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
 <span data-ttu-id="d5c95-125">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="d5c95-125">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="d5c95-126">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="d5c95-126">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 [<span data-ttu-id="d5c95-127">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="d5c95-127">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

