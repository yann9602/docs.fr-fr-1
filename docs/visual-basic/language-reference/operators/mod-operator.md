---
title: "Mod, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="fbc50-102">Mod, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbc50-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="fbc50-103">Divise deux nombres et retourne uniquement le reste.</span><span class="sxs-lookup"><span data-stu-id="fbc50-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc50-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="fbc50-105">Composants</span><span class="sxs-lookup"><span data-stu-id="fbc50-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="fbc50-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="fbc50-106">Required.</span></span> <span data-ttu-id="fbc50-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="fbc50-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="fbc50-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="fbc50-108">Required.</span></span> <span data-ttu-id="fbc50-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="fbc50-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="fbc50-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="fbc50-110">Supported Types</span></span>  
 <span data-ttu-id="fbc50-111">Tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="fbc50-111">All numeric types.</span></span> <span data-ttu-id="fbc50-112">Cela inclut les types non signés et à virgule flottante et `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fbc50-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="fbc50-113">Résultat</span><span class="sxs-lookup"><span data-stu-id="fbc50-113">Result</span></span>  
 <span data-ttu-id="fbc50-114">Le résultat est le reste après `number1` divisé par `number2`.</span><span class="sxs-lookup"><span data-stu-id="fbc50-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="fbc50-115">Par exemple, l’expression `14 Mod 4` prend la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="fbc50-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbc50-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="fbc50-116">Remarks</span></span>  
 <span data-ttu-id="fbc50-117">Si le paramètre `number1` ou `number2` est une valeur à virgule flottante, le reste à virgule flottante de la division est retourné.</span><span class="sxs-lookup"><span data-stu-id="fbc50-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="fbc50-118">Le type de données du résultat est le plus petit type de données qui peut contenir toutes les valeurs possibles qui résultent de la division avec les types de données de `number1` et `number2`.</span><span class="sxs-lookup"><span data-stu-id="fbc50-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="fbc50-119">Si `number1` ou `number2` prend la valeur de [rien](../../../visual-basic/language-reference/nothing.md), il est traité en tant que zéro.</span><span class="sxs-lookup"><span data-stu-id="fbc50-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="fbc50-120">Les opérateurs connexes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fbc50-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="fbc50-121">Le [\, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) renvoie le quotient entier d’une division.</span><span class="sxs-lookup"><span data-stu-id="fbc50-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="fbc50-122">Par exemple, l’expression `14 \ 4` renvoie la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="fbc50-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="fbc50-123">Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, y compris le reste, en tant que nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="fbc50-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="fbc50-124">Par exemple, l’expression `14 / 4` prend la valeur 3,5.</span><span class="sxs-lookup"><span data-stu-id="fbc50-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="fbc50-125">Tentative de Division par zéro</span><span class="sxs-lookup"><span data-stu-id="fbc50-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="fbc50-126">Si `number2` correspond à zéro, le comportement de la `Mod` opérateur varie selon le type de données des opérandes.</span><span class="sxs-lookup"><span data-stu-id="fbc50-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="fbc50-127">Une division intégrale lève une <xref:System.DivideByZeroException> exception.</span><span class="sxs-lookup"><span data-stu-id="fbc50-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="fbc50-128">Une division à virgule flottante retourne <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="fbc50-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="fbc50-129">Formule équivalente</span><span class="sxs-lookup"><span data-stu-id="fbc50-129">Equivalent Formula</span></span>  
 <span data-ttu-id="fbc50-130">L’expression `a Mod b` correspond à une des formules suivantes :</span><span class="sxs-lookup"><span data-stu-id="fbc50-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="fbc50-131">À virgule flottante imprécision</span><span class="sxs-lookup"><span data-stu-id="fbc50-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="fbc50-132">Lorsque vous travaillez avec des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours de représentation précise dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fbc50-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="fbc50-133">Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les `Mod` opérateur.</span><span class="sxs-lookup"><span data-stu-id="fbc50-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="fbc50-134">Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="fbc50-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fbc50-135">Surcharge</span><span class="sxs-lookup"><span data-stu-id="fbc50-135">Overloading</span></span>  
 <span data-ttu-id="fbc50-136">Le `Mod` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement.</span><span class="sxs-lookup"><span data-stu-id="fbc50-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="fbc50-137">Si votre code applique `Mod` à une instance d’une classe ou une structure qui inclut une telle surcharge, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="fbc50-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fbc50-138">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fbc50-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbc50-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbc50-139">Example</span></span>  
 <span data-ttu-id="fbc50-140">L’exemple suivant utilise le `Mod` opérateur diviser deux nombres et retourner uniquement le reste.</span><span class="sxs-lookup"><span data-stu-id="fbc50-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="fbc50-141">Si un nombre est un nombre à virgule flottante, le résultat est un nombre à virgule flottante qui représente le reste.</span><span class="sxs-lookup"><span data-stu-id="fbc50-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="fbc50-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbc50-142">Example</span></span>  
 <span data-ttu-id="fbc50-143">L’exemple suivant montre l’imprécision potentielle des opérandes à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="fbc50-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="fbc50-144">Dans la première instruction, les opérandes sont `Double`, et 0,2 représente une fraction binaire se répétant avec une valeur stockée de 0,20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="fbc50-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="fbc50-145">Dans la deuxième instruction, le littéral de type caractère `D` force les deux opérandes de `Decimal`, et 0,2 a une représentation précise.</span><span class="sxs-lookup"><span data-stu-id="fbc50-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fbc50-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbc50-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="fbc50-147">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="fbc50-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="fbc50-148">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbc50-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="fbc50-149">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="fbc50-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="fbc50-150">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="fbc50-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="fbc50-151">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbc50-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="fbc50-152">\, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbc50-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
