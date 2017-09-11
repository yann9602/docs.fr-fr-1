---
title: Boxing et unboxing (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c783ac60735ba25db2736bd9469063c0897be22f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="31fbe-102">Boxing et unboxing (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="31fbe-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="31fbe-103">Le boxing est la conversion d’un [type valeur](../../../csharp/language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="31fbe-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="31fbe-104">Lorsque le CLR exécute un boxing d’un type valeur, il inclut la valeur dans un wrapper, à l’intérieur d’un System.Object, et la stocke sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="31fbe-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="31fbe-105">L'unboxing extrait le type valeur de l'objet.</span><span class="sxs-lookup"><span data-stu-id="31fbe-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="31fbe-106">La conversion boxing est implicite ; la conversion unboxing est explicite.</span><span class="sxs-lookup"><span data-stu-id="31fbe-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="31fbe-107">Le concept de boxing et de unboxing repose sur la vue unifiée par C# du système de type, dans lequel une valeur de n'importe quel type peut être traitée en tant qu'objet.</span><span class="sxs-lookup"><span data-stu-id="31fbe-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="31fbe-108">Dans l’exemple suivant, la variable de type entier `i` est convertie (*boxed*) et assignée à l’objet `o`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 <span data-ttu-id="31fbe-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-110">L’objet `o` peut ensuite être unboxed et assigné à la variable de type entier `i` :</span><span class="sxs-lookup"><span data-stu-id="31fbe-110">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 <span data-ttu-id="31fbe-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-112">Les exemples suivants montrent comment le boxing est utilisé dans C#.</span><span class="sxs-lookup"><span data-stu-id="31fbe-112">The following examples illustrate how boxing is used in C#.</span></span>  
  
 <span data-ttu-id="31fbe-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span></span>  
  
## <a name="performance"></a><span data-ttu-id="31fbe-114">Performances</span><span class="sxs-lookup"><span data-stu-id="31fbe-114">Performance</span></span>  
 <span data-ttu-id="31fbe-115">Par rapport aux assignations simples, le boxing et l'unboxing sont des processus qui coûtent cher en calcul.</span><span class="sxs-lookup"><span data-stu-id="31fbe-115">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="31fbe-116">Lorsqu'un type valeur est boxed, un nouvel objet doit être alloué et construit.</span><span class="sxs-lookup"><span data-stu-id="31fbe-116">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="31fbe-117">À un degré moindre, le cast requis pour l'unboxing coûte également cher en calcul.</span><span class="sxs-lookup"><span data-stu-id="31fbe-117">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="31fbe-118">Pour plus d’informations, consultez [Performances](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="31fbe-118">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="31fbe-119">Boxing</span><span class="sxs-lookup"><span data-stu-id="31fbe-119">Boxing</span></span>  
 <span data-ttu-id="31fbe-120">Le boxing est utilisé pour stocker des types valeur dans le tas rassemblé par garbage collection.</span><span class="sxs-lookup"><span data-stu-id="31fbe-120">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="31fbe-121">Le boxing est une conversion implicite d’un [type valeur](../../../csharp/language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="31fbe-121">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="31fbe-122">Le boxing d'un type valeur alloue une instance d'objet sur le tas et copie la valeur dans le nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="31fbe-122">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="31fbe-123">Dans l'exemple suivant, une variable de type valeur est déclarée :</span><span class="sxs-lookup"><span data-stu-id="31fbe-123">Consider the following declaration of a value-type variable:</span></span>  
  
 <span data-ttu-id="31fbe-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-125">L'instruction ci-dessous réalise implicitement une opération de boxing sur la variable `i` :</span><span class="sxs-lookup"><span data-stu-id="31fbe-125">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 <span data-ttu-id="31fbe-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-127">Le résultat de cette instruction crée, sur la pile, un objet `o` qui fait référence à une valeur de type `int` sur le tas.</span><span class="sxs-lookup"><span data-stu-id="31fbe-127">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="31fbe-128">Cette valeur est une copie de la valeur de type valeur qui a été assignée à la variable `i`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-128">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="31fbe-129">La différence entre les deux variables, `i` et `o`, est illustrée dans la figure ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="31fbe-129">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="31fbe-130">![Graphique d’une conversion boxing](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="31fbe-130">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="31fbe-131">Conversion boxing</span><span class="sxs-lookup"><span data-stu-id="31fbe-131">Boxing Conversion</span></span>  
  
 <span data-ttu-id="31fbe-132">Il est également possible, mais jamais obligatoire, d'effectuer un boxing explicite comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="31fbe-132">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 <span data-ttu-id="31fbe-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span></span>  
  
## <a name="description"></a><span data-ttu-id="31fbe-134">Description</span><span class="sxs-lookup"><span data-stu-id="31fbe-134">Description</span></span>  
 <span data-ttu-id="31fbe-135">Cet exemple utilise le boxing pour convertir une variable `i` (entier) en un objet `o`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-135">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="31fbe-136">Ensuite, la valeur `i` stockée dans la variable `123` est remplacée par la valeur `456`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-136">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="31fbe-137">L'exemple montre que le type valeur d'origine et que l'objet boxed utilisent des emplacements de mémoire distincts et peuvent, par conséquent, stocker des valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="31fbe-137">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31fbe-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="31fbe-138">Example</span></span>  
 <span data-ttu-id="31fbe-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span></span>  
  
## <a name="unboxing"></a><span data-ttu-id="31fbe-140">Unboxing</span><span class="sxs-lookup"><span data-stu-id="31fbe-140">Unboxing</span></span>  
 <span data-ttu-id="31fbe-141">L’unboxing est une conversion explicite du type `object` en un [type valeur](../../../csharp/language-reference/keywords/value-types.md), ou d’un type interface en un type valeur qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="31fbe-141">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="31fbe-142">Une opération d'unboxing comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="31fbe-142">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="31fbe-143">Vérification de l'instance de l'objet pour s'assurer qu'il s'agit bien d'une valeur boxed du type valeur spécifié.</span><span class="sxs-lookup"><span data-stu-id="31fbe-143">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="31fbe-144">Copie de la valeur de l'instance dans la variable de type valeur.</span><span class="sxs-lookup"><span data-stu-id="31fbe-144">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="31fbe-145">Les instructions suivantes expliquent les opérations de boxing et d'unboxing :</span><span class="sxs-lookup"><span data-stu-id="31fbe-145">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 <span data-ttu-id="31fbe-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-147">Le résultat de ces instructions est illustré dans la figure ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="31fbe-147">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="31fbe-148">![Graphique de conversion unboxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="31fbe-148">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="31fbe-149">Conversion unboxing</span><span class="sxs-lookup"><span data-stu-id="31fbe-149">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="31fbe-150">Pour que l'unboxing de types valeur réussisse au moment de l'exécution, l'élément qui est unboxed doit être une référence à un objet précédemment créé par boxing d'une instance de ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="31fbe-150">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="31fbe-151">La tentative d'extraction de `null` provoque un <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="31fbe-151">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="31fbe-152">La tentative d'extraction d'une référence vers un type de valeur incompatible provoque un <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="31fbe-152">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31fbe-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="31fbe-153">Example</span></span>  
 <span data-ttu-id="31fbe-154">L'exemple suivant montre un cas d'unboxing non valide et l'`InvalidCastException` qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="31fbe-154">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="31fbe-155">Avec `try` et `catch`, un message d'erreur est affiché lorsque l'erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="31fbe-155">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 <span data-ttu-id="31fbe-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="31fbe-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span></span>  
  
 <span data-ttu-id="31fbe-157">Sortie de ce programme :</span><span class="sxs-lookup"><span data-stu-id="31fbe-157">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="31fbe-158">Si vous modifiez l'instruction :</span><span class="sxs-lookup"><span data-stu-id="31fbe-158">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="31fbe-159">en :</span><span class="sxs-lookup"><span data-stu-id="31fbe-159">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="31fbe-160">la conversion sera réalisée, avec le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="31fbe-160">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="31fbe-161">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="31fbe-161">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="31fbe-162">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="31fbe-162">Related Sections</span></span>  
 <span data-ttu-id="31fbe-163">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="31fbe-163">For more information:</span></span>  
  
-   [<span data-ttu-id="31fbe-164">Types référence</span><span class="sxs-lookup"><span data-stu-id="31fbe-164">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="31fbe-165">Types valeur</span><span class="sxs-lookup"><span data-stu-id="31fbe-165">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="31fbe-166">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="31fbe-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="31fbe-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31fbe-167">See Also</span></span>  
 [<span data-ttu-id="31fbe-168">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="31fbe-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

