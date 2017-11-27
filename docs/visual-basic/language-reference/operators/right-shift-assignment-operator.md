---
title: "&gt;&gt;=, Opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="e7fad-102">&gt;&gt;=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7fad-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="e7fad-103">Effectue un décalage arithmétique vers la droite de la valeur d’une variable ou propriété et assigne le résultat à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="e7fad-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7fad-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="e7fad-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e7fad-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e7fad-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e7fad-106">Required.</span></span> <span data-ttu-id="e7fad-107">Variable ou propriété d’un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="e7fad-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="e7fad-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e7fad-108">Required.</span></span> <span data-ttu-id="e7fad-109">Expression numérique d’un type de données qui s’étend à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e7fad-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7fad-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7fad-110">Remarks</span></span>  
 <span data-ttu-id="e7fad-111">L’élément sur le côté gauche de la `>>=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="e7fad-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e7fad-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e7fad-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e7fad-113">Le `>>=` opérateur effectue tout d’abord un décalage arithmétique vers la droite de la valeur de la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="e7fad-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="e7fad-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="e7fad-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="e7fad-115">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="e7fad-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="e7fad-116">Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position de bit plus à droite sont ignorés, et le bit le plus à gauche est propagé vers les positions de bit libérées à gauche.</span><span class="sxs-lookup"><span data-stu-id="e7fad-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="e7fad-117">Cela signifie que si `variableorproperty` a une valeur négative, les positions libérées sont définies à un.</span><span class="sxs-lookup"><span data-stu-id="e7fad-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="e7fad-118">Si `variableorproperty` est positif, ou si son type de données est un type non signé, les positions libérées sont définies à zéro.</span><span class="sxs-lookup"><span data-stu-id="e7fad-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e7fad-119">Surcharge</span><span class="sxs-lookup"><span data-stu-id="e7fad-119">Overloading</span></span>  
 <span data-ttu-id="e7fad-120">Le [>> opérateur](../../../visual-basic/language-reference/operators/right-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="e7fad-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e7fad-121">La surcharge la `>>` opérateur affecte le comportement de la `>>=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="e7fad-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="e7fad-122">Si votre code utilise `>>=` sur une classe ou structure qui surcharge `>>`, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="e7fad-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e7fad-123">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e7fad-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7fad-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7fad-124">Example</span></span>  
 <span data-ttu-id="e7fad-125">L’exemple suivant utilise le `>>=` opérateur pour décaler le modèle binaire d’une `Integer` variable vers la droite de la durée spécifiée et assigner le résultat à la variable.</span><span class="sxs-lookup"><span data-stu-id="e7fad-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e7fad-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7fad-126">See Also</span></span>  
 [<span data-ttu-id="e7fad-127">>> (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e7fad-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="e7fad-128">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="e7fad-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="e7fad-129">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="e7fad-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="e7fad-130">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7fad-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e7fad-131">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="e7fad-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e7fad-132">Instructions</span><span class="sxs-lookup"><span data-stu-id="e7fad-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
