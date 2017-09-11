---
title: "/ =, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
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
ms.openlocfilehash: e877e98104b5c9fd679485b50a88943fac80a696
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5e6f1-102">/=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e6f1-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="5e6f1-103">Divise la valeur d’une variable ou une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à cette variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e6f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e6f1-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5e6f1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5e6f1-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="5e6f1-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-106">Required.</span></span> <span data-ttu-id="5e6f1-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="5e6f1-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-108">Required.</span></span> <span data-ttu-id="5e6f1-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e6f1-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="5e6f1-110">Remarks</span></span>  
 <span data-ttu-id="5e6f1-111">L’élément sur le côté gauche de la `/=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="5e6f1-112">La variable ou la propriété ne peut pas être [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="5e6f1-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="5e6f1-113">Le `/=` opérateur divise d’abord la valeur de la variable ou la propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="5e6f1-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="5e6f1-114">L’opérateur assigne ensuite le résultat de cette opération en virgule flottante à cette variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="5e6f1-115">Cette instruction assigne une `Double` valeur à la variable ou la propriété sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="5e6f1-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="5e6f1-117">Si `Option Strict` est `Off`, Visual Basic exécute une conversion implicite et assigne le résultat à `variableorproperty`, avec une erreur possible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="5e6f1-118">Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e6f1-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5e6f1-119">Surcharge</span><span class="sxs-lookup"><span data-stu-id="5e6f1-119">Overloading</span></span>  
 <span data-ttu-id="5e6f1-120">Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5e6f1-121">La surcharge la `/` opérateur affecte le comportement de la `/=` (opérateur).</span><span class="sxs-lookup"><span data-stu-id="5e6f1-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="5e6f1-122">Si votre code utilise `/=` sur une classe ou structure qui surcharge `/`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5e6f1-123">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5e6f1-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e6f1-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e6f1-124">Example</span></span>  
 <span data-ttu-id="5e6f1-125">L’exemple suivant utilise le `/=` opérateur pour diviser une `Integer` variable par une autre et assigner le quotient à la première variable.</span><span class="sxs-lookup"><span data-stu-id="5e6f1-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 <span data-ttu-id="5e6f1-126">[!code-vb[VbVbalrOperators&#17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e6f1-126">[!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6f1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e6f1-127">See Also</span></span>  
 <span data-ttu-id="5e6f1-128">[/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-128">[/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span></span>  
<span data-ttu-id="5e6f1-129"> [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-129"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="5e6f1-130"> [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-130"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="5e6f1-131"> [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-131"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="5e6f1-132"> [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-132"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="5e6f1-133"> [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="5e6f1-133"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="5e6f1-134"> [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="5e6f1-134"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

