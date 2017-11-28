---
title: "out, modificateur de paramètre (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="4975b-102">out, modificateur de paramètre (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4975b-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="4975b-103">Le mot clé `out` entraîne le passage des arguments par référence.</span><span class="sxs-lookup"><span data-stu-id="4975b-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="4975b-104">Il est similaire au mot clé [ref](../../../csharp/language-reference/keywords/ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée.</span><span class="sxs-lookup"><span data-stu-id="4975b-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="4975b-105">Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="4975b-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="4975b-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4975b-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="4975b-107">Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant.</span><span class="sxs-lookup"><span data-stu-id="4975b-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="4975b-108">Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="4975b-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="4975b-109">Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4975b-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="4975b-110">Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4975b-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="4975b-111">Bien que les mots clés `ref` et `out` entraînent un comportement différent lors de l'exécution, ils ne sont pas considérés comme partie de la signature de la méthode au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="4975b-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="4975b-112">Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l'une d'elles accepte un argument`ref` et l'autre un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="4975b-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="4975b-113">Le code suivant, par exemple, ne se compilera pas :</span><span class="sxs-lookup"><span data-stu-id="4975b-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="4975b-114">Toutefois, la surcharge est autorisée si une méthode prend un argument `ref` ou `out` et que l’autre méthode n’utilise ni l’un ni l’autre, comme suit :</span><span class="sxs-lookup"><span data-stu-id="4975b-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="4975b-115">Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.</span><span class="sxs-lookup"><span data-stu-id="4975b-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="4975b-116">Pour plus d’informations sur le passage de tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="4975b-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="4975b-117">Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="4975b-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="4975b-118">Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="4975b-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="4975b-119">Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="4975b-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="4975b-120">Déclaration d’arguments `out`</span><span class="sxs-lookup"><span data-stu-id="4975b-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="4975b-121">La déclaration d’une méthode avec des arguments `out` est utile lorsque vous souhaitez qu’une méthode retourne plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="4975b-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="4975b-122">L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4975b-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="4975b-123">Notez que le troisième argument reçoit la valeur null.</span><span class="sxs-lookup"><span data-stu-id="4975b-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="4975b-124">Cela permet aux méthodes de retourner des valeurs le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="4975b-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="4975b-125">Le [modèle Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) consiste à retourner une valeur `bool` qui indique si une opération a réussi ou échoué et à retourner le résultat de l’opération dans un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="4975b-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="4975b-126">Un certain nombre de méthodes d’analyse, notamment la méthode [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), utilisent ce modèle.</span><span class="sxs-lookup"><span data-stu-id="4975b-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="4975b-127">Appel d’une méthode avec un argument `out`</span><span class="sxs-lookup"><span data-stu-id="4975b-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="4975b-128">Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`.</span><span class="sxs-lookup"><span data-stu-id="4975b-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="4975b-129">L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.</span><span class="sxs-lookup"><span data-stu-id="4975b-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="4975b-130">À compter de C# 7, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte.</span><span class="sxs-lookup"><span data-stu-id="4975b-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="4975b-131">Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4975b-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="4975b-132">L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="4975b-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="4975b-133">Dans l’exemple précédent, la variable `number` est fortement typée en `int`.</span><span class="sxs-lookup"><span data-stu-id="4975b-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="4975b-134">Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4975b-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="4975b-135">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4975b-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4975b-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4975b-136">See Also</span></span>  
 [<span data-ttu-id="4975b-137">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4975b-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4975b-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4975b-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4975b-139">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4975b-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4975b-140">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="4975b-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
