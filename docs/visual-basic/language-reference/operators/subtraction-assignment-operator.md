---
title: "-=, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
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
ms.openlocfilehash: 694033ec89e32b5fdba4092bd60292af536f58dd
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="11a85-102">-=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11a85-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="11a85-103">Soustrait la valeur d’une expression de la valeur d’une variable ou propriété et assigne le résultat à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="11a85-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11a85-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="11a85-105">Composants</span><span class="sxs-lookup"><span data-stu-id="11a85-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="11a85-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="11a85-106">Required.</span></span> <span data-ttu-id="11a85-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="11a85-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="11a85-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="11a85-108">Required.</span></span> <span data-ttu-id="11a85-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="11a85-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11a85-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="11a85-110">Remarks</span></span>  
 <span data-ttu-id="11a85-111">L’élément sur le côté gauche de la `-=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="11a85-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="11a85-112">La variable ou la propriété ne peut pas être [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="11a85-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="11a85-113">Le `-=` opérateur tout d’abord soustrait la valeur de l’expression (sur le côté droit de l’opérateur) à partir de la valeur de la variable ou la propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="11a85-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="11a85-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="11a85-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="11a85-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="11a85-115">Overloading</span></span>  
 <span data-ttu-id="11a85-116">Le [-, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="11a85-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="11a85-117">La surcharge la `-` opérateur affecte le comportement de la `-=` (opérateur).</span><span class="sxs-lookup"><span data-stu-id="11a85-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="11a85-118">Si votre code utilise `-=` sur une classe ou structure qui surcharge `-`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="11a85-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="11a85-119">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="11a85-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11a85-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="11a85-120">Example</span></span>  
 <span data-ttu-id="11a85-121">L’exemple suivant utilise le `-=` à soustraire un opérateur `Integer` variable d’une autre et assigner le résultat à la dernière variable.</span><span class="sxs-lookup"><span data-stu-id="11a85-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 <span data-ttu-id="11a85-122">[!code-vb[VbVbalrOperators&#11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="11a85-122">[!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a85-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11a85-123">See Also</span></span>  
 <span data-ttu-id="11a85-124">[-, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span><span class="sxs-lookup"><span data-stu-id="11a85-124">[- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span></span>  
<span data-ttu-id="11a85-125"> [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="11a85-125"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="11a85-126"> [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="11a85-126"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="11a85-127"> [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="11a85-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="11a85-128"> [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="11a85-128"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="11a85-129"> [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="11a85-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

