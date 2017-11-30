---
title: "Opérateur IsNot (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isnot
helpviewer_keywords: IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="69c2b-102">Opérateur IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69c2b-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="69c2b-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="69c2b-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69c2b-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="69c2b-105">Composants</span><span class="sxs-lookup"><span data-stu-id="69c2b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="69c2b-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="69c2b-106">Required.</span></span> <span data-ttu-id="69c2b-107">Valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="69c2b-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="69c2b-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="69c2b-108">Required.</span></span> <span data-ttu-id="69c2b-109">N’importe quel `Object` variable ou une expression.</span><span class="sxs-lookup"><span data-stu-id="69c2b-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="69c2b-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="69c2b-110">Required.</span></span> <span data-ttu-id="69c2b-111">N’importe quel `Object` variable ou une expression.</span><span class="sxs-lookup"><span data-stu-id="69c2b-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69c2b-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="69c2b-112">Remarks</span></span>  
 <span data-ttu-id="69c2b-113">Le `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="69c2b-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="69c2b-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="69c2b-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="69c2b-115">Si `object1` et `object2` se rapportent à la même instance d’objet, `result` est `False`; le cas contraire, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="69c2b-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="69c2b-116">`IsNot`est le contraire de la `Is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="69c2b-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="69c2b-117">L’avantage de `IsNot` est que vous pouvez éviter la syntaxe difficile avec `Not` et `Is`, qui peut être difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="69c2b-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="69c2b-118">Vous pouvez utiliser la `Is` et `IsNot` opérateurs pour tester des objets à liaison anticipée et liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="69c2b-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69c2b-119">Le `IsNot` opérateur ne peut pas être utilisé pour comparer des expressions retournées par la `TypeOf` opérateur.</span><span class="sxs-lookup"><span data-stu-id="69c2b-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="69c2b-120">Au lieu de cela, vous devez utiliser le `Not` et `Is` opérateurs.</span><span class="sxs-lookup"><span data-stu-id="69c2b-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69c2b-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="69c2b-121">Example</span></span>  
 <span data-ttu-id="69c2b-122">L’exemple de code suivant utilise à la fois le `Is` opérateur et la `IsNot` opérateur pour effectuer la même comparaison.</span><span class="sxs-lookup"><span data-stu-id="69c2b-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69c2b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69c2b-123">See Also</span></span>  
 [<span data-ttu-id="69c2b-124">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="69c2b-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="69c2b-125">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="69c2b-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="69c2b-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69c2b-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="69c2b-127">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="69c2b-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
