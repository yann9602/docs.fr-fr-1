---
title: "In (modificateur générique) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="4cdc7-102">In (modificateur générique) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cdc7-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="4cdc7-103">Pour les paramètres de type générique, le mot clé `In` spécifie que le paramètre de type est contravariant.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cdc7-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="4cdc7-104">Remarks</span></span>  
 <span data-ttu-id="4cdc7-105">La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="4cdc7-106">Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="4cdc7-107">Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="4cdc7-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4cdc7-108">Règles</span><span class="sxs-lookup"><span data-stu-id="4cdc7-108">Rules</span></span>  
 <span data-ttu-id="4cdc7-109">Vous pouvez utiliser le mot clé `In` dans les interfaces et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="4cdc7-110">Un paramètre de type peut être déclaré contravariant dans une interface générique ou un délégué si elle est utilisée uniquement en tant que type d’arguments de méthode et pas utilisé comme type de retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="4cdc7-111">`ByRef`les paramètres ne peuvent pas être covariants ou contravariants.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="4cdc7-112">Covariance et contravariance sont pris en charge pour les types référence et non pris en charge pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="4cdc7-113">En Visual Basic, vous ne pouvez pas déclarer des événements dans des interfaces contravariant sans spécifier le type délégué.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="4cdc7-114">En outre, les interfaces de contravariant ne peut pas avoir de classes, d’enums ou de structures imbriqués, mais ont des interfaces imbriquées.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4cdc7-115">Comportement</span><span class="sxs-lookup"><span data-stu-id="4cdc7-115">Behavior</span></span>  
 <span data-ttu-id="4cdc7-116">Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="4cdc7-117">Par exemple, comme dans le .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Person` hérite de `Employee`.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="4cdc7-118">Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdc7-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cdc7-119">Example</span></span>  
 <span data-ttu-id="4cdc7-120">L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="4cdc7-121">Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4cdc7-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cdc7-122">Example</span></span>  
 <span data-ttu-id="4cdc7-123">L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="4cdc7-124">Il montre également comment convertir implicitement un type délégué.</span><span class="sxs-lookup"><span data-stu-id="4cdc7-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4cdc7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cdc7-125">See Also</span></span>  
 [<span data-ttu-id="4cdc7-126">Variance dans les interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="4cdc7-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="4cdc7-127">Out</span><span class="sxs-lookup"><span data-stu-id="4cdc7-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
