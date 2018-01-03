---
title: "Out (modificateur générique) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="4d30d-102">Out (modificateur générique) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d30d-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="4d30d-103">Paramètres de type générique, la `Out` (mot clé) Spécifie que le type est covariant.</span><span class="sxs-lookup"><span data-stu-id="4d30d-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d30d-104">Notes</span><span class="sxs-lookup"><span data-stu-id="4d30d-104">Remarks</span></span>  
 <span data-ttu-id="4d30d-105">La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="4d30d-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="4d30d-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="4d30d-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="4d30d-107">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d30d-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4d30d-108">Règles</span><span class="sxs-lookup"><span data-stu-id="4d30d-108">Rules</span></span>  
 <span data-ttu-id="4d30d-109">Vous pouvez utiliser le mot clé `Out` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="4d30d-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="4d30d-110">Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d30d-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="4d30d-111">Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="4d30d-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d30d-112">Il existe une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="4d30d-112">There is one exception to this rule.</span></span> <span data-ttu-id="4d30d-113">Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué.</span><span class="sxs-lookup"><span data-stu-id="4d30d-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="4d30d-114">Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4d30d-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="4d30d-115">Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="4d30d-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="4d30d-116">Dans un délégué générique, un paramètre de type peut être déclaré covariant s’il est utilisé uniquement comme un type de retour de méthode et pas utilisé pour les arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="4d30d-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="4d30d-117">La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="4d30d-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="4d30d-118">En Visual Basic, vous ne pouvez pas déclarer des événements des interfaces covariants sans spécifier le type délégué.</span><span class="sxs-lookup"><span data-stu-id="4d30d-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="4d30d-119">En outre, les interfaces covariants ne peut pas avoir de classes, d’enums ou de structures imbriqués, mais ont des interfaces imbriquées.</span><span class="sxs-lookup"><span data-stu-id="4d30d-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4d30d-120">Comportement</span><span class="sxs-lookup"><span data-stu-id="4d30d-120">Behavior</span></span>  
 <span data-ttu-id="4d30d-121">Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="4d30d-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="4d30d-122">Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerabe(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.</span><span class="sxs-lookup"><span data-stu-id="4d30d-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="4d30d-123">Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.</span><span class="sxs-lookup"><span data-stu-id="4d30d-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d30d-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d30d-124">Example</span></span>  
 <span data-ttu-id="4d30d-125">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante.</span><span class="sxs-lookup"><span data-stu-id="4d30d-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="4d30d-126">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.</span><span class="sxs-lookup"><span data-stu-id="4d30d-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4d30d-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d30d-127">Example</span></span>  
 <span data-ttu-id="4d30d-128">L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant.</span><span class="sxs-lookup"><span data-stu-id="4d30d-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="4d30d-129">Il montre également comment vous pouvez utiliser la conversion implicite pour les types délégués.</span><span class="sxs-lookup"><span data-stu-id="4d30d-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4d30d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d30d-130">See Also</span></span>  
 [<span data-ttu-id="4d30d-131">Variance dans les interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="4d30d-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="4d30d-132">In</span><span class="sxs-lookup"><span data-stu-id="4d30d-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
