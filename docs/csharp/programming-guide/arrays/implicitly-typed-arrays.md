---
title: "Tableaux implicitement typés (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: 13
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
ms.openlocfilehash: 5a042bdebd07062debe70cbea0a9661fbd425804
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="d283b-102">Tableaux implicitement typés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d283b-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="d283b-103">Vous pouvez créer un tableau implicitement typé dans lequel le type de l’instance de tableau est déduit à partir des éléments spécifiés dans l’initialiseur de tableau.</span><span class="sxs-lookup"><span data-stu-id="d283b-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="d283b-104">Les règles applicables à une variable implicitement typée s’appliquent aussi aux tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="d283b-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="d283b-105">Pour plus d’informations, consultez la page [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="d283b-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="d283b-106">Les tableaux implicitement typés sont généralement utilisés dans les expressions de requête avec des types anonymes et des initialiseurs d’objets et de collections.</span><span class="sxs-lookup"><span data-stu-id="d283b-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="d283b-107">Les exemples suivants montrent comment créer un tableau implicitement typé :</span><span class="sxs-lookup"><span data-stu-id="d283b-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 <span data-ttu-id="d283b-108">[!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d283b-108">[!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="d283b-109">Dans l’exemple précédent, vous pouvez constater que dans le cas des tableaux implicitement typés, aucun crochet n’est utilisé à gauche de l’instruction d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="d283b-109">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="d283b-110">Notez aussi que les tableaux en escalier sont initialisés à l’aide de `new []` à l’instar des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="d283b-110">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="d283b-111">Tableaux implicitement typés dans les initialiseurs d’objets</span><span class="sxs-lookup"><span data-stu-id="d283b-111">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="d283b-112">Quand vous créez un type anonyme qui contient un tableau, le tableau doit être implicitement typé dans l’initialiseur d’objet du type.</span><span class="sxs-lookup"><span data-stu-id="d283b-112">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="d283b-113">Dans l’exemple suivant, `contacts` est un tableau implicitement typé de types anonymes, dont chacun contient un tableau nommé `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="d283b-113">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="d283b-114">Notez que le mot clé `var` n’est pas utilisé dans les initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="d283b-114">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 <span data-ttu-id="d283b-115">[!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d283b-115">[!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d283b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d283b-116">See Also</span></span>  
 <span data-ttu-id="d283b-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d283b-118">[Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-118">[Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) </span></span>  
 <span data-ttu-id="d283b-119">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-119">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="d283b-120">[Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-120">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="d283b-121">[Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-121">[Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span></span>  
 <span data-ttu-id="d283b-122">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="d283b-122">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 [<span data-ttu-id="d283b-123">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="d283b-123">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

