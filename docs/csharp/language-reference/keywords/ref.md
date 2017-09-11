---
title: "ref (référence C#)"
ms.date: 2017-05-30
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
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
ms.openlocfilehash: 003125ca6218d42a919d8bb592b5454a7cb387c7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ref-c-reference"></a><span data-ttu-id="b1b7e-102">ref (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b1b7e-102">ref (C# Reference)</span></span>

<span data-ttu-id="b1b7e-103">Le mot clé `ref` indique une valeur qui est passée par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="b1b7e-104">Il est utilisé dans trois contextes différents :</span><span class="sxs-lookup"><span data-stu-id="b1b7e-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="b1b7e-105">Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="b1b7e-106">Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="b1b7e-107">Dans une signature de méthode, pour retourner une valeur à l’appelant par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="b1b7e-108">Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="b1b7e-109">Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="b1b7e-110">Pour plus d’informations, consultez [Variables locales ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="b1b7e-111">Passage d’un argument par référence</span><span class="sxs-lookup"><span data-stu-id="b1b7e-111">Passing an argument by reference</span></span>

<span data-ttu-id="b1b7e-112">Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="b1b7e-113">La conséquence est que toute modification apportée à l’argument dans la méthode appelée est reflétée dans la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="b1b7e-114">Par exemple, si l’appelant passe une expression de variable locale ou une expression d’accès à un élément de tableau et que la méthode appelée remplace l’objet auquel fait référence le paramètre ref, la variable locale de l’appelant ou l’élément de tableau fait désormais référence au nouvel objet quand la méthode retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="b1b7e-115">Ne confondez pas le concept de passage par référence avec celui de types de référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="b1b7e-116">Les deux concepts ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-116">The two concepts are not the same.</span></span> <span data-ttu-id="b1b7e-117">Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="b1b7e-118">Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="b1b7e-119">Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

<span data-ttu-id="b1b7e-120">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-120">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]</span></span>

<span data-ttu-id="b1b7e-121">Un argument passé à un paramètre `ref` doit être initialisé avant d'être transmis.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-121">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="b1b7e-122">Cette obligation diffère des paramètres [out](out.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-122">This differs from [out](out.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="b1b7e-123">Les membres d'une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref` et `out`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-123">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="b1b7e-124">Une erreur de compilation se produit si la seule différence entre deux membres d'un type est que l'un d'eux a un paramètre `ref`et l'autre un paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-124">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="b1b7e-125">Le code suivant, par exemple, ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-125">The following code, for example, doesn't compile.</span></span>  
  
 <span data-ttu-id="b1b7e-126">[!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-126">[!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]</span></span>
  
 <span data-ttu-id="b1b7e-127">Cependant, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref` ou `out`, et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-127">However, methods can be overloaded when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
 <span data-ttu-id="b1b7e-128">[!code-cs[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-128">[!code-cs[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]</span></span>
  
 <span data-ttu-id="b1b7e-129">Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `ref` et `out` font partie de la signature et ne correspondent pas l'un à l'autre.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-129">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="b1b7e-130">Les propriétés ne sont pas des variables.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-130">Properties are not variables.</span></span> <span data-ttu-id="b1b7e-131">Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="b1b7e-132">Pour plus d’informations sur la manière de passer des tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-132">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="b1b7e-133">Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="b1b7e-133">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="b1b7e-134">Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-134">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="b1b7e-135">Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-135">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="b1b7e-136">Passage d’un argument par référence : exemple</span><span class="sxs-lookup"><span data-stu-id="b1b7e-136">Passing an argument by reference: An example</span></span>

<span data-ttu-id="b1b7e-137">Les exemples précédents passent les types valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-137">The previous examples pass value types by reference.</span></span> <span data-ttu-id="b1b7e-138">Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-138">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="b1b7e-139">Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-139">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="b1b7e-140">L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-140">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="b1b7e-141">Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-141">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="b1b7e-142">L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-142">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
 <span data-ttu-id="b1b7e-143">[!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-143">[!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]</span></span>  

<span data-ttu-id="b1b7e-144">Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-144">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="b1b7e-145">Valeurs de retour de référence</span><span class="sxs-lookup"><span data-stu-id="b1b7e-145">Reference return values</span></span>

<span data-ttu-id="b1b7e-146">Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-146">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="b1b7e-147">Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et ce changement est reflété dans l’état de l’objet qui contient la méthode.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-147">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="b1b7e-148">Une valeur de retour de référence est définie à l’aide du mot clé `ref` :</span><span class="sxs-lookup"><span data-stu-id="b1b7e-148">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="b1b7e-149">Dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-149">In the method signature.</span></span> <span data-ttu-id="b1b7e-150">Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-150">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="b1b7e-151">Avant chaque instruction `return` dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-151">Before each `return` statement in the method.</span></span> <span data-ttu-id="b1b7e-152">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b1b7e-152">For example:</span></span>
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

<span data-ttu-id="b1b7e-153">Pour que l’appelant modifie l’état d’un objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="b1b7e-153">In order for the caller to modify the an object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="b1b7e-154">Pour obtenir un exemple, consultez [un exemple de retours ref et de variables locales ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="b1b7e-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="b1b7e-155">Variables locales ref</span><span class="sxs-lookup"><span data-stu-id="b1b7e-155">Ref locals</span></span>

<span data-ttu-id="b1b7e-156">Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `ref return`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-156">A ref local variable is used to refer to values returned using `ref return`.</span></span>  <span data-ttu-id="b1b7e-157">Une variable locale ref doit être initialisée et affectée à une valeur de retour de référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-157">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="b1b7e-158">Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-158">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="b1b7e-159">Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-159">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="b1b7e-160">Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="b1b7e-160">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="b1b7e-161">Notez que le mot clé `ref` doit être utilisé aux deux emplacements, sans quoi le compilateur génère l’erreur CS8172, « Impossible d’initialiser une variable par référence avec une valeur ».</span><span class="sxs-lookup"><span data-stu-id="b1b7e-161">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="b1b7e-162">Exemple de retours ref et de variables locales ref</span><span class="sxs-lookup"><span data-stu-id="b1b7e-162">A ref returns and ref locals example</span></span>

<span data-ttu-id="b1b7e-163">L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-163">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="b1b7e-164">Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-164">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="b1b7e-165">Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-165">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

<span data-ttu-id="b1b7e-166">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-166">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]</span></span>  

<span data-ttu-id="b1b7e-167">Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b1b7e-167">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

<span data-ttu-id="b1b7e-168">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="b1b7e-168">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="b1b7e-169">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b1b7e-169">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1b7e-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1b7e-170">See Also</span></span>  
 <span data-ttu-id="b1b7e-171">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1b7e-171">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b1b7e-172">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1b7e-172">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b1b7e-173">[Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="b1b7e-173">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 <span data-ttu-id="b1b7e-174">[Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="b1b7e-174">[Method Parameters](../../../csharp/language-reference/keywords/method-parameters.md) </span></span>  
 [<span data-ttu-id="b1b7e-175">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b1b7e-175">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

