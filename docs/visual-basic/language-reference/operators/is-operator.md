---
title: "Is, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="5853e-102">Is, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5853e-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="5853e-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="5853e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5853e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5853e-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="5853e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5853e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="5853e-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5853e-106">Required.</span></span> <span data-ttu-id="5853e-107">N’importe quel `Boolean` valeur.</span><span class="sxs-lookup"><span data-stu-id="5853e-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="5853e-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5853e-108">Required.</span></span> <span data-ttu-id="5853e-109">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="5853e-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="5853e-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5853e-110">Required.</span></span> <span data-ttu-id="5853e-111">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="5853e-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5853e-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5853e-112">Remarks</span></span>  
 <span data-ttu-id="5853e-113">Le `Is` opérateur détermine si deux références d’objet font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="5853e-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="5853e-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="5853e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="5853e-115">Si `object1` et `object2` se rapportent à la même instance d’objet, `result` est `True`; le cas contraire, `result` est `False`.</span><span class="sxs-lookup"><span data-stu-id="5853e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="5853e-116">`Is`peut également être utilisé avec le `TypeOf` mot clé pour rendre un `TypeOf`... `Is` expression, qui teste si une variable objet est compatible avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="5853e-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5853e-117">Le `Is` clé est également utilisé dans le [sélectionnez... Cas d’instruction](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5853e-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5853e-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="5853e-118">Example</span></span>  
 <span data-ttu-id="5853e-119">L’exemple suivant utilise le `Is` opérateur pour comparer des paires de références d’objet.</span><span class="sxs-lookup"><span data-stu-id="5853e-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="5853e-120">Les résultats sont affectés à un `Boolean` valeur indiquant si les deux objets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="5853e-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="5853e-121">Comme indiqué dans l’exemple précédent, vous pouvez utiliser la `Is` pour tester les deux à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="5853e-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5853e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5853e-122">See Also</span></span>  
 [<span data-ttu-id="5853e-123">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="5853e-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="5853e-124">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="5853e-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="5853e-125">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5853e-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="5853e-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5853e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="5853e-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="5853e-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="5853e-128">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="5853e-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
