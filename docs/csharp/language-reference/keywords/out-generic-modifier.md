---
title: "out (modificateur générique) (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5c63fe2229d4b7190397d3ba98fa150c84a12fb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="c2b23-102">out (modificateur générique) (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c2b23-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="c2b23-103">Pour les paramètres de type générique, le mot clé `out` spécifie que le paramètre de type est covariant.</span><span class="sxs-lookup"><span data-stu-id="c2b23-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="c2b23-104">Vous pouvez utiliser le mot clé `out` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="c2b23-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="c2b23-105">La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="c2b23-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="c2b23-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="c2b23-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="c2b23-107">La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="c2b23-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="c2b23-108">Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="c2b23-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="c2b23-109">Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerabe(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.</span><span class="sxs-lookup"><span data-stu-id="c2b23-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="c2b23-110">Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.</span><span class="sxs-lookup"><span data-stu-id="c2b23-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="c2b23-111">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2b23-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b23-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2b23-112">Example</span></span>  
 <span data-ttu-id="c2b23-113">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante.</span><span class="sxs-lookup"><span data-stu-id="c2b23-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="c2b23-114">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.</span><span class="sxs-lookup"><span data-stu-id="c2b23-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="c2b23-115">Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2b23-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="c2b23-116">Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="c2b23-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2b23-117">Il existe une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="c2b23-117">There is one exception to this rule.</span></span> <span data-ttu-id="c2b23-118">Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué.</span><span class="sxs-lookup"><span data-stu-id="c2b23-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="c2b23-119">Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c2b23-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="c2b23-120">Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="c2b23-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b23-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2b23-121">Example</span></span>  
 <span data-ttu-id="c2b23-122">L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant.</span><span class="sxs-lookup"><span data-stu-id="c2b23-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="c2b23-123">Il montre également comment convertir implicitement des types délégués.</span><span class="sxs-lookup"><span data-stu-id="c2b23-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="c2b23-124">Dans un délégué générique, un type peut être déclaré comme étant covariant s’il est utilisé uniquement comme type de retour des méthodes, mais pas pour des arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="c2b23-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2b23-125">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c2b23-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2b23-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2b23-126">See Also</span></span>  
 [<span data-ttu-id="c2b23-127">Variance dans les interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="c2b23-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="c2b23-128">in</span><span class="sxs-lookup"><span data-stu-id="c2b23-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="c2b23-129">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="c2b23-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
