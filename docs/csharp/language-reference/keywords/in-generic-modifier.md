---
title: "in (modificateur générique) (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="48d09-102">in (modificateur générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="48d09-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="48d09-103">Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="48d09-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="48d09-104">Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="48d09-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="48d09-105">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="48d09-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="48d09-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="48d09-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="48d09-107">La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="48d09-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="48d09-108">Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique s’il est utilisé uniquement comme un type d’argument de méthode et non comme un type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="48d09-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="48d09-109">Les paramètres `Ref` et `out` ne peuvent pas être variants.</span><span class="sxs-lookup"><span data-stu-id="48d09-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="48d09-110">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="48d09-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="48d09-111">Par exemple, comme dans le .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="48d09-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="48d09-112">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="48d09-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="48d09-113">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="48d09-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48d09-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="48d09-114">Example</span></span>  
 <span data-ttu-id="48d09-115">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="48d09-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="48d09-116">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="48d09-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="48d09-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="48d09-117">Example</span></span>  
 <span data-ttu-id="48d09-118">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="48d09-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="48d09-119">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="48d09-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="48d09-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="48d09-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="48d09-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48d09-121">See Also</span></span>  
 [<span data-ttu-id="48d09-122">out</span><span class="sxs-lookup"><span data-stu-id="48d09-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="48d09-123">Covariance et contravariance</span><span class="sxs-lookup"><span data-stu-id="48d09-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="48d09-124">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="48d09-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
