---
title: "=, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
dev_langs:
- VB
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 46dc9e6018cf2ae71f1fc6dc2b8f19c2f0aadb62
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="044c9-102">=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="044c9-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="044c9-103">Assigne une valeur à une variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="044c9-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="044c9-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="044c9-105">Composants</span><span class="sxs-lookup"><span data-stu-id="044c9-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="044c9-106">N’importe quelle variable accessible en écriture ou n’importe quelle propriété.</span><span class="sxs-lookup"><span data-stu-id="044c9-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="044c9-107">N’importe quel littéral, une constante ou une expression.</span><span class="sxs-lookup"><span data-stu-id="044c9-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="044c9-108">Notes</span><span class="sxs-lookup"><span data-stu-id="044c9-108">Remarks</span></span>  
 <span data-ttu-id="044c9-109">L’élément sur le côté gauche du signe égal (`=`) peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="044c9-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="044c9-110">La variable ou la propriété ne peut pas être [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="044c9-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="044c9-111">Le `=` opérateur assigne la valeur située à droite vers la variable ou propriété du côté gauche.</span><span class="sxs-lookup"><span data-stu-id="044c9-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="044c9-112">Le `=` opérateur est également utilisé comme opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="044c9-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="044c9-113">Pour plus d’informations, consultez [opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="044c9-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="044c9-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="044c9-114">Overloading</span></span>  
 <span data-ttu-id="044c9-115">Le `=` opérateur peut être surchargée uniquement comme un opérateur de comparaison relationnel et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="044c9-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="044c9-116">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="044c9-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="044c9-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="044c9-117">Example</span></span>  
 <span data-ttu-id="044c9-118">L’exemple suivant illustre l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="044c9-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="044c9-119">La valeur située à droite est assignée à la variable sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="044c9-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 <span data-ttu-id="044c9-120">[!code-vb[VbVbalrOperators&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="044c9-120">[!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044c9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="044c9-121">See Also</span></span>  
 <span data-ttu-id="044c9-122">[< = (Opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-122">[&= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-123"> [* =, Opérateur](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-123"> [*= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-124"> [+=, Opérateur](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-124"> [+= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-125"> [-=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-125"> [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-126"> [/ =, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-126"> [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-127"> [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-127"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-128"> [^ =, Opérateur](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-128"> [^= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span></span>  
<span data-ttu-id="044c9-129"> [Instructions](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="044c9-130"> [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-130"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="044c9-131"> [En lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="044c9-131"> [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) </span></span>  
<span data-ttu-id="044c9-132"> [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="044c9-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

