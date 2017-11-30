---
title: "And, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="b3f97-102">And, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3f97-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="b3f97-103">Effectue une conjonction logique sur deux `Boolean` expressions ou conjonction au niveau du bit sur deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="b3f97-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3f97-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b3f97-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b3f97-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b3f97-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b3f97-106">Required.</span></span> <span data-ttu-id="b3f97-107">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="b3f97-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="b3f97-108">Pour la comparaison Boolean, `result` est la conjonction logique de deux `Boolean` valeurs.</span><span class="sxs-lookup"><span data-stu-id="b3f97-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="b3f97-109">Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.</span><span class="sxs-lookup"><span data-stu-id="b3f97-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b3f97-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b3f97-110">Required.</span></span> <span data-ttu-id="b3f97-111">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="b3f97-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b3f97-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b3f97-112">Required.</span></span> <span data-ttu-id="b3f97-113">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="b3f97-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3f97-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="b3f97-114">Remarks</span></span>  
 <span data-ttu-id="b3f97-115">Pour la comparaison Boolean, `result` est `True` si et seulement si `expression1` et `expression2` correspondre à `True`.</span><span class="sxs-lookup"><span data-stu-id="b3f97-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="b3f97-116">Le tableau suivant illustre comment `result` est déterminée.</span><span class="sxs-lookup"><span data-stu-id="b3f97-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b3f97-117">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-117">If `expression1` is</span></span>|<span data-ttu-id="b3f97-118">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-118">And `expression2` is</span></span>|<span data-ttu-id="b3f97-119">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="b3f97-120">Dans la comparaison Boolean, le `And` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="b3f97-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="b3f97-121">Le [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *de court-circuit*, ce qui signifie que si `expression1` est `False`, puis `expression2` n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="b3f97-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="b3f97-122">Quand il est appliqué à des valeurs numériques, la `And` opérateur effectue une comparaison au niveau du bit de position identique dans deux expressions numériques et définit le bit dans correspondant `result` conformément au tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b3f97-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="b3f97-123">Si bit dans `expression1` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-123">If bit in `expression1` is</span></span>|<span data-ttu-id="b3f97-124">Et que le bit de `expression2` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-124">And bit in `expression2` is</span></span>|<span data-ttu-id="b3f97-125">Le bit `result` est</span><span class="sxs-lookup"><span data-stu-id="b3f97-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="b3f97-126">1</span><span class="sxs-lookup"><span data-stu-id="b3f97-126">1</span></span>|<span data-ttu-id="b3f97-127">1</span><span class="sxs-lookup"><span data-stu-id="b3f97-127">1</span></span>|<span data-ttu-id="b3f97-128">1</span><span class="sxs-lookup"><span data-stu-id="b3f97-128">1</span></span>|  
|<span data-ttu-id="b3f97-129">1</span><span class="sxs-lookup"><span data-stu-id="b3f97-129">1</span></span>|<span data-ttu-id="b3f97-130">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-130">0</span></span>|<span data-ttu-id="b3f97-131">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-131">0</span></span>|  
|<span data-ttu-id="b3f97-132">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-132">0</span></span>|<span data-ttu-id="b3f97-133">1</span><span class="sxs-lookup"><span data-stu-id="b3f97-133">1</span></span>|<span data-ttu-id="b3f97-134">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-134">0</span></span>|  
|<span data-ttu-id="b3f97-135">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-135">0</span></span>|<span data-ttu-id="b3f97-136">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-136">0</span></span>|<span data-ttu-id="b3f97-137">0</span><span class="sxs-lookup"><span data-stu-id="b3f97-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b3f97-138">Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations de bits doivent être placées entre parenthèses pour garantir des résultats précis.</span><span class="sxs-lookup"><span data-stu-id="b3f97-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="b3f97-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="b3f97-139">Data Types</span></span>  
 <span data-ttu-id="b3f97-140">Si les opérandes se composent d’une `Boolean` expression et une expression numérique, Visual Basic convertit le `Boolean` expression à une valeur numérique (-1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="b3f97-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="b3f97-141">Pour une comparaison Boolean, le type de données du résultat est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b3f97-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="b3f97-142">Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`.</span><span class="sxs-lookup"><span data-stu-id="b3f97-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="b3f97-143">Consultez le tableau « Relationnelles et au niveau du bit des comparaisons » [Types de données de résultats de l’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="b3f97-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3f97-144">Le `And` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b3f97-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b3f97-145">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="b3f97-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b3f97-146">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b3f97-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3f97-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="b3f97-147">Example</span></span>  
 <span data-ttu-id="b3f97-148">L’exemple suivant utilise le `And` opérateur effectue une conjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="b3f97-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="b3f97-149">Le résultat est un `Boolean` valeur qui indique si les deux expressions sont `True`.</span><span class="sxs-lookup"><span data-stu-id="b3f97-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="b3f97-150">L’exemple précédent produit des résultats de `True` et `False`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b3f97-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3f97-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="b3f97-151">Example</span></span>  
 <span data-ttu-id="b3f97-152">L’exemple suivant utilise le `And` opérateur pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="b3f97-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="b3f97-153">Le bit du modèle de résultat est défini si les bits correspondants dans les opérandes sont toutes deux définies sur 1.</span><span class="sxs-lookup"><span data-stu-id="b3f97-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="b3f97-154">L’exemple précédent produit des résultats de 8, 2 et 0, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b3f97-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f97-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3f97-155">See Also</span></span>  
 [<span data-ttu-id="b3f97-156">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3f97-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="b3f97-157">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3f97-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b3f97-158">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b3f97-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b3f97-159">AndAlso (opérateur)</span><span class="sxs-lookup"><span data-stu-id="b3f97-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="b3f97-160">Opérateurs logiques et au niveau du bit en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3f97-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
