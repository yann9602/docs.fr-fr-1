---
title: "ref (référence C#)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0be0eee67b507e2a209c9caaa3eb14cc60e8a763
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ref-c-reference"></a><span data-ttu-id="3d97f-102">ref (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3d97f-102">ref (C# Reference)</span></span>

<span data-ttu-id="3d97f-103">Le mot clé `ref` indique une valeur qui est passée par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="3d97f-104">Il est utilisé dans trois contextes différents :</span><span class="sxs-lookup"><span data-stu-id="3d97f-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="3d97f-105">Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="3d97f-106">Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="3d97f-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="3d97f-107">Dans une signature de méthode, pour retourner une valeur à l’appelant par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="3d97f-108">Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="3d97f-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="3d97f-109">Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier.</span><span class="sxs-lookup"><span data-stu-id="3d97f-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="3d97f-110">Pour plus d’informations, consultez [Variables locales ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="3d97f-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="3d97f-111">Passage d’un argument par référence</span><span class="sxs-lookup"><span data-stu-id="3d97f-111">Passing an argument by reference</span></span>

<span data-ttu-id="3d97f-112">Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur.</span><span class="sxs-lookup"><span data-stu-id="3d97f-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="3d97f-113">La conséquence est que toute modification apportée à l’argument dans la méthode appelée est reflétée dans la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="3d97f-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="3d97f-114">Par exemple, si l’appelant passe une expression de variable locale ou une expression d’accès à un élément de tableau et que la méthode appelée remplace l’objet auquel fait référence le paramètre ref, la variable locale de l’appelant ou l’élément de tableau fait désormais référence au nouvel objet quand la méthode retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="3d97f-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="3d97f-115">Ne confondez pas le concept de passage par référence avec celui de types de référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="3d97f-116">Les deux concepts ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="3d97f-116">The two concepts are not the same.</span></span> <span data-ttu-id="3d97f-117">Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="3d97f-118">Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="3d97f-119">Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

<span data-ttu-id="3d97f-120">Un argument passé à un paramètre `ref` doit être initialisé avant d'être transmis.</span><span class="sxs-lookup"><span data-stu-id="3d97f-120">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="3d97f-121">Cette obligation diffère des paramètres [out](out.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.</span><span class="sxs-lookup"><span data-stu-id="3d97f-121">This differs from [out](out.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="3d97f-122">Les membres d'une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref` et `out`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-122">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="3d97f-123">Une erreur de compilation se produit si la seule différence entre deux membres d'un type est que l'un d'eux a un paramètre `ref`et l'autre un paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="3d97f-124">Le code suivant, par exemple, ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="3d97f-124">The following code, for example, doesn't compile.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 <span data-ttu-id="3d97f-125">Cependant, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref` ou `out`, et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-125">However, methods can be overloaded when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 <span data-ttu-id="3d97f-126">Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `ref` et `out` font partie de la signature et ne correspondent pas l'un à l'autre.</span><span class="sxs-lookup"><span data-stu-id="3d97f-126">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="3d97f-127">Les propriétés ne sont pas des variables.</span><span class="sxs-lookup"><span data-stu-id="3d97f-127">Properties are not variables.</span></span> <span data-ttu-id="3d97f-128">Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="3d97f-129">Pour plus d’informations sur la manière de passer des tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="3d97f-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="3d97f-130">Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="3d97f-130">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="3d97f-131">Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="3d97f-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="3d97f-132">Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="3d97f-133">Passage d’un argument par référence : exemple</span><span class="sxs-lookup"><span data-stu-id="3d97f-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="3d97f-134">Les exemples précédents passent les types valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="3d97f-135">Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="3d97f-136">Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="3d97f-137">L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="3d97f-138">Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="3d97f-139">L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

<span data-ttu-id="3d97f-140">Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3d97f-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="3d97f-141">Valeurs de retour de référence</span><span class="sxs-lookup"><span data-stu-id="3d97f-141">Reference return values</span></span>

<span data-ttu-id="3d97f-142">Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="3d97f-143">Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et ce changement est reflété dans l’état de l’objet qui contient la méthode.</span><span class="sxs-lookup"><span data-stu-id="3d97f-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="3d97f-144">Une valeur de retour de référence est définie à l’aide du mot clé `ref` :</span><span class="sxs-lookup"><span data-stu-id="3d97f-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="3d97f-145">Dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3d97f-145">In the method signature.</span></span> <span data-ttu-id="3d97f-146">Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="3d97f-147">Avant chaque instruction `return` dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="3d97f-147">Before each `return` statement in the method.</span></span> <span data-ttu-id="3d97f-148">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3d97f-148">For example:</span></span>
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

<span data-ttu-id="3d97f-149">Afin que l’appelant modifier l’état de l’objet, la référence de retourner la valeur doit être stockée dans une variable qui est explicitement définie comme un [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="3d97f-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="3d97f-150">Pour obtenir un exemple, consultez [un exemple de retours ref et de variables locales ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="3d97f-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="3d97f-151">Variables locales ref</span><span class="sxs-lookup"><span data-stu-id="3d97f-151">Ref locals</span></span>

<span data-ttu-id="3d97f-152">Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `ref return`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-152">A ref local variable is used to refer to values returned using `ref return`.</span></span>  <span data-ttu-id="3d97f-153">Une variable locale ref doit être initialisée et affectée à une valeur de retour de référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="3d97f-154">Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="3d97f-155">Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="3d97f-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="3d97f-156">Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="3d97f-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="3d97f-157">Notez que le mot clé `ref` doit être utilisé aux deux emplacements, sans quoi le compilateur génère l’erreur CS8172, « Impossible d’initialiser une variable par référence avec une valeur ».</span><span class="sxs-lookup"><span data-stu-id="3d97f-157">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="3d97f-158">Exemple de retours ref et de variables locales ref</span><span class="sxs-lookup"><span data-stu-id="3d97f-158">A ref returns and ref locals example</span></span>

<span data-ttu-id="3d97f-159">L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-159">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="3d97f-160">Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-160">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="3d97f-161">Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="3d97f-161">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

<span data-ttu-id="3d97f-162">Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3d97f-162">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a><span data-ttu-id="3d97f-163">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3d97f-163">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d97f-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d97f-164">See Also</span></span>  
 [<span data-ttu-id="3d97f-165">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3d97f-165">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3d97f-166">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3d97f-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d97f-167">Passage de paramètres</span><span class="sxs-lookup"><span data-stu-id="3d97f-167">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="3d97f-168">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="3d97f-168">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="3d97f-169">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3d97f-169">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
