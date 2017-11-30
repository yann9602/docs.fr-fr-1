---
title: "*=, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="27adb-102">*=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27adb-102">*= Operator (Visual Basic)</span></span>
<span data-ttu-id="27adb-103">Multiplie la valeur d’une variable ou une propriété par la valeur d’une expression et assigne le résultat à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="27adb-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27adb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27adb-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="27adb-105">Composants</span><span class="sxs-lookup"><span data-stu-id="27adb-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="27adb-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="27adb-106">Required.</span></span> <span data-ttu-id="27adb-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="27adb-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="27adb-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="27adb-108">Required.</span></span> <span data-ttu-id="27adb-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="27adb-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27adb-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="27adb-110">Remarks</span></span>  
 <span data-ttu-id="27adb-111">L’élément sur le côté gauche de la `*=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="27adb-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="27adb-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="27adb-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="27adb-113">Le `*=` opérateur multiplie tout d’abord la valeur de l’expression (sur le côté droit de l’opérateur) par la valeur de la variable ou propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="27adb-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="27adb-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="27adb-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="27adb-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="27adb-115">Overloading</span></span>  
 <span data-ttu-id="27adb-116">Le [* opérateur](../../../visual-basic/language-reference/operators/multiplication-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="27adb-116">The [* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="27adb-117">La surcharge la `*` opérateur affecte le comportement de la `*=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="27adb-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="27adb-118">Si votre code utilise `*=` sur une classe ou structure qui surcharge `*`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="27adb-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="27adb-119">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="27adb-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27adb-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="27adb-120">Example</span></span>  
 <span data-ttu-id="27adb-121">L’exemple suivant utilise le `*=` opérateur multiplier un `Integer` variable par une autre et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="27adb-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="27adb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27adb-122">See Also</span></span>  
 [<span data-ttu-id="27adb-123">* (opérateur)</span><span class="sxs-lookup"><span data-stu-id="27adb-123">* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [<span data-ttu-id="27adb-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="27adb-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="27adb-125">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="27adb-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="27adb-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27adb-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="27adb-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="27adb-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="27adb-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="27adb-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
