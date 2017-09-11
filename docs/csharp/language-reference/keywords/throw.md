---
title: "throw (référence C#)"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: 955f6d87614e0b452ace162e79e34aec9decad54
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="throw-c-reference"></a><span data-ttu-id="fbed1-102">throw (référence C#)</span><span class="sxs-lookup"><span data-stu-id="fbed1-102">throw (C# Reference)</span></span>
<span data-ttu-id="fbed1-103">Signale l’occurrence d’une exception pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="fbed1-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbed1-104">Notes</span><span class="sxs-lookup"><span data-stu-id="fbed1-104">Remarks</span></span>

<span data-ttu-id="fbed1-105">La syntaxe de `throw` est :</span><span class="sxs-lookup"><span data-stu-id="fbed1-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="fbed1-106">où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fbed1-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=fullName>.</span></span> <span data-ttu-id="fbed1-107">L’exemple suivant utilise l’instruction `throw` pour lever une exception @System.IndexOutOfRangeException si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="fbed1-107">The following example uses the `throw` statement to throw an @System.IndexOutOfRangeException if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

<span data-ttu-id="fbed1-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span></span>  

<span data-ttu-id="fbed1-109">Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="fbed1-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="fbed1-110">L’exemple suivant gère l’exception levée par la méthode `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="fbed1-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

<span data-ttu-id="fbed1-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span></span>  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="fbed1-112">Génération répétée d’une exception</span><span class="sxs-lookup"><span data-stu-id="fbed1-112">Re-throwing an exception</span></span>

<span data-ttu-id="fbed1-113">`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="fbed1-113">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="fbed1-114">Dans ce cas, `throw` n’accepte pas d’opérande d’exception.</span><span class="sxs-lookup"><span data-stu-id="fbed1-114">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="fbed1-115">Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="fbed1-115">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="fbed1-116">Par exemple, l’exemple suivant lève de nouveau une exception @System.NullReferenceException qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée.</span><span class="sxs-lookup"><span data-stu-id="fbed1-116">For example, the following example re-throws an @System.NullReferenceException that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

<span data-ttu-id="fbed1-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="fbed1-118">Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="fbed1-118">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="fbed1-119">Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété @System.Exception.Stacktrace, n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="fbed1-119">In this case, the stack trace of the original exception, which is available from the @System.Exception.Stacktrace property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="fbed1-120">Expression `throw`</span><span class="sxs-lookup"><span data-stu-id="fbed1-120">The `throw` expression</span></span>

<span data-ttu-id="fbed1-121">À compter de C# 7, `throw` peut être utilisé en tant qu’expression et en tant qu’instruction.</span><span class="sxs-lookup"><span data-stu-id="fbed1-121">Starting with C# 7, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="fbed1-122">Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge,</span><span class="sxs-lookup"><span data-stu-id="fbed1-122">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="fbed1-123">à savoir :</span><span class="sxs-lookup"><span data-stu-id="fbed1-123">These include:</span></span>

- <span data-ttu-id="fbed1-124">[l’opérateur conditionnel](../operators/conditional-operator.md) :</span><span class="sxs-lookup"><span data-stu-id="fbed1-124">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="fbed1-125">l’exemple suivant utilise une expression `throw` pour lever une exception @System.ArgumentException si une méthode reçoit un tableau de chaînes vide.</span><span class="sxs-lookup"><span data-stu-id="fbed1-125">The following example uses a `throw` expression to throw an @System.ArgumentException if a method is passed an empty string array.</span></span> <span data-ttu-id="fbed1-126">Avant C# 7, cette logique devait figurer dans une instruction `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="fbed1-126">Before C# 7, this logic would need to appear in an `if`/`else` statement.</span></span>

   <span data-ttu-id="fbed1-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span></span>  
  
- <span data-ttu-id="fbed1-128">[l’opérateur de fusion de Null](../operators/null-conditional-operator.md) :</span><span class="sxs-lookup"><span data-stu-id="fbed1-128">[the null-coalescing operator](../operators/null-conditional-operator.md).</span></span> <span data-ttu-id="fbed1-129">dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.</span><span class="sxs-lookup"><span data-stu-id="fbed1-129">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   <span data-ttu-id="fbed1-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span></span>  
 
- <span data-ttu-id="fbed1-131">un [lambda](../../lambda-expressions.md) ou une méthode expression-bodied :</span><span class="sxs-lookup"><span data-stu-id="fbed1-131">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="fbed1-132">l’exemple suivant illustre une méthode expression-bodied qui lève une exception @System.InvalidCastException, car une conversion vers une valeur @System.DateTime n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="fbed1-132">The following example illustrates an expression-bodied method that throws an @System.InvalidCastException because a conversion to a @System.DateTime value is not supported.</span></span>
 
   <span data-ttu-id="fbed1-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="fbed1-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span></span>  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="fbed1-134">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="fbed1-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbed1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbed1-135">See Also</span></span>  
 <span data-ttu-id="fbed1-136">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fbed1-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fbed1-138">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-138">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="fbed1-139">[Les instructions try, catch et throw en C++](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-139">[The try, catch, and throw Statements in C++](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="fbed1-140">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-140">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="fbed1-141">[Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="fbed1-141">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 [<span data-ttu-id="fbed1-142">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="fbed1-142">How to: Explicitly Throw Exceptions</span></span>](https://msdn.microsoft.com/library/xhcbs8fz)

