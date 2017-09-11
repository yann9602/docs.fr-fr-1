---
title: "in (modificateur générique) (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
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
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: 663fa75a7e214ed97efb45dda2c9ac298559653d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="34960-102">in (modificateur générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="34960-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="34960-103">Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="34960-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="34960-104">Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="34960-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="34960-105">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="34960-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="34960-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="34960-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="34960-107">La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="34960-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="34960-108">Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique s’il est utilisé uniquement comme un type d’argument de méthode et non comme un type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="34960-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="34960-109">Les paramètres `Ref` et `out` ne peuvent pas être variants.</span><span class="sxs-lookup"><span data-stu-id="34960-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="34960-110">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="34960-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="34960-111">Par exemple, comme dans le .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="34960-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="34960-112">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="34960-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="34960-113">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="34960-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34960-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="34960-114">Example</span></span>  
 <span data-ttu-id="34960-115">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="34960-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="34960-116">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="34960-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 <span data-ttu-id="34960-117">[!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="34960-117">[!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="34960-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="34960-118">Example</span></span>  
 <span data-ttu-id="34960-119">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="34960-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="34960-120">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="34960-120">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 <span data-ttu-id="34960-121">[!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="34960-121">[!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="34960-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="34960-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34960-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34960-123">See Also</span></span>  
 <span data-ttu-id="34960-124">[out](../../../csharp/language-reference/keywords/out-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="34960-124">[out](../../../csharp/language-reference/keywords/out-generic-modifier.md) </span></span>  
 <span data-ttu-id="34960-125">[Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) </span><span class="sxs-lookup"><span data-stu-id="34960-125">[Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) </span></span>  
 [<span data-ttu-id="34960-126">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="34960-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

