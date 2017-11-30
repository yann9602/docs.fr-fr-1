---
title: "^, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e54bf-102">^, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e54bf-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="e54bf-103">Élève un nombre à la puissance d’un autre nombre.</span><span class="sxs-lookup"><span data-stu-id="e54bf-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e54bf-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="e54bf-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e54bf-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="e54bf-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e54bf-106">Required.</span></span> <span data-ttu-id="e54bf-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="e54bf-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="e54bf-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e54bf-108">Required.</span></span> <span data-ttu-id="e54bf-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="e54bf-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e54bf-110">Résultat</span><span class="sxs-lookup"><span data-stu-id="e54bf-110">Result</span></span>  
 <span data-ttu-id="e54bf-111">Le résultat est `number` à la puissance de `exponent`, toujours comme un `Double` valeur.</span><span class="sxs-lookup"><span data-stu-id="e54bf-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e54bf-112">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="e54bf-112">Supported Types</span></span>  
 <span data-ttu-id="e54bf-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="e54bf-113">`Double`.</span></span> <span data-ttu-id="e54bf-114">Les opérandes de tous types sont convertis en `Double`.</span><span class="sxs-lookup"><span data-stu-id="e54bf-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e54bf-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="e54bf-115">Remarks</span></span>  
 <span data-ttu-id="e54bf-116">Visual Basic exécute toujours l’élévation à la puissance de la [Type de données Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e54bf-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="e54bf-117">La valeur de `exponent` peut être fractionnaire, négative, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="e54bf-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="e54bf-118">Lorsque plusieurs élévation est effectuée dans une expression unique, la `^` opérateur est évalué comme il est rencontré, de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="e54bf-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e54bf-119">Le `^` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="e54bf-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e54bf-120">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="e54bf-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e54bf-121">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e54bf-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e54bf-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="e54bf-122">Example</span></span>  
 <span data-ttu-id="e54bf-123">L’exemple suivant utilise le `^` opérateur pour élever un nombre à la puissance d’un exposant.</span><span class="sxs-lookup"><span data-stu-id="e54bf-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="e54bf-124">Le résultat est le premier opérande élevé à la puissance de la seconde.</span><span class="sxs-lookup"><span data-stu-id="e54bf-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="e54bf-125">L’exemple précédent génère les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="e54bf-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="e54bf-126">`exp1`a la valeur 4 (2 au carré).</span><span class="sxs-lookup"><span data-stu-id="e54bf-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="e54bf-127">`exp2`a la valeur 19 683 (3 au cube, puis cette valeur au cube).</span><span class="sxs-lookup"><span data-stu-id="e54bf-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="e54bf-128">`exp3`a la valeur-125 (-5 au cube).</span><span class="sxs-lookup"><span data-stu-id="e54bf-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="e54bf-129">`exp4`a la valeur 625 (-5 à la puissance quatre).</span><span class="sxs-lookup"><span data-stu-id="e54bf-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="e54bf-130">`exp5`a la valeur 2 (racine cubique de 8).</span><span class="sxs-lookup"><span data-stu-id="e54bf-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="e54bf-131">`exp6`a la valeur 0,5 (1,0 divisé par la racine cubique de 8).</span><span class="sxs-lookup"><span data-stu-id="e54bf-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="e54bf-132">Notez l’importance des parenthèses dans les expressions dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="e54bf-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="e54bf-133">Raison de *la priorité des opérateurs*, Visual Basic exécute normalement le `^` opérateur avant les autres, même l’unaire `–` opérateur.</span><span class="sxs-lookup"><span data-stu-id="e54bf-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="e54bf-134">Si `exp4` et `exp6` avaient été calculés sans parenthèses, ils aurait produit les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="e54bf-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="e54bf-135">`exp4 = -5 ^ 4`serait calculé comme-(5 à la puissance quatre), ce qui entraînerait-625.</span><span class="sxs-lookup"><span data-stu-id="e54bf-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="e54bf-136">`exp6 = 8 ^ -1.0 / 3.0`serait calculé comme (8 à la puissance-1, ou 0,125) divisé par 3,0, ce qui donnerait 0,041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="e54bf-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54bf-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e54bf-137">See Also</span></span>  
 [<span data-ttu-id="e54bf-138">^= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e54bf-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="e54bf-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="e54bf-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e54bf-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e54bf-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e54bf-141">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="e54bf-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e54bf-142">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e54bf-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
