---
title: "out, modificateur de paramètre (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
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
ms.sourcegitcommit: 59e445ac27f07c85d9e98c5f595cf5f935f75443
ms.openlocfilehash: 9a0a488c6f444608a335cd990847774fb6fe9e3f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/31/2017

---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="d8a89-102">out, modificateur de paramètre (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d8a89-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="d8a89-103">Le mot clé `out` entraîne le passage des arguments par référence.</span><span class="sxs-lookup"><span data-stu-id="d8a89-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="d8a89-104">Il est similaire au mot clé [ref](../../../csharp/language-reference/keywords/ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée.</span><span class="sxs-lookup"><span data-stu-id="d8a89-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="d8a89-105">Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="d8a89-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d8a89-106">For example:</span></span>  
  
 <span data-ttu-id="d8a89-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="d8a89-108">Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant.</span><span class="sxs-lookup"><span data-stu-id="d8a89-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="d8a89-109">Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d8a89-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="d8a89-110">Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="d8a89-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="d8a89-111">Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d8a89-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="d8a89-112">Bien que les mots clés `ref` et `out` entraînent un comportement différent lors de l'exécution, ils ne sont pas considérés comme partie de la signature de la méthode au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d8a89-112">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="d8a89-113">Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l'une d'elles accepte un argument`ref` et l'autre un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="d8a89-114">Le code suivant, par exemple, ne se compilera pas :</span><span class="sxs-lookup"><span data-stu-id="d8a89-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="d8a89-115">Toutefois, la surcharge est autorisée si une méthode prend un argument `ref` ou `out` et que l’autre méthode n’utilise ni l’un ni l’autre, comme suit :</span><span class="sxs-lookup"><span data-stu-id="d8a89-115">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 <span data-ttu-id="d8a89-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span></span>  
  
 <span data-ttu-id="d8a89-117">Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="d8a89-118">Pour plus d’informations sur le passage de tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="d8a89-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="d8a89-119">Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :</span><span class="sxs-lookup"><span data-stu-id="d8a89-119">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="d8a89-120">Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="d8a89-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="d8a89-121">Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="d8a89-122">Déclaration d’arguments `out`</span><span class="sxs-lookup"><span data-stu-id="d8a89-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="d8a89-123">La déclaration d’une méthode avec des arguments `out` est utile lorsque vous souhaitez qu’une méthode retourne plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="d8a89-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="d8a89-124">L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="d8a89-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="d8a89-125">Notez que le troisième argument reçoit la valeur null.</span><span class="sxs-lookup"><span data-stu-id="d8a89-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="d8a89-126">Cela permet aux méthodes de retourner des valeurs le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d8a89-126">This enables methods to return values optionally.</span></span>  
  
 <span data-ttu-id="d8a89-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span></span>  

 <span data-ttu-id="d8a89-128">Le [modèle Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) consiste à retourner une valeur `bool` qui indique si une opération a réussi ou échoué et à retourner le résultat de l’opération dans un argument `out`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-128">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="d8a89-129">Un certain nombre de méthodes d’analyse, notamment la méthode [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), utilisent ce modèle.</span><span class="sxs-lookup"><span data-stu-id="d8a89-129">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="d8a89-130">Appel d’une méthode avec un argument `out`</span><span class="sxs-lookup"><span data-stu-id="d8a89-130">Calling a method with an `out` argument</span></span>

<span data-ttu-id="d8a89-131">Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-131">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="d8a89-132">L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.</span><span class="sxs-lookup"><span data-stu-id="d8a89-132">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 <span data-ttu-id="d8a89-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span></span>  

<span data-ttu-id="d8a89-134">À compter de C# 7, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte.</span><span class="sxs-lookup"><span data-stu-id="d8a89-134">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="d8a89-135">Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="d8a89-135">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="d8a89-136">L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="d8a89-136">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 <span data-ttu-id="d8a89-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span></span>  
   
<span data-ttu-id="d8a89-138">Dans l’exemple précédent, la variable `number` est fortement typée en `int`.</span><span class="sxs-lookup"><span data-stu-id="d8a89-138">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="d8a89-139">Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d8a89-139">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 <span data-ttu-id="d8a89-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span></span>  
   
## <a name="c-language-specification"></a><span data-ttu-id="d8a89-141">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d8a89-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8a89-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8a89-142">See Also</span></span>  
 <span data-ttu-id="d8a89-143">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8a89-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d8a89-144">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8a89-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d8a89-145">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8a89-145">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="d8a89-146">Paramètres de méthodes</span><span class="sxs-lookup"><span data-stu-id="d8a89-146">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

