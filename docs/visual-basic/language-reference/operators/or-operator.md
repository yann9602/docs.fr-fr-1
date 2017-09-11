---
title: "Opérateur (Visual Basic) ou | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
dev_langs:
- VB
helpviewer_keywords:
- Or operator
- operators [Visual Basic], bitwise
- inclusive Or operator
- bitwise operators, OR operator
- Or keyword
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison
- logical disjunction
- disjunction operator
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
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
ms.openlocfilehash: 01d51f50dd785f168ed850e3f1763b300d9d2011
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="9205c-102">Or, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9205c-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="9205c-103">Effectue une disjonction logique sur deux `Boolean` expressions ou une disjonction au niveau du bit sur deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="9205c-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9205c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9205c-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9205c-105">Composants</span><span class="sxs-lookup"><span data-stu-id="9205c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9205c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9205c-106">Required.</span></span> <span data-ttu-id="9205c-107">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="9205c-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="9205c-108">Pour `Boolean` comparaison, `result` est la disjonction logique inclusive de deux `Boolean` valeurs.</span><span class="sxs-lookup"><span data-stu-id="9205c-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="9205c-109">Pour les opérations au niveau du bit, `result` est une valeur numérique qui représente la disjonction de bits inclusive de deux modèles binaires numériques.</span><span class="sxs-lookup"><span data-stu-id="9205c-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="9205c-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9205c-110">Required.</span></span> <span data-ttu-id="9205c-111">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="9205c-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9205c-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9205c-112">Required.</span></span> <span data-ttu-id="9205c-113">N’importe quel `Boolean` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="9205c-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9205c-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="9205c-114">Remarks</span></span>  
 <span data-ttu-id="9205c-115">Pour `Boolean` comparaison, `result` est `False` si et seulement si `expression1` et `expression2` correspondre à `False`.</span><span class="sxs-lookup"><span data-stu-id="9205c-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="9205c-116">Le tableau suivant illustre comment `result` est déterminée.</span><span class="sxs-lookup"><span data-stu-id="9205c-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9205c-117">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="9205c-117">If `expression1` is</span></span>|<span data-ttu-id="9205c-118">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="9205c-118">And `expression2` is</span></span>|<span data-ttu-id="9205c-119">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="9205c-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="9205c-120">Dans un `Boolean` comparaison, la `Or` opérateur évalue toujours les deux expressions qui pourraient inclure des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="9205c-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="9205c-121">Le [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) exécute *de court-circuit*, ce qui signifie que si `expression1` est `True`, puis `expression2` n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="9205c-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="9205c-122">Pour les opérations au niveau du bit, les `Or` opérateur effectue une comparaison au niveau du bit des bits occupant la même positionnés dans deux expressions numériques et définit le bit de correspondant `result` conformément au tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9205c-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="9205c-123">Si bit dans `expression1` est</span><span class="sxs-lookup"><span data-stu-id="9205c-123">If bit in `expression1` is</span></span>|<span data-ttu-id="9205c-124">Et que le bit de `expression2` est</span><span class="sxs-lookup"><span data-stu-id="9205c-124">And bit in `expression2` is</span></span>|<span data-ttu-id="9205c-125">Le bit `result` est</span><span class="sxs-lookup"><span data-stu-id="9205c-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="9205c-126">1</span><span class="sxs-lookup"><span data-stu-id="9205c-126">1</span></span>|<span data-ttu-id="9205c-127">1</span><span class="sxs-lookup"><span data-stu-id="9205c-127">1</span></span>|<span data-ttu-id="9205c-128">1</span><span class="sxs-lookup"><span data-stu-id="9205c-128">1</span></span>|  
|<span data-ttu-id="9205c-129">1</span><span class="sxs-lookup"><span data-stu-id="9205c-129">1</span></span>|<span data-ttu-id="9205c-130">0</span><span class="sxs-lookup"><span data-stu-id="9205c-130">0</span></span>|<span data-ttu-id="9205c-131">1</span><span class="sxs-lookup"><span data-stu-id="9205c-131">1</span></span>|  
|<span data-ttu-id="9205c-132">0</span><span class="sxs-lookup"><span data-stu-id="9205c-132">0</span></span>|<span data-ttu-id="9205c-133">1</span><span class="sxs-lookup"><span data-stu-id="9205c-133">1</span></span>|<span data-ttu-id="9205c-134">1</span><span class="sxs-lookup"><span data-stu-id="9205c-134">1</span></span>|  
|<span data-ttu-id="9205c-135">0</span><span class="sxs-lookup"><span data-stu-id="9205c-135">0</span></span>|<span data-ttu-id="9205c-136">0</span><span class="sxs-lookup"><span data-stu-id="9205c-136">0</span></span>|<span data-ttu-id="9205c-137">0</span><span class="sxs-lookup"><span data-stu-id="9205c-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9205c-138">Étant donné que les opérateurs logiques et de bits ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.</span><span class="sxs-lookup"><span data-stu-id="9205c-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9205c-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="9205c-139">Data Types</span></span>  
 <span data-ttu-id="9205c-140">Si les opérandes se composent d’une `Boolean` expression et une expression numérique, Visual Basic convertit la `Boolean` expression à une valeur numérique (-1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="9205c-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="9205c-141">Pour un `Boolean` comparaison, le type de données du résultat est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9205c-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="9205c-142">Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`.</span><span class="sxs-lookup"><span data-stu-id="9205c-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9205c-143">Consultez le tableau « Et au niveau du bit comparaisons relationnelles » [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="9205c-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9205c-144">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9205c-144">Overloading</span></span>  
 <span data-ttu-id="9205c-145">Le `Or` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="9205c-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9205c-146">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="9205c-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9205c-147">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9205c-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9205c-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="9205c-148">Example</span></span>  
 <span data-ttu-id="9205c-149">L’exemple suivant utilise le `Or` opérateur effectue une disjonction logique inclusive sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="9205c-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="9205c-150">Le résultat est un `Boolean` valeur représentant si une des deux expressions est `True`.</span><span class="sxs-lookup"><span data-stu-id="9205c-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 <span data-ttu-id="9205c-151">[!code-vb[VbVbalrOperators&#35;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9205c-151">[!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="9205c-152">L’exemple précédent produit des résultats de `True`, `True`, et `False`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9205c-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9205c-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="9205c-153">Example</span></span>  
 <span data-ttu-id="9205c-154">L’exemple suivant utilise le `Or` opérateur effectue une disjonction logique inclusive sur les bits individuels de deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="9205c-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="9205c-155">Le bit du modèle de résultat est défini si un des bits correspondants dans les opérandes est défini sur 1.</span><span class="sxs-lookup"><span data-stu-id="9205c-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 <span data-ttu-id="9205c-156">[!code-vb[VbVbalrOperators n °&36;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9205c-156">[!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="9205c-157">L’exemple précédent produit les résultats de 10, 14 et 14, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9205c-157">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9205c-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9205c-158">See Also</span></span>  
 <span data-ttu-id="9205c-159">[Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="9205c-159">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="9205c-160"> [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="9205c-160"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="9205c-161"> [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="9205c-161"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="9205c-162"> [OrElse, opérateur](../../../visual-basic/language-reference/operators/orelse-operator.md) </span><span class="sxs-lookup"><span data-stu-id="9205c-162"> [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) </span></span>  
<span data-ttu-id="9205c-163"> [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="9205c-163"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

