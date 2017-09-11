---
title: "/, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
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
ms.openlocfilehash: 82255339c3bdab7f6e760de9bef073f463260877
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c3b7c-102">/, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="c3b7c-103">Effectue la division de deux nombres et retourne un résultat à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3b7c-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c3b7c-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c3b7c-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="c3b7c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-106">Required.</span></span> <span data-ttu-id="c3b7c-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c3b7c-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-108">Required.</span></span> <span data-ttu-id="c3b7c-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c3b7c-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="c3b7c-110">Supported Types</span></span>  
 <span data-ttu-id="c3b7c-111">Tous les types numériques, y compris les types non signés et à virgule flottante et `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="c3b7c-112">Résultat</span><span class="sxs-lookup"><span data-stu-id="c3b7c-112">Result</span></span>  
 <span data-ttu-id="c3b7c-113">Le résultat est le quotient entier de `expression1` divisé par `expression2`, y compris tout élément restant.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="c3b7c-114">Le [\, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) renvoie le quotient entier, sans le reste.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3b7c-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c3b7c-115">Remarks</span></span>  
 <span data-ttu-id="c3b7c-116">Le type de données du résultat dépend des types des opérandes.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="c3b7c-117">Le tableau suivant présente la façon dont le type de données du résultat est déterminé.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="c3b7c-118">Types de données d’opérande</span><span class="sxs-lookup"><span data-stu-id="c3b7c-118">Operand data types</span></span>|<span data-ttu-id="c3b7c-119">Type de données de résultat</span><span class="sxs-lookup"><span data-stu-id="c3b7c-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="c3b7c-120">Les deux expressions sont des types de données intégraux ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [octets](../../../visual-basic/language-reference/data-types/byte-data-type.md), [court](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [entier](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="c3b7c-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="c3b7c-121">Une expression est un [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) type de données et l’autre n’est pas un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="c3b7c-122">Une expression est un [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) type de données et l’autre n’est pas un [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) ou un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="c3b7c-123">Des expressions sont un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) type de données</span><span class="sxs-lookup"><span data-stu-id="c3b7c-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="c3b7c-124">Avant d’effectuer la division, toutes les expressions numériques intégrales sont étendues à `Double`.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="c3b7c-125">Si vous affectez le résultat à un type intégral, Visual Basic essaie de convertir le résultat de `Double` à ce type.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="c3b7c-126">Cela peut lever une exception si le résultat ne tient pas dans ce type.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="c3b7c-127">En particulier, consultez « Tentative de Division par zéro » sur cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="c3b7c-128">Si `expression1` ou `expression2` a la valeur [rien](../../../visual-basic/language-reference/nothing.md), elle est considérée comme nulle.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="c3b7c-129">Tentative de Division par zéro</span><span class="sxs-lookup"><span data-stu-id="c3b7c-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="c3b7c-130">Si `expression2` correspond à zéro, le `/` opérateur se comporte différemment pour les types de données différents d’opérande.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="c3b7c-131">Le tableau suivant répertorie les comportements possibles.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="c3b7c-132">Types de données d’opérande</span><span class="sxs-lookup"><span data-stu-id="c3b7c-132">Operand data types</span></span>|<span data-ttu-id="c3b7c-133">Comportement si `expression2` est égal à zéro</span><span class="sxs-lookup"><span data-stu-id="c3b7c-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="c3b7c-134">Virgule flottante (`Single` ou `Double`)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="c3b7c-135">Retourne l’infini (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN>(pas un nombre) si `expression1` est également zéro</xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity></span><span class="sxs-lookup"><span data-stu-id="c3b7c-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="c3b7c-136">Lève une exception<xref:System.DivideByZeroException></xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="c3b7c-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="c3b7c-137">Intégral (signé ou non signé)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="c3b7c-138">Tentative de conversion en type intégral lève <xref:System.OverflowException>, car les types intégraux ne peut pas accepter <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN></xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="c3b7c-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c3b7c-139">Le `/` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c3b7c-140">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c3b7c-141">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c3b7c-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b7c-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3b7c-142">Example</span></span>  
 <span data-ttu-id="c3b7c-143">Cet exemple utilise le `/` opérateur pour effectuer une division à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="c3b7c-144">Le résultat est le quotient de deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-144">The result is the quotient of the two operands.</span></span>  
  
 <span data-ttu-id="c3b7c-145">[!code-vb[VbVbalrOperators&#16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c3b7c-145">[!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="c3b7c-146">Les expressions dans l’exemple précédent retournent les valeurs 2,5 et 3,333333.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="c3b7c-147">Notez que le résultat est toujours en virgule flottante (`Double`), même si les deux opérandes sont des constantes entières.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b7c-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3b7c-148">See Also</span></span>  
 <span data-ttu-id="c3b7c-149">[/ =, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-149">[/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="c3b7c-150"> [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-150"> [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span></span>  
<span data-ttu-id="c3b7c-151"> [Types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-151"> [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span></span>  
<span data-ttu-id="c3b7c-152"> [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-152"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="c3b7c-153"> [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-153"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="c3b7c-154"> [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="c3b7c-154"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="c3b7c-155"> [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c3b7c-155"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

