---
title: "Opérateurs de comparaison en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a958481fa04cb1a9abde69c5215dccd6dbbe4a14
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="2f30d-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f30d-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="2f30d-103">Opérateurs de comparaison comparent deux expressions et retournent un `Boolean` valeur qui représente la relation de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="2f30d-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="2f30d-104">Il existe des opérateurs pour comparer des valeurs numériques, des opérateurs de comparaison de chaînes et des opérateurs pour comparer des objets.</span><span class="sxs-lookup"><span data-stu-id="2f30d-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="2f30d-105">Les trois types d’opérateurs sont détaillés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2f30d-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="2f30d-106">Comparer des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="2f30d-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2f30d-107">Compare des valeurs numériques à l’aide de six opérateurs de comparaison numériques.</span><span class="sxs-lookup"><span data-stu-id="2f30d-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="2f30d-108">Chaque opérateur accepte comme opérandes deux expressions qui correspondent à des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="2f30d-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="2f30d-109">Le tableau suivant répertorie les opérateurs et présente des exemples de chacun.</span><span class="sxs-lookup"><span data-stu-id="2f30d-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="2f30d-110">Opérateur</span><span class="sxs-lookup"><span data-stu-id="2f30d-110">Operator</span></span>|<span data-ttu-id="2f30d-111">Condition testée</span><span class="sxs-lookup"><span data-stu-id="2f30d-111">Condition tested</span></span>|<span data-ttu-id="2f30d-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f30d-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="2f30d-113">`=`(Égalité)</span><span class="sxs-lookup"><span data-stu-id="2f30d-113">`=` (Equality)</span></span>|<span data-ttu-id="2f30d-114">Est la valeur de la première expression égale à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="2f30d-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="2f30d-118">`<>`(Inégalité)</span><span class="sxs-lookup"><span data-stu-id="2f30d-118">`<>` (Inequality)</span></span>|<span data-ttu-id="2f30d-119">La valeur de la première expression n’est pas égale à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="2f30d-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="2f30d-123">`<`(Inférieur à)</span><span class="sxs-lookup"><span data-stu-id="2f30d-123">`<` (Less than)</span></span>|<span data-ttu-id="2f30d-124">Est la valeur de la première expression inférieure à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="2f30d-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="2f30d-128">`>`(Supérieur à)</span><span class="sxs-lookup"><span data-stu-id="2f30d-128">`>` (Greater than)</span></span>|<span data-ttu-id="2f30d-129">La valeur de la première expression est supérieure à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="2f30d-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="2f30d-133">`<=`(Inférieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="2f30d-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="2f30d-134">Est la valeur de la première expression inférieure ou égale à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="2f30d-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="2f30d-138">`>=`(Supérieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="2f30d-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="2f30d-139">Est la valeur de la première expression supérieure ou égale à la valeur de la seconde ?</span><span class="sxs-lookup"><span data-stu-id="2f30d-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="2f30d-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="2f30d-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="2f30d-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="2f30d-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="2f30d-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="2f30d-143">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="2f30d-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2f30d-144">Compare des chaînes à l’aide de la [opérateur Like](../../../../visual-basic/language-reference/operators/like-operator.md) , ainsi que les opérateurs de comparaison numériques.</span><span class="sxs-lookup"><span data-stu-id="2f30d-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="2f30d-145">Le `Like` opérateur vous permet de spécifier un modèle.</span><span class="sxs-lookup"><span data-stu-id="2f30d-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="2f30d-146">La chaîne est ensuite comparée par rapport au modèle, et si elle correspond, le résultat est `True`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="2f30d-147">Dans le cas contraire, le résultat est `False`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="2f30d-148">Les opérateurs numériques permettent de comparer `String` valeurs selon leur ordre de tri, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f30d-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="2f30d-149">Le résultat de l’exemple précédent est `True` car le premier caractère dans la première chaîne est trié avant le premier caractère dans la deuxième chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f30d-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="2f30d-150">Si les premiers caractères sont identiques, la comparaison de continuer au caractère suivant dans les deux chaînes et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="2f30d-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="2f30d-151">Vous pouvez également tester l’égalité de chaînes à l’aide de l’opérateur d’égalité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f30d-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="2f30d-152">Si une chaîne est un préfixe de l’autre, tels que « aa » et « aaa », la plus longue chaîne est considéré comme supérieur à la chaîne la plus courte.</span><span class="sxs-lookup"><span data-stu-id="2f30d-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="2f30d-153">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="2f30d-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="2f30d-154">L’ordre de tri est basé sur une comparaison binaire ou une comparaison de texte selon le paramètre de `Option Compare`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="2f30d-155">Pour plus d’informations, consultez [instruction Option Compare](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2f30d-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="2f30d-156">Comparaison des objets</span><span class="sxs-lookup"><span data-stu-id="2f30d-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2f30d-157">Compare deux variables de référence avec l’objet le [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) et [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2f30d-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="2f30d-158">Vous pouvez utiliser un de ces opérateurs pour déterminer si deux variables de référence font référence à la même instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="2f30d-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="2f30d-159">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="2f30d-159">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2f30d-160">[!code-vb[VbVbalrOperators&#65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f30d-160">[!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="2f30d-161">Dans l’exemple précédent, `x Is y` a la valeur `True`, car les deux variables font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="2f30d-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="2f30d-162">Comparez ce résultat à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f30d-162">Contrast this result with the following example.</span></span>  
  
 <span data-ttu-id="2f30d-163">[!code-vb[VbVbalrOperators&#66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f30d-163">[!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="2f30d-164">Dans l’exemple précédent, `x Is y` a la valeur `False`, car même si les variables font référence à des objets du même type, ils font référence à des instances distinctes de ce type.</span><span class="sxs-lookup"><span data-stu-id="2f30d-164">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="2f30d-165">Lorsque vous souhaitez tester deux objets ne pointe ne pas vers la même instance, le `IsNot` opérateur vous permet d’éviter une combinaison grammaticalement maladroite de `Not` et `Is`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-165">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="2f30d-166">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="2f30d-166">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2f30d-167">[!code-vb[VbVbalrOperators&#67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f30d-167">[!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="2f30d-168">Dans l’exemple précédent, `If a IsNot b` équivaut à `If Not a Is b`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-168">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="2f30d-169">Comparaison de Type d’objet</span><span class="sxs-lookup"><span data-stu-id="2f30d-169">Comparing Object Type</span></span>  
 <span data-ttu-id="2f30d-170">Vous pouvez vérifier si un objet est d’un type particulier avec les `TypeOf`... `Is` expression.</span><span class="sxs-lookup"><span data-stu-id="2f30d-170">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="2f30d-171">La syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2f30d-171">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="2f30d-172">Lors de la `typename` spécifie un type d’interface, puis le `TypeOf`... `Is` retourne `True` si l’objet implémente le type interface.</span><span class="sxs-lookup"><span data-stu-id="2f30d-172">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="2f30d-173">Lors de la `typename` est un type classe, l’expression retourne `True` si l’objet est une instance de la classe spécifiée ou d’une classe qui dérive de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f30d-173">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="2f30d-174">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="2f30d-174">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2f30d-175">[!code-vb[VbVbalrOperators&#68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f30d-175">[!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="2f30d-176">Dans l’exemple précédent, le `TypeOf x Is Control` l’expression `True` , car le type de `x` est `Button`, qui hérite de `Control`.</span><span class="sxs-lookup"><span data-stu-id="2f30d-176">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="2f30d-177">Pour plus d’informations, consultez [TypeOf, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2f30d-177">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f30d-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f30d-178">See Also</span></span>  
 <span data-ttu-id="2f30d-179">[Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="2f30d-179">[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="2f30d-180"> [Opérateurs de comparaison](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2f30d-180"> [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="2f30d-181"> [Opérateurs](../../../../visual-basic/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="2f30d-181"> [Operators](../../../../visual-basic/language-reference/operators/index.md) </span></span>  
<span data-ttu-id="2f30d-182"> [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2f30d-182"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="2f30d-183"> [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2f30d-183"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="2f30d-184"> [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="2f30d-184"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
