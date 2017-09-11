---
title: "Priorité des opérateurs dans Visual Basic | Documents Microsoft"
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
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f653dd83c9778dddfe0e52db27065f7d73866e37
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="fccec-102">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fccec-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="fccec-103">Lorsque plusieurs opérations ont lieu dans une expression, chaque partie est évalué et résolu dans un ordre prédéterminé *la priorité des opérateurs*.</span><span class="sxs-lookup"><span data-stu-id="fccec-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="fccec-104">Règles de priorité</span><span class="sxs-lookup"><span data-stu-id="fccec-104">Precedence Rules</span></span>  
 <span data-ttu-id="fccec-105">Expressions contenant des opérateurs à partir de plusieurs catégories, elles sont évaluées selon les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="fccec-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="fccec-106">Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante et leur priorité supérieure à la comparaison, logiques et opérateurs au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="fccec-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="fccec-107">Tous les opérateurs de comparaison ont la même priorité et leur priorité supérieure à celle des opérateurs logiques et de bits, mais moins élevée que les opérateurs arithmétiques et de concaténation.</span><span class="sxs-lookup"><span data-stu-id="fccec-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="fccec-108">Les opérateurs logiques et de bits ont l’ordre de priorité décrit dans la section suivante, et leur priorité inférieure à celle de l’arithmétique, concaténation et les opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="fccec-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="fccec-109">Les opérateurs ayant la même priorité sont évalués de gauche à droite dans l’ordre dans lequel ils apparaissent dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="fccec-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="fccec-110">Ordre de priorité</span><span class="sxs-lookup"><span data-stu-id="fccec-110">Precedence Order</span></span>  
 <span data-ttu-id="fccec-111">Les opérateurs sont évalués dans l’ordre de priorité suivant :</span><span class="sxs-lookup"><span data-stu-id="fccec-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="fccec-112">Await, opérateur</span><span class="sxs-lookup"><span data-stu-id="fccec-112">Await Operator</span></span>  
 <span data-ttu-id="fccec-113">Await</span><span class="sxs-lookup"><span data-stu-id="fccec-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="fccec-114">Opérations arithmétiques et concaténation</span><span class="sxs-lookup"><span data-stu-id="fccec-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="fccec-115">Élévation à la puissance (`^`)</span><span class="sxs-lookup"><span data-stu-id="fccec-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="fccec-116">Unaire identité et la négation (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="fccec-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="fccec-117">Multiplication et division à virgule flottante (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="fccec-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="fccec-118">Division d’entier (`\`)</span><span class="sxs-lookup"><span data-stu-id="fccec-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="fccec-119">Modulo arithmétique (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="fccec-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="fccec-120">Addition et soustraction (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="fccec-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="fccec-121">Concaténation de chaînes (`&`)</span><span class="sxs-lookup"><span data-stu-id="fccec-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="fccec-122">Décalage de bits arithmétique (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="fccec-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="fccec-123">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="fccec-123">Comparison Operators</span></span>  
 <span data-ttu-id="fccec-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)</span><span class="sxs-lookup"><span data-stu-id="fccec-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="fccec-125">Opérateurs logiques et au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="fccec-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="fccec-126">Négation (`Not`)</span><span class="sxs-lookup"><span data-stu-id="fccec-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="fccec-127">Association (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="fccec-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="fccec-128">Disjonction inclusive (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="fccec-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="fccec-129">Disjonction exclusive (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="fccec-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="fccec-130">Commentaires</span><span class="sxs-lookup"><span data-stu-id="fccec-130">Comments</span></span>  
 <span data-ttu-id="fccec-131">Le `=` opérateur n'est que l’opérateur d’égalité, pas l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="fccec-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="fccec-132">L’opérateur de concaténation de chaîne (`&`) n’est pas un opérateur arithmétique, mais il est groupé avec les opérateurs arithmétiques priorités.</span><span class="sxs-lookup"><span data-stu-id="fccec-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="fccec-133">Le `Is` et `IsNot` opérateurs sont des opérateurs de comparaison de référence objet.</span><span class="sxs-lookup"><span data-stu-id="fccec-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="fccec-134">Ils ne comparent pas les valeurs de deux objets ; ils vérifient uniquement pour déterminer si deux variables objets font référence à la même instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="fccec-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="fccec-135">Associativité</span><span class="sxs-lookup"><span data-stu-id="fccec-135">Associativity</span></span>  
 <span data-ttu-id="fccec-136">Lorsque les opérateurs de même priorité apparaissent ensemble dans une expression, par exemple multiplication et division, le compilateur évalue chaque opération qu’elle rencontre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="fccec-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="fccec-137">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="fccec-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="fccec-138">La première expression évalue la division 96 / 8 (ce qui entraîne à 12), puis la division 12 / 4, ce qui se traduit par trois.</span><span class="sxs-lookup"><span data-stu-id="fccec-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="fccec-139">Comme le compilateur évalue les opérations de `n1` de gauche à droite, l’évaluation ne change pas lorsque cet ordre est indiqué explicitement pour `n2`.</span><span class="sxs-lookup"><span data-stu-id="fccec-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="fccec-140">Les deux `n1` et `n2` ont un résultat de trois.</span><span class="sxs-lookup"><span data-stu-id="fccec-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="fccec-141">En revanche, `n3` a un résultat égal à 48, parce que les parenthèses forcent le compilateur à évaluer 8 / 4 première.</span><span class="sxs-lookup"><span data-stu-id="fccec-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="fccec-142">En raison de ce comportement, les opérateurs sont dits *associatifs sur leur gauche* dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="fccec-142">Because of this behavior, operators are said to be *left associative* in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="fccec-143">Substitution de priorité et associativité</span><span class="sxs-lookup"><span data-stu-id="fccec-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="fccec-144">Vous pouvez utiliser des parenthèses pour forcer certaines parties d’une expression doit être évaluée avant d’autres.</span><span class="sxs-lookup"><span data-stu-id="fccec-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="fccec-145">Cela peut substituer l’ordre de priorité et l’associativité de gauche.</span><span class="sxs-lookup"><span data-stu-id="fccec-145">This can override both the order of precedence and the left associativity.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="fccec-146">effectue toujours les opérations entre parenthèses avant celles en dehors.</span><span class="sxs-lookup"><span data-stu-id="fccec-146"> always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="fccec-147">Toutefois, entre parenthèses, il maintient ordinaire priorité et associativité, sauf si vous utilisez des parenthèses dans les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="fccec-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="fccec-148">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="fccec-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="fccec-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fccec-149">See Also</span></span>  
 <span data-ttu-id="fccec-150">[=, Opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-150">[= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) </span></span>  
<span data-ttu-id="fccec-151"> [Opérateur](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-151"> [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="fccec-152"> [IsNot, opérateur](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-152"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="fccec-153"> [LIKE (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-153"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="fccec-154"> [TypeOf, opérateur](../../../visual-basic/language-reference/operators/typeof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-154"> [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md) </span></span>  
<span data-ttu-id="fccec-155"> [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-155"> [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="fccec-156"> [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="fccec-156"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="fccec-157"> [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="fccec-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>
