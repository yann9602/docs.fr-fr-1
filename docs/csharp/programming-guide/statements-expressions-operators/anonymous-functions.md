---
title: "Fonctions anonymes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="eb6a5-102">Fonctions anonymes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="eb6a5-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="eb6a5-103">Une fonction anonyme est une instruction ou expression « inline » qui peut être utilisée partout où un type délégué est attendu.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="eb6a5-104">Vous pouvez l’utiliser pour initialiser un délégué nommé ou la passer à la place d’un type délégué nommé comme paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="eb6a5-105">Il existe deux sortes de fonctions anonymes, qui sont décrites dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb6a5-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="eb6a5-106">[Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="eb6a5-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="eb6a5-107">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="eb6a5-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="eb6a5-108">Les expressions lambda peuvent être liées à des arborescences d’expression et également à des délégués.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="eb6a5-109">Évolution des délégués en C#</span><span class="sxs-lookup"><span data-stu-id="eb6a5-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="eb6a5-110">Dans C# 1.0, vous pouviez créer une instance d’un délégué en l’initialisant explicitement avec une méthode déjà définie à un autre endroit dans le code.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="eb6a5-111">C# 2.0 a introduit le concept des méthodes anonymes, qui vous permettent d’écrire des blocs d’instructions inline sans nom pouvant être exécutés dans un appel de délégué.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="eb6a5-112">C# 3.0 a introduit les expressions lambda, qui sont semblables aux méthodes anonymes d’un point de vue conceptuel, mais qui sont plus expressives et concises.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="eb6a5-113">Ces deux fonctionnalités sont désignées collectivement comme des *fonctions anonymes*.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="eb6a5-114">En général, les applications qui ciblent la version 3.5 ou une version ultérieure de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] utilisent des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="eb6a5-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="eb6a5-115">L’exemple suivant montre l’évolution de la création de délégués entre C# 1.0 et C# 3.0 :</span><span class="sxs-lookup"><span data-stu-id="eb6a5-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb6a5-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="eb6a5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb6a5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb6a5-117">See Also</span></span>  
 [<span data-ttu-id="eb6a5-118">Instructions, expressions et opérateurs</span><span class="sxs-lookup"><span data-stu-id="eb6a5-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="eb6a5-119">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="eb6a5-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="eb6a5-120">Délégués</span><span class="sxs-lookup"><span data-stu-id="eb6a5-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="eb6a5-121">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="eb6a5-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
