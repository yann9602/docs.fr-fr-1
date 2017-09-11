---
title: "yield (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
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
ms.openlocfilehash: eb55fd5b1ade48316516cda83633935abbf8dcf9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="yield-c-reference"></a><span data-ttu-id="b9338-102">yield (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="b9338-102">yield (C# Reference)</span></span>
<span data-ttu-id="b9338-103">Lorsque vous utilisez le mot clé `yield` dans une instruction, vous indiquez que la méthode, l'opérateur, ou l'accesseur `get` dans lequel elle apparaît est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="b9338-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="b9338-104">L'utilisation de `yield` pour définir un itérateur rend une classe explicite supplémentaire inutile (la classe qui contient l'état d'une énumération ; pour obtenir un exemple, consultez <xref:System.Collections.Generic.IEnumerator%601>) lorsque vous implémentez les modèles <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour un type de collection personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b9338-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="b9338-105">L'exemple suivant montre les deux formulaires de l'instruction `yield`.</span><span class="sxs-lookup"><span data-stu-id="b9338-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9338-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9338-106">Remarks</span></span>  
 <span data-ttu-id="b9338-107">Utilisez une instruction `yield return` pour retourner chaque élément un par un.</span><span class="sxs-lookup"><span data-stu-id="b9338-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="b9338-108">Vous consommez une méthode Iterator à l’aide d’une instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="b9338-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="b9338-109">Chaque itération de la boucle `foreach` appelle la méthode Iterator.</span><span class="sxs-lookup"><span data-stu-id="b9338-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="b9338-110">Lorsqu'une instruction `yield return` est atteinte dans la méthode Iterator, `expression` est retourné, et l'emplacement dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="b9338-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="b9338-111">L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.</span><span class="sxs-lookup"><span data-stu-id="b9338-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="b9338-112">Utilisez une instruction `yield break` pour terminer l'itération.</span><span class="sxs-lookup"><span data-stu-id="b9338-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="b9338-113">Pour plus d’informations sur les itérateurs, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="b9338-113">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="b9338-114">Méthodes Iterator et accesseurs get</span><span class="sxs-lookup"><span data-stu-id="b9338-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="b9338-115">La déclaration d'un itérateur doit respecter les spécifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9338-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="b9338-116">Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="b9338-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="b9338-117">La déclaration ne peut pas contenir des paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ni [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="b9338-117">The declaration can't have any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
 <span data-ttu-id="b9338-118">Le type `yield` d'un itérateur qui retourne <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> est `object`.</span><span class="sxs-lookup"><span data-stu-id="b9338-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="b9338-119">Si l'itérateur retourne <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, il doit exister une conversion implicite du type de l'expression dans l'instruction `yield return` au paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="b9338-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="b9338-120">Vous ne pouvez pas inclure une instruction `yield return` ou `yield break` dans les méthodes qui présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9338-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="b9338-121">Méthodes anonymes.</span><span class="sxs-lookup"><span data-stu-id="b9338-121">Anonymous methods.</span></span> <span data-ttu-id="b9338-122">Pour plus d’informations, consultez [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b9338-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="b9338-123">Méthodes qui contiennent des blocs unsafe.</span><span class="sxs-lookup"><span data-stu-id="b9338-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="b9338-124">Pour plus d’informations, consultez [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b9338-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="b9338-125">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="b9338-125">Exception Handling</span></span>  
 <span data-ttu-id="b9338-126">Il ne peut pas y avoir d'instruction `yield return` dans un bloc try-catch.</span><span class="sxs-lookup"><span data-stu-id="b9338-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="b9338-127">Une instruction `yield return` peut se trouver dans le bloc try d'une instruction try-finally.</span><span class="sxs-lookup"><span data-stu-id="b9338-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="b9338-128">Une instruction `yield break` peut se trouver dans un bloc try ou un bloc catch mais pas dans un bloc finally.</span><span class="sxs-lookup"><span data-stu-id="b9338-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="b9338-129">Si le corps `foreach` (en dehors de la méthode Iterator) lève une exception, un bloc `finally` de la méthode Iterator est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b9338-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="b9338-130">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="b9338-130">Technical Implementation</span></span>  
 <span data-ttu-id="b9338-131">Le code suivant retourne `IEnumerable<string>` depuis une méthode Iterator, puis itère au sein de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="b9338-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="b9338-132">L'appel à `MyIteratorMethod` n'exécute pas le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b9338-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="b9338-133">À la place, l'appel retourne `IEnumerable<string>` dans la variable `elements`.</span><span class="sxs-lookup"><span data-stu-id="b9338-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="b9338-134">Dans une itération de la boucle `foreach`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`.</span><span class="sxs-lookup"><span data-stu-id="b9338-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="b9338-135">Cet appel exécute le corps de `MyIteratorMethod` jusqu'à ce que l'instruction `yield return` suivante soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="b9338-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="b9338-136">L'expression retournée par l'instruction `yield return` détermine non seulement la valeur de la variable `element` pour la consommation par le corps de boucle mais également la propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A> des éléments, qui est `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="b9338-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="b9338-137">À chaque itération suivante de la boucle `foreach`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="b9338-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="b9338-138">La boucle `foreach` se termine lorsque à la fin de la méthode Iterator ou lorsqu'une instruction `yield break` est atteinte.</span><span class="sxs-lookup"><span data-stu-id="b9338-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9338-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9338-139">Example</span></span>  
 <span data-ttu-id="b9338-140">L'exemple suivant comprend une instruction `yield return` située dans une boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="b9338-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="b9338-141">Chaque itération du corps d'instruction `foreach` dans `Process` crée un appel à la fonction d'itérateur `Power`.</span><span class="sxs-lookup"><span data-stu-id="b9338-141">Each iteration of the `foreach` statement body in `Process` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="b9338-142">Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `yield return`, qui se produit pendant l'itération suivante de la boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="b9338-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="b9338-143">Le type de retour de la méthode Iterator est <xref:System.Collections.IEnumerable>, qui est un type interface itérateur.</span><span class="sxs-lookup"><span data-stu-id="b9338-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="b9338-144">Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.</span><span class="sxs-lookup"><span data-stu-id="b9338-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 <span data-ttu-id="b9338-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b9338-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9338-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9338-146">Example</span></span>  
 <span data-ttu-id="b9338-147">L'exemple suivant illustre un accesseur `get` qui est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="b9338-147">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="b9338-148">Dans cet exemple, chaque instruction `yield return` retourne une instance d'une classe définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b9338-148">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 <span data-ttu-id="b9338-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b9338-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b9338-150">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b9338-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9338-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9338-151">See Also</span></span>  
 <span data-ttu-id="b9338-152">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b9338-152">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b9338-153">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b9338-153">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b9338-154">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="b9338-154">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 [<span data-ttu-id="b9338-155">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="b9338-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)

