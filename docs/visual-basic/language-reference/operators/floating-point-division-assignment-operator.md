---
title: "/=, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94448856072a949582e64577287134c4b975bfec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7b67c-102">/=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b67c-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="7b67c-103">Divise la valeur d’une variable ou une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à cette variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="7b67c-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b67c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b67c-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7b67c-105">Composants</span><span class="sxs-lookup"><span data-stu-id="7b67c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="7b67c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7b67c-106">Required.</span></span> <span data-ttu-id="7b67c-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="7b67c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="7b67c-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7b67c-108">Required.</span></span> <span data-ttu-id="7b67c-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="7b67c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b67c-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b67c-110">Remarks</span></span>  
 <span data-ttu-id="7b67c-111">L’élément sur le côté gauche de la `/=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="7b67c-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7b67c-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="7b67c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="7b67c-113">Le `/=` opérateur divise d’abord la valeur de la variable ou propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="7b67c-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="7b67c-114">L’opérateur assigne ensuite le résultat à virgule flottante de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="7b67c-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="7b67c-115">Cette instruction assigne un `Double` valeur à la variable ou propriété sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="7b67c-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="7b67c-116">Si `Option Strict` est `On`, `variableorproperty` doit être un `Double`.</span><span class="sxs-lookup"><span data-stu-id="7b67c-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="7b67c-117">Si `Option Strict` est `Off`, Visual Basic exécute une conversion implicite et assigne le résultat à `variableorproperty`, avec une erreur possible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7b67c-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="7b67c-118">Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b67c-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7b67c-119">Surcharge</span><span class="sxs-lookup"><span data-stu-id="7b67c-119">Overloading</span></span>  
 <span data-ttu-id="7b67c-120">Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="7b67c-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7b67c-121">La surcharge la `/` opérateur affecte le comportement de la `/=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="7b67c-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="7b67c-122">Si votre code utilise `/=` sur une classe ou structure qui surcharge `/`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="7b67c-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7b67c-123">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7b67c-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b67c-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b67c-124">Example</span></span>  
 <span data-ttu-id="7b67c-125">L’exemple suivant utilise le `/=` opérateur pour diviser une `Integer` variable par une autre et assigner le quotient à la première variable.</span><span class="sxs-lookup"><span data-stu-id="7b67c-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b67c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b67c-126">See Also</span></span>  
 [<span data-ttu-id="7b67c-127">/, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b67c-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="7b67c-128">\\=, Opérateur</span><span class="sxs-lookup"><span data-stu-id="7b67c-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="7b67c-129">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="7b67c-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="7b67c-130">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="7b67c-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="7b67c-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b67c-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="7b67c-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="7b67c-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="7b67c-133">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b67c-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
