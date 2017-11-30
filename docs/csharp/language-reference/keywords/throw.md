---
title: "throw (référence C#)"
ms.date: 03/02/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56bd8f8b6bfcc7c8f1eb2df6ac157e28adac331
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="throw-c-reference"></a><span data-ttu-id="e4c79-102">throw (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e4c79-102">throw (C# Reference)</span></span>
<span data-ttu-id="e4c79-103">Signale l’occurrence d’une exception pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="e4c79-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4c79-104">Notes</span><span class="sxs-lookup"><span data-stu-id="e4c79-104">Remarks</span></span>

<span data-ttu-id="e4c79-105">La syntaxe de `throw` est :</span><span class="sxs-lookup"><span data-stu-id="e4c79-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="e4c79-106">où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4c79-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e4c79-107">L’exemple suivant utilise l’instruction `throw` pour lever une exception <xref:System.IndexOutOfRangeException> si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="e4c79-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="e4c79-108">Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="e4c79-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="e4c79-109">L’exemple suivant gère l’exception levée par la méthode `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="e4c79-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="e4c79-110">Génération répétée d’une exception</span><span class="sxs-lookup"><span data-stu-id="e4c79-110">Re-throwing an exception</span></span>

<span data-ttu-id="e4c79-111">`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="e4c79-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="e4c79-112">Dans ce cas, `throw` n’accepte pas d’opérande d’exception.</span><span class="sxs-lookup"><span data-stu-id="e4c79-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="e4c79-113">Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e4c79-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="e4c79-114">Par exemple, l’exemple suivant lève de nouveau une exception <xref:System.NullReferenceException> qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée.</span><span class="sxs-lookup"><span data-stu-id="e4c79-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="e4c79-115">Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e4c79-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="e4c79-116">Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété <xref:System.Exception.StackTrace>, n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="e4c79-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="e4c79-117">Expression `throw`</span><span class="sxs-lookup"><span data-stu-id="e4c79-117">The `throw` expression</span></span>

<span data-ttu-id="e4c79-118">À compter de C# 7, `throw` peut être utilisé en tant qu’expression et en tant qu’instruction.</span><span class="sxs-lookup"><span data-stu-id="e4c79-118">Starting with C# 7, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="e4c79-119">Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e4c79-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="e4c79-120">à savoir :</span><span class="sxs-lookup"><span data-stu-id="e4c79-120">These include:</span></span>

- <span data-ttu-id="e4c79-121">[l’opérateur conditionnel](../operators/conditional-operator.md) :</span><span class="sxs-lookup"><span data-stu-id="e4c79-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="e4c79-122">l’exemple suivant utilise une expression `throw` pour lever une exception <xref:System.ArgumentException> si une méthode reçoit un tableau de chaînes vide.</span><span class="sxs-lookup"><span data-stu-id="e4c79-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="e4c79-123">Avant C# 7, cette logique devait figurer dans une instruction `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="e4c79-123">Before C# 7, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="e4c79-124">[l’opérateur de fusion de Null](../operators/null-conditional-operator.md) :</span><span class="sxs-lookup"><span data-stu-id="e4c79-124">[the null-coalescing operator](../operators/null-conditional-operator.md).</span></span> <span data-ttu-id="e4c79-125">dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.</span><span class="sxs-lookup"><span data-stu-id="e4c79-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="e4c79-126">un [lambda](../../lambda-expressions.md) ou une méthode expression-bodied :</span><span class="sxs-lookup"><span data-stu-id="e4c79-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="e4c79-127">l’exemple suivant illustre une méthode expression-bodied qui lève une exception <xref:System.InvalidCastException>, car une conversion vers une valeur <xref:System.DateTime> n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e4c79-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="e4c79-128">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e4c79-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4c79-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4c79-129">See Also</span></span>  
 [<span data-ttu-id="e4c79-130">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e4c79-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e4c79-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e4c79-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e4c79-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="e4c79-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="e4c79-133">Try, catch et throw instructions en C++</span><span class="sxs-lookup"><span data-stu-id="e4c79-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="e4c79-134">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="e4c79-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e4c79-135">Instructions de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="e4c79-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="e4c79-136">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="e4c79-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
