---
title: "Opérateurs de comparaison (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa450f7978f46196663c7534b31597b04d80482a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="966b8-102">Opérateurs de comparaison (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="966b8-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="966b8-103">Voici les opérateurs de comparaison définis dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="966b8-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="966b8-104">`<`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-104">`<` operator</span></span>  
  
 <span data-ttu-id="966b8-105">`<=`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-105">`<=` operator</span></span>  
  
 <span data-ttu-id="966b8-106">`>`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-106">`>` operator</span></span>  
  
 <span data-ttu-id="966b8-107">`>=`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-107">`>=` operator</span></span>  
  
 <span data-ttu-id="966b8-108">`=`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-108">`=` operator</span></span>  
  
 <span data-ttu-id="966b8-109">`<>`(opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="966b8-110">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="966b8-111">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="966b8-112">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="966b8-113">Ces opérateurs comparent deux expressions pour déterminer si elles sont égales, et dans le cas contraire, leurs différences.</span><span class="sxs-lookup"><span data-stu-id="966b8-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="966b8-114">`Is`, `IsNot`, et `Like` sont présentées en détail dans les pages d’aide distinctes.</span><span class="sxs-lookup"><span data-stu-id="966b8-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="966b8-115">Opérateurs de comparaison relationnels sont présentées en détail dans cette page.</span><span class="sxs-lookup"><span data-stu-id="966b8-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966b8-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="966b8-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="966b8-117">Composants</span><span class="sxs-lookup"><span data-stu-id="966b8-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="966b8-118">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-118">Required.</span></span> <span data-ttu-id="966b8-119">A `Boolean` valeur représentant le résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="966b8-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="966b8-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-120">Required.</span></span> <span data-ttu-id="966b8-121">Toute expression.</span><span class="sxs-lookup"><span data-stu-id="966b8-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="966b8-122">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-122">Required.</span></span> <span data-ttu-id="966b8-123">N’importe quel opérateur de comparaison relationnel.</span><span class="sxs-lookup"><span data-stu-id="966b8-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="966b8-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="966b8-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="966b8-125">Requis.</span><span class="sxs-lookup"><span data-stu-id="966b8-125">Required.</span></span> <span data-ttu-id="966b8-126">Tous les noms d’objet de référence.</span><span class="sxs-lookup"><span data-stu-id="966b8-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="966b8-127">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-127">Required.</span></span> <span data-ttu-id="966b8-128">Toute expression `String`.</span><span class="sxs-lookup"><span data-stu-id="966b8-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="966b8-129">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-129">Required.</span></span> <span data-ttu-id="966b8-130">N’importe quel `String` expression ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="966b8-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966b8-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="966b8-131">Remarks</span></span>  
 <span data-ttu-id="966b8-132">Le tableau suivant contient une liste des opérateurs de comparaison relationnels et les conditions qui déterminent si `result` est `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="966b8-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="966b8-133">Opérateur</span><span class="sxs-lookup"><span data-stu-id="966b8-133">Operator</span></span>|<span data-ttu-id="966b8-134">`True`If</span><span class="sxs-lookup"><span data-stu-id="966b8-134">`True` if</span></span>|<span data-ttu-id="966b8-135">`False`If</span><span class="sxs-lookup"><span data-stu-id="966b8-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="966b8-136">`<`(Inférieur à)</span><span class="sxs-lookup"><span data-stu-id="966b8-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="966b8-137">`<=`(Inférieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="966b8-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="966b8-138">`>`(Supérieur à)</span><span class="sxs-lookup"><span data-stu-id="966b8-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="966b8-139">`>=`(Supérieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="966b8-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="966b8-140">`=`(Égal à)</span><span class="sxs-lookup"><span data-stu-id="966b8-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="966b8-141">`<>`(Différent de)</span><span class="sxs-lookup"><span data-stu-id="966b8-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="966b8-142">Le [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md) est également utilisé comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="966b8-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="966b8-143">Le `Is` (opérateur), le `IsNot` (opérateur) et le `Like` opérateur ont des fonctionnalités de comparaison spécifiques qui diffèrent des opérateurs dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="966b8-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="966b8-144">Comparaison de nombres</span><span class="sxs-lookup"><span data-stu-id="966b8-144">Comparing Numbers</span></span>  
 <span data-ttu-id="966b8-145">Lorsque vous comparez une expression de type `Single` à un de type `Double`, le `Single` expression est convertie en `Double`.</span><span class="sxs-lookup"><span data-stu-id="966b8-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="966b8-146">Ce comportement est l’inverse de celui trouvé dans Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="966b8-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="966b8-147">De même, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double`, le `Decimal` expression est convertie en `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="966b8-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="966b8-148">Pour `Decimal` expressions, toute valeur fractionnaire inférieure à 1E-28 peut-être être perdue.</span><span class="sxs-lookup"><span data-stu-id="966b8-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="966b8-149">Cette perte de valeur fractionnaire risque de deux valeurs considérées comme égales lorsqu’ils ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="966b8-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="966b8-150">Pour cette raison, vous devez prendre soin lors de l’utilisation de l’égalité (`=`) pour comparer deux variables à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="966b8-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="966b8-151">Il est plus sûr tester si la valeur absolue de la différence entre les deux nombres est inférieure à une petite tolérance acceptable.</span><span class="sxs-lookup"><span data-stu-id="966b8-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="966b8-152">À virgule flottante imprécision</span><span class="sxs-lookup"><span data-stu-id="966b8-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="966b8-153">Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours de représentation précise dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="966b8-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="966b8-154">Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les [MOD, opérateur](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="966b8-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="966b8-155">Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="966b8-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="966b8-156">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="966b8-156">Comparing Strings</span></span>  
 <span data-ttu-id="966b8-157">Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées selon leur ordre de tri par ordre alphabétique, qui varie selon le `Option Compare` paramètre.</span><span class="sxs-lookup"><span data-stu-id="966b8-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="966b8-158">`Option Compare Binary`bases de comparaisons sur un ordre de tri dérivé des représentations binaires internes des caractères de chaînes.</span><span class="sxs-lookup"><span data-stu-id="966b8-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="966b8-159">L’ordre de tri est déterminé par la page de codes.</span><span class="sxs-lookup"><span data-stu-id="966b8-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="966b8-160">L’exemple suivant montre un ordre de tri binaire standard.</span><span class="sxs-lookup"><span data-stu-id="966b8-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="966b8-161">`Option Compare Text`bases de chaîne des comparaisons sur un ordre de tri de texte sans respecter la casse déterminé par les paramètres régionaux de votre application.</span><span class="sxs-lookup"><span data-stu-id="966b8-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="966b8-162">Lorsque vous définissez `Option Compare Text` et triez les caractères dans l’exemple précédent, l’ordre de tri de texte suivant s’applique :</span><span class="sxs-lookup"><span data-stu-id="966b8-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="966b8-163">Dépendance des paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="966b8-163">Locale Dependence</span></span>  
 <span data-ttu-id="966b8-164">Lorsque vous définissez `Option Compare Text`, le résultat d’une comparaison de chaînes peut dépendre des paramètres régionaux dans lequel l’application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="966b8-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="966b8-165">Deux caractères peuvent considérés comme égaux dans des paramètres régionaux, mais pas dans un autre.</span><span class="sxs-lookup"><span data-stu-id="966b8-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="966b8-166">Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, telles que s’il faut accepter une tentative de connexion, vous devez être alerte sensibilité de paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="966b8-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="966b8-167">Un paramètre `Option Compare Binary` ou appel le <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, qui prend les paramètres régionaux en compte.</span><span class="sxs-lookup"><span data-stu-id="966b8-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="966b8-168">Programmation sans type avec des opérateurs de comparaison relationnels</span><span class="sxs-lookup"><span data-stu-id="966b8-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="966b8-169">L’utilisation d’opérateurs de comparaison relationnels avec `Object` expressions n’est pas autorisée sous `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="966b8-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="966b8-170">Lorsque `Option Strict` est `Off`et la valeur `expression1` ou `expression2` est un `Object` expression, les types d’exécution déterminent la façon dont ils sont comparés.</span><span class="sxs-lookup"><span data-stu-id="966b8-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="966b8-171">Le tableau suivant montre comment les expressions sont comparées et le résultat de la comparaison, en fonction du type d’exécution des opérandes.</span><span class="sxs-lookup"><span data-stu-id="966b8-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="966b8-172">Si les opérandes sont</span><span class="sxs-lookup"><span data-stu-id="966b8-172">If operands are</span></span>|<span data-ttu-id="966b8-173">La comparaison est</span><span class="sxs-lookup"><span data-stu-id="966b8-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="966b8-174">Les deux`String`</span><span class="sxs-lookup"><span data-stu-id="966b8-174">Both `String`</span></span>|<span data-ttu-id="966b8-175">Comparaison basée sur les caractéristiques de tri de chaîne de tri.</span><span class="sxs-lookup"><span data-stu-id="966b8-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="966b8-176">Les deux numériques</span><span class="sxs-lookup"><span data-stu-id="966b8-176">Both numeric</span></span>|<span data-ttu-id="966b8-177">Les objets convertis en `Double`, comparaison numérique.</span><span class="sxs-lookup"><span data-stu-id="966b8-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="966b8-178">Une valeur numérique et l’autre`String`</span><span class="sxs-lookup"><span data-stu-id="966b8-178">One numeric and one `String`</span></span>|<span data-ttu-id="966b8-179">Le `String` est converti en un `Double` et une comparaison numérique est effectuée.</span><span class="sxs-lookup"><span data-stu-id="966b8-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="966b8-180">Si le `String` ne peut pas être converti en `Double`, un <xref:System.InvalidCastException> est levée.</span><span class="sxs-lookup"><span data-stu-id="966b8-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="966b8-181">Les deux sont des types de référence autres que`String`</span><span class="sxs-lookup"><span data-stu-id="966b8-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="966b8-182">Un objet <xref:System.InvalidCastException> est levé.</span><span class="sxs-lookup"><span data-stu-id="966b8-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="966b8-183">Les comparaisons numériques traitent `Nothing` en tant que 0.</span><span class="sxs-lookup"><span data-stu-id="966b8-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="966b8-184">Comparaisons de chaînes traitent `Nothing` en tant que `""` (une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="966b8-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="966b8-185">Surcharge</span><span class="sxs-lookup"><span data-stu-id="966b8-185">Overloading</span></span>  
 <span data-ttu-id="966b8-186">Opérateurs de comparaison relationnels (`<`.</span><span class="sxs-lookup"><span data-stu-id="966b8-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="966b8-187">`<=``>`, `>=`, `=`, `<>`) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir leur comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="966b8-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="966b8-188">Si votre code utilise un de ces opérateurs sur une telle classe ou structure, assurez-vous que vous comprenez le comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="966b8-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="966b8-189">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="966b8-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="966b8-190">Notez que la [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md) peuvent être surchargées uniquement en tant qu’un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="966b8-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="966b8-191">Exemple</span><span class="sxs-lookup"><span data-stu-id="966b8-191">Example</span></span>  
 <span data-ttu-id="966b8-192">L’exemple suivant montre les différentes utilisations des opérateurs de comparaison relationnels, ce qui vous permet de comparer des expressions.</span><span class="sxs-lookup"><span data-stu-id="966b8-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="966b8-193">Opérateurs de comparaison relationnels retournent un `Boolean` résultat qui indique si l’expression spécifiée a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="966b8-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="966b8-194">Lorsque vous appliquez le `>` et `<` opérateurs en chaînes, la comparaison est effectuée à l’aide de l’ordre de tri alphabétique normal des chaînes.</span><span class="sxs-lookup"><span data-stu-id="966b8-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="966b8-195">Cet ordre peut dépendre de vos paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="966b8-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="966b8-196">Si le tri respecte la casse ou non dépend de la [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) paramètre.</span><span class="sxs-lookup"><span data-stu-id="966b8-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="966b8-197">Dans l’exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True`.</span><span class="sxs-lookup"><span data-stu-id="966b8-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966b8-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="966b8-198">See Also</span></span>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="966b8-199">= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="966b8-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="966b8-200">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="966b8-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="966b8-201">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="966b8-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="966b8-202">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="966b8-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="966b8-203">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="966b8-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
