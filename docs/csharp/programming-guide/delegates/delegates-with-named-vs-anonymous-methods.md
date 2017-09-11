---
title: "Délégués avec méthodes nommées et méthodes anonymes (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
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
ms.openlocfilehash: f82519f42e75008fc78fe475b7e37040985a21a1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="4a305-102">Délégués avec méthodes nommées et méthodes anonymes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4a305-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="4a305-103">Un [délégué](../../../csharp/language-reference/keywords/delegate.md) peut être associé à une méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="4a305-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="4a305-104">Quand vous instanciez un délégué à l’aide d’une méthode nommée, la méthode est passée en tant que paramètre, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4a305-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 <span data-ttu-id="4a305-105">[!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a305-105">[!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="4a305-106">C’est ce qui s’appelle utiliser une méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="4a305-106">This is called using a named method.</span></span> <span data-ttu-id="4a305-107">Les délégués construits avec une méthode nommée peuvent encapsuler une méthode [static](../../../csharp/language-reference/keywords/static.md) ou une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="4a305-107">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="4a305-108">Les méthodes nommées représentent la seule façon d’instancier un délégué dans les versions précédentes de C#.</span><span class="sxs-lookup"><span data-stu-id="4a305-108">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="4a305-109">Toutefois, dans une situation où la création d’une méthode constitue une charge de travail non souhaitée, C# vous permet d’instancier un délégué et de spécifier immédiatement un bloc de code que le délégué traite quand il est appelé.</span><span class="sxs-lookup"><span data-stu-id="4a305-109">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="4a305-110">Le bloc peut contenir une expression lambda ou une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="4a305-110">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="4a305-111">Pour plus d’informations, consultez [Fonctions anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4a305-111">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a305-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a305-112">Remarks</span></span>  
 <span data-ttu-id="4a305-113">La méthode que vous passez en tant que paramètre de délégué doit avoir la même signature que la déclaration du délégué.</span><span class="sxs-lookup"><span data-stu-id="4a305-113">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="4a305-114">Une instance de délégué encapsule soit une méthode statique soit une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="4a305-114">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="4a305-115">Même si le délégué peut utiliser un paramètre [out](../../../csharp/language-reference/keywords/out.md), nous ne recommandons pas son utilisation avec les délégués d’événement multicast, car vous ne pouvez pas savoir quel délégué sera appelé.</span><span class="sxs-lookup"><span data-stu-id="4a305-115">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="4a305-116">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="4a305-116">Example 1</span></span>  
 <span data-ttu-id="4a305-117">L’exemple suivant est un exemple simple de déclaration et d’utilisation d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="4a305-117">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="4a305-118">Notez que le délégué, `Del`, et la méthode associée, `MultiplyNumbers`, ont la même signature</span><span class="sxs-lookup"><span data-stu-id="4a305-118">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 <span data-ttu-id="4a305-119">[!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a305-119">[!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="4a305-120">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="4a305-120">Example 2</span></span>  
 <span data-ttu-id="4a305-121">Dans l’exemple suivant, un délégué est associé à une méthode statique et à une méthode d’instance, et retourne des informations spécifiques à partir de chacune.</span><span class="sxs-lookup"><span data-stu-id="4a305-121">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 <span data-ttu-id="4a305-122">[!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a305-122">[!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a305-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a305-123">See Also</span></span>  
 <span data-ttu-id="4a305-124">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a305-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4a305-125">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a305-125">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="4a305-126">[Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="4a305-126">[Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
 <span data-ttu-id="4a305-127">[Guide pratique pour combiner des délégués (délégués multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="4a305-127">[How to: Combine Delegates (Multicast Delegates)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md) </span></span>  
 [<span data-ttu-id="4a305-128">Événements</span><span class="sxs-lookup"><span data-stu-id="4a305-128">Events</span></span>](../../../csharp/programming-guide/events/index.md)

