---
title: "Méthodes anonymes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d942e0f3245f6404c896173b2c7ca6f1090a8c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="8f0f8-102">Méthodes anonymes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8f0f8-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="8f0f8-103">Dans les versions de C# antérieures à 2.0, la seule façon de déclarer un type [delegate](../../../csharp/language-reference/keywords/delegate.md) consistait à utiliser des [méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8f0f8-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="8f0f8-104">C# 2.0 a introduit les méthodes anonymes et dans C# 3.0 et ultérieur, les expressions lambda remplacent les méthodes anonymes comme meilleur moyen d’écrire du code « in line ».</span><span class="sxs-lookup"><span data-stu-id="8f0f8-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="8f0f8-105">Toutefois, les informations relatives aux méthodes anonymes figurant dans cette rubrique s’appliquent également aux expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="8f0f8-106">Il existe un cas où une méthode anonyme fournit des fonctionnalités non disponibles dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="8f0f8-107">Les méthodes anonymes vous permettent d’omettre la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="8f0f8-108">Cela signifie qu’une méthode anonyme peut être convertie en délégués avec diverses signatures.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="8f0f8-109">Cela n’est pas possible avec les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="8f0f8-110">Pour plus d’informations spécifiques aux expressions lambda, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8f0f8-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="8f0f8-111">La création de méthodes anonymes est essentiellement un moyen de passer un bloc de code comme paramètre de délégué.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="8f0f8-112">Voici deux exemples :</span><span class="sxs-lookup"><span data-stu-id="8f0f8-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="8f0f8-113">En utilisant des méthodes anonymes, vous réduisez la surcharge liée au codage dans l’instanciation de délégués, car vous n’avez pas à créer de méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="8f0f8-114">Par exemple, la spécification d’un bloc de code au lieu d’un délégué peut être utile dans une situation où la surcharge que représente la création d’une méthode ne semble pas justifiée.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="8f0f8-115">Un bon exemple pourrait être le moment où vous démarrez un nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="8f0f8-116">Cette classe crée un thread et contient également le code exécuté par le thread sans créer une méthode supplémentaire pour le délégué.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="8f0f8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="8f0f8-117">Remarks</span></span>  
 <span data-ttu-id="8f0f8-118">La portée des paramètres d’une méthode anonyme est *bloc-méthode-anonyme*.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="8f0f8-119">C’est une erreur d’avoir une instruction de saut, telle que [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), à l’intérieur du bloc de méthode anonyme si la cible est à l’extérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="8f0f8-120">C’est également une erreur d’avoir une instruction de saut, telle que `goto`, `break` ou `continue`, à l’extérieur du bloc de méthode anonyme si la cible est à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="8f0f8-121">Les variables locales et les paramètres dont la portée contient une déclaration de méthode anonyme sont appelés variables *externes* de la méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="8f0f8-122">Par exemple, dans le segment de code suivant, `n` est une variable externe :</span><span class="sxs-lookup"><span data-stu-id="8f0f8-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="8f0f8-123">Une référence à la variable externe `n` est dite *capturée* quand le délégué est créé.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="8f0f8-124">Contrairement aux variables locales, la durée de vie d’une variable capturée s’étend jusqu’à ce que les délégués qui font référence aux méthodes anonymes soient éligibles pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="8f0f8-125">Une méthode anonyme ne peut pas accéder aux paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) d’une portée externe.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-125">An anonymous method cannot access the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="8f0f8-126">Aucun code unsafe n’est accessible dans le *bloc-méthode-anonyme*.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="8f0f8-127">Les méthodes anonymes ne sont pas autorisées à gauche de l’opérateur [is](../../../csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="8f0f8-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f0f8-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f0f8-128">Example</span></span>  
 <span data-ttu-id="8f0f8-129">L’exemple suivant présente deux façons d’instancier un délégué :</span><span class="sxs-lookup"><span data-stu-id="8f0f8-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="8f0f8-130">Association du délégué à une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="8f0f8-131">Association du délégué à une méthode nommée (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="8f0f8-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="8f0f8-132">Dans chaque cas, un message s’affiche quand le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="8f0f8-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8f0f8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f0f8-133">See Also</span></span>  
 [<span data-ttu-id="8f0f8-134">Référence C#</span><span class="sxs-lookup"><span data-stu-id="8f0f8-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f0f8-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8f0f8-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f0f8-136">Délégués</span><span class="sxs-lookup"><span data-stu-id="8f0f8-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="8f0f8-137">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="8f0f8-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="8f0f8-138">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="8f0f8-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="8f0f8-139">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8f0f8-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="8f0f8-140">Délégués avec méthodes nommées et méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="8f0f8-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
