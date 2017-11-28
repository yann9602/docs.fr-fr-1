---
title: "Tableaux implicitement typés (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="0eaf5-102">Tableaux implicitement typés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0eaf5-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="0eaf5-103">Vous pouvez créer un tableau implicitement typé dans lequel le type de l’instance de tableau est déduit à partir des éléments spécifiés dans l’initialiseur de tableau.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="0eaf5-104">Les règles applicables à une variable implicitement typée s’appliquent aussi aux tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="0eaf5-105">Pour plus d’informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="0eaf5-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="0eaf5-106">Les tableaux implicitement typés sont généralement utilisés dans les expressions de requête avec des types anonymes et des initialiseurs d’objets et de collections.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="0eaf5-107">Les exemples suivants montrent comment créer un tableau implicitement typé :</span><span class="sxs-lookup"><span data-stu-id="0eaf5-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="0eaf5-108">Dans l’exemple précédent, vous pouvez constater que dans le cas des tableaux implicitement typés, aucun crochet n’est utilisé à gauche de l’instruction d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="0eaf5-109">Notez aussi que les tableaux en escalier sont initialisés à l’aide de `new []` à l’instar des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="0eaf5-110">Tableaux implicitement typés dans les initialiseurs d’objets</span><span class="sxs-lookup"><span data-stu-id="0eaf5-110">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="0eaf5-111">Quand vous créez un type anonyme qui contient un tableau, le tableau doit être implicitement typé dans l’initialiseur d’objet du type.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="0eaf5-112">Dans l’exemple suivant, `contacts` est un tableau implicitement typé de types anonymes, dont chacun contient un tableau nommé `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="0eaf5-113">Notez que le mot clé `var` n’est pas utilisé dans les initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="0eaf5-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0eaf5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eaf5-114">See Also</span></span>  
 [<span data-ttu-id="0eaf5-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0eaf5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0eaf5-116">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="0eaf5-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [<span data-ttu-id="0eaf5-117">Tableaux</span><span class="sxs-lookup"><span data-stu-id="0eaf5-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="0eaf5-118">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="0eaf5-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="0eaf5-119">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="0eaf5-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="0eaf5-120">var</span><span class="sxs-lookup"><span data-stu-id="0eaf5-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="0eaf5-121">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="0eaf5-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
