---
title: "-=, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="bf6e3-102">-=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf6e3-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="bf6e3-103">Soustrait la valeur d’une expression de la valeur d’une variable ou propriété et assigne le résultat à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6e3-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="bf6e3-105">Composants</span><span class="sxs-lookup"><span data-stu-id="bf6e3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="bf6e3-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-106">Required.</span></span> <span data-ttu-id="bf6e3-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="bf6e3-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-108">Required.</span></span> <span data-ttu-id="bf6e3-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf6e3-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bf6e3-110">Remarks</span></span>  
 <span data-ttu-id="bf6e3-111">L’élément sur le côté gauche de la `-=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bf6e3-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bf6e3-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bf6e3-113">Le `-=` opérateur soustrait tout d’abord la valeur de l’expression (sur le côté droit de l’opérateur) à partir de la valeur de la variable ou propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="bf6e3-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="bf6e3-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bf6e3-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="bf6e3-115">Overloading</span></span>  
 <span data-ttu-id="bf6e3-116">Le [-, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bf6e3-117">La surcharge la `-` opérateur affecte le comportement de la `-=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="bf6e3-118">Si votre code utilise `-=` sur une classe ou structure qui surcharge `-`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bf6e3-119">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bf6e3-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf6e3-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf6e3-120">Example</span></span>  
 <span data-ttu-id="bf6e3-121">L’exemple suivant utilise le `-=` opérateur pour soustraire un `Integer` variable d’une autre et assigner le résultat à la dernière variable.</span><span class="sxs-lookup"><span data-stu-id="bf6e3-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf6e3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf6e3-122">See Also</span></span>  
 [<span data-ttu-id="bf6e3-123">-, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf6e3-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [<span data-ttu-id="bf6e3-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="bf6e3-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="bf6e3-125">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="bf6e3-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="bf6e3-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf6e3-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="bf6e3-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="bf6e3-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="bf6e3-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="bf6e3-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
