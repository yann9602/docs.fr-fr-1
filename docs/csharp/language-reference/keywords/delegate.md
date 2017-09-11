---
title: "delegate (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
dev_langs:
- CSharp
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
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
ms.openlocfilehash: 402eedd0c59b5c95e1a9b44faca66ccb4d4e04e7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="delegate-c-reference"></a><span data-ttu-id="c879a-102">delegate (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c879a-102">delegate (C# Reference)</span></span>
<span data-ttu-id="c879a-103">La déclaration d’un type délégué est semblable à une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="c879a-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="c879a-104">Elle a une valeur de retour et un nombre quelconque de paramètres de type quelconque :</span><span class="sxs-lookup"><span data-stu-id="c879a-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="c879a-105">Un `delegate` est un type référence qui peut être utilisé pour encapsuler une méthode anonyme ou nommée.</span><span class="sxs-lookup"><span data-stu-id="c879a-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="c879a-106">Les délégués sont comparables aux pointeurs fonction en C++, mais ils offrent l’avantage d’être sûrs et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="c879a-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="c879a-107">Pour les applications de délégués, consultez [Délégués](../../../csharp/programming-guide/delegates/index.md) et [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c879a-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c879a-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c879a-108">Remarks</span></span>  
 <span data-ttu-id="c879a-109">Les délégués sont la base des [événements](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="c879a-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="c879a-110">Un délégué peut être instancié en l’associant à une méthode nommée ou anonyme.</span><span class="sxs-lookup"><span data-stu-id="c879a-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="c879a-111">Pour plus d’informations, consultez [Méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) et [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c879a-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="c879a-112">Le délégué doit être instancié avec une méthode ou une expression lambda qui a un type de retour compatible et des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c879a-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="c879a-113">Pour plus d’informations sur le degré de variance autorisé dans la signature de méthode, consultez [Variance dans les délégués](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca).</span><span class="sxs-lookup"><span data-stu-id="c879a-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca).</span></span> <span data-ttu-id="c879a-114">Pour une utilisation avec des méthodes anonymes, le délégué et le code à lui associer sont déclarés ensemble.</span><span class="sxs-lookup"><span data-stu-id="c879a-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="c879a-115">Les deux façons d’instancier un délégué sont décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="c879a-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c879a-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="c879a-116">Example</span></span>  
 <span data-ttu-id="c879a-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c879a-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c879a-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c879a-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c879a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c879a-119">See Also</span></span>  
 <span data-ttu-id="c879a-120">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c879a-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c879a-122">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c879a-123">[Types référence](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-123">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="c879a-124">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-124">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="c879a-125">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-125">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="c879a-126">[Délégués avec méthodes nommées et méthodes anonymes](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="c879a-126">[Delegates with Named vs. Anonymous Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span></span>  
 [<span data-ttu-id="c879a-127">Méthodes anonymes</span><span class="sxs-lookup"><span data-stu-id="c879a-127">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)

