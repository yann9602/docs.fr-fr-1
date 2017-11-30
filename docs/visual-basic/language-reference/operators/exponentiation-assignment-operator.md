---
title: "^=, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ecc53-102">^=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecc53-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="ecc53-103">Élève la valeur d’une variable ou une propriété à la puissance d’une expression et assigne le résultat à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="ecc53-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc53-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ecc53-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ecc53-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ecc53-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ecc53-106">Required.</span></span> <span data-ttu-id="ecc53-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="ecc53-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ecc53-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ecc53-108">Required.</span></span> <span data-ttu-id="ecc53-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ecc53-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecc53-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="ecc53-110">Remarks</span></span>  
 <span data-ttu-id="ecc53-111">L’élément sur le côté gauche de la `^=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="ecc53-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ecc53-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ecc53-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ecc53-113">Le `^=` opérateur déclenche d’abord la valeur de la variable ou propriété (sur le côté gauche de l’opérateur) à la puissance de la valeur de l’expression (sur le côté droit de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="ecc53-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="ecc53-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="ecc53-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="ecc53-115">Visual Basic exécute toujours l’élévation à la puissance de la [Type de données Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ecc53-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="ecc53-116">Les opérandes de tous types sont convertis en `Double`, et le résultat est toujours `Double`.</span><span class="sxs-lookup"><span data-stu-id="ecc53-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="ecc53-117">La valeur de `expression` peut être fractionnaire, négative, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="ecc53-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ecc53-118">Surcharge</span><span class="sxs-lookup"><span data-stu-id="ecc53-118">Overloading</span></span>  
 <span data-ttu-id="ecc53-119">Le [^ opérateur](../../../visual-basic/language-reference/operators/exponentiation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="ecc53-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ecc53-120">La surcharge la `^` opérateur affecte le comportement de la `^=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="ecc53-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="ecc53-121">Si votre code utilise `^=` sur une classe ou structure qui surcharge `^`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="ecc53-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ecc53-122">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ecc53-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc53-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ecc53-123">Example</span></span>  
 <span data-ttu-id="ecc53-124">L’exemple suivant utilise le `^=` d’augmenter la valeur d’un opérateur `Integer` variable à la puissance d’une seconde variable et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="ecc53-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ecc53-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecc53-125">See Also</span></span>  
 [<span data-ttu-id="ecc53-126">^ (opérateur)</span><span class="sxs-lookup"><span data-stu-id="ecc53-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="ecc53-127">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="ecc53-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="ecc53-128">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="ecc53-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="ecc53-129">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecc53-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ecc53-130">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="ecc53-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="ecc53-131">Instructions</span><span class="sxs-lookup"><span data-stu-id="ecc53-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
