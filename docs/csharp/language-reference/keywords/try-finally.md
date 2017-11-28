---
title: "try-finally (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="ed3f6-102">try-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ed3f6-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="ed3f6-103">En utilisant un bloc `finally`, vous pouvez nettoyer toutes les ressources allouées dans un bloc [try](../../../csharp/language-reference/keywords/try-catch.md) et vous pouvez exécuter du code même si une exception se produit dans le bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="ed3f6-104">En règle générale, les instructions d’un bloc `finally` s’exécutent lorsque le contrôle quitte une instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="ed3f6-105">Le transfert de contrôle peut se produire suite à une exécution normale, à l’exécution d’une instruction `break`, `continue`, `goto` ou `return`, ou à la propagation d’une exception hors de l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="ed3f6-106">Dans une exception gérée, le bloc `finally` associé est assuré d’être exécuté.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="ed3f6-107">Toutefois, si l’exception n’est pas gérée, l’exécution du bloc `finally` dépend de la manière dont l’opération de déroulement d’exception est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="ed3f6-108">Ceci, à son tour, dépend du paramétrage de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="ed3f6-109">En général, lorsqu’une exception non gérée met fin à une application, que le bloc `finally` soit exécuté ou non n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="ed3f6-110">Toutefois, si vous avez des instructions dans un bloc `finally` qui doivent être exécutées même dans cette situation, une solution consiste à ajouter un bloc `catch` à l’instruction `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="ed3f6-111">Ou bien, vous pouvez intercepter l’exception qui peut être levée dans le bloc `try` d’une instruction `try`-`finally` plus haut dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="ed3f6-112">Autrement dit, vous pouvez intercepter l’exception dans la méthode qui appelle la méthode contenant l’instruction `try`-`finally`, ou dans la méthode qui appelle cette méthode, ou dans n’importe quelle méthode figurant dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="ed3f6-113">Si l’exception n’est pas interceptée, l’exécution du bloc `finally` varie selon que le système d’exploitation choisit de déclencher une opération de déroulement d’exception.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed3f6-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed3f6-114">Example</span></span>  
 <span data-ttu-id="ed3f6-115">Dans l’exemple suivant, une instruction de conversion non valide provoque une exception `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="ed3f6-116">L’exception n’est pas gérée.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="ed3f6-117">Dans l’exemple suivant, une exception issue de la méthode `TryCast` est interceptée dans une méthode plus loin dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="ed3f6-118">Pour plus d’informations sur `finally`, consultez [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="ed3f6-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="ed3f6-119">C# contient également l’[instruction using](../../../csharp/language-reference/keywords/using-statement.md), qui fournit des fonctionnalités similaires pour les objets <xref:System.IDisposable> dans une syntaxe pratique.</span><span class="sxs-lookup"><span data-stu-id="ed3f6-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ed3f6-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ed3f6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ed3f6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed3f6-121">See Also</span></span>  
 [<span data-ttu-id="ed3f6-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ed3f6-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ed3f6-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ed3f6-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ed3f6-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="ed3f6-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ed3f6-125">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="ed3f6-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="ed3f6-126">Instructions de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="ed3f6-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="ed3f6-127">throw</span><span class="sxs-lookup"><span data-stu-id="ed3f6-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="ed3f6-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="ed3f6-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="ed3f6-129">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="ed3f6-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
