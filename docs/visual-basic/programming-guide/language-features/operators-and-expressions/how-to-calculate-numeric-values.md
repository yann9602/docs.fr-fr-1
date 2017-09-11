---
title: "Comment : calculer des valeurs numériques (Visual Basic) | Documents Microsoft"
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
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
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
ms.openlocfilehash: fe781cca8f716c792d3af153b2004c716bc87f90
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="cfdff-102">Comment : calculer des valeurs numériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfdff-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="cfdff-103">Vous pouvez calculer des valeurs numériques à l’aide d’expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="cfdff-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="cfdff-104">A *expression numérique* est une expression qui contient des littéraux, des constantes et des variables représentant des valeurs numériques et les opérateurs qui agissent sur ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="cfdff-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="cfdff-105">Calcul de valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="cfdff-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="cfdff-106">Pour calculer une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="cfdff-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="cfdff-107">Combiner une ou plusieurs des littéraux numériques, de constantes et variables dans une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="cfdff-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="cfdff-108">L’exemple suivant montre des expressions numériques valides.</span><span class="sxs-lookup"><span data-stu-id="cfdff-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="cfdff-109">Les trois premières lignes affichent un littéral, une constante et une variable.</span><span class="sxs-lookup"><span data-stu-id="cfdff-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="cfdff-110">Chacune d’elle forme une expression numérique valide par elle-même.</span><span class="sxs-lookup"><span data-stu-id="cfdff-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="cfdff-111">La dernière ligne affiche une combinaison d’une variable avec deux littéraux.</span><span class="sxs-lookup"><span data-stu-id="cfdff-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="cfdff-112">Notez qu’une expression numérique ne constitue pas une liste complète [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] en elle-même.</span><span class="sxs-lookup"><span data-stu-id="cfdff-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statement by itself.</span></span> <span data-ttu-id="cfdff-113">Vous devez utiliser l’expression dans le cadre d’une instruction complète.</span><span class="sxs-lookup"><span data-stu-id="cfdff-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="cfdff-114">Pour stocker une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="cfdff-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="cfdff-115">Vous pouvez utiliser une instruction d’assignation pour assigner la valeur représentée par une expression numérique à une variable, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cfdff-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     <span data-ttu-id="cfdff-116">[!code-vb[VbVbalrOperators&#82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cfdff-116">[!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span></span>  
  
     <span data-ttu-id="cfdff-117">Dans l’exemple précédent, la valeur de l’expression située à droite de l’opérateur égal (`=`) est affectée à la variable `j` sur le côté gauche de l’opérateur, donc `j` correspond à 276.</span><span class="sxs-lookup"><span data-stu-id="cfdff-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="cfdff-118">Pour plus d’informations, consultez [instructions](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="cfdff-118">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="cfdff-119">Opérateurs multiples</span><span class="sxs-lookup"><span data-stu-id="cfdff-119">Multiple Operators</span></span>  
 <span data-ttu-id="cfdff-120">Si l’expression numérique contient plusieurs opérateurs, l’ordre dans lequel ils sont évalués est déterminé par les règles de priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="cfdff-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="cfdff-121">Pour remplacer les règles de priorité des opérateurs, vous placez les expressions entre parenthèses, comme dans l’exemple ci-dessus ; les expressions entre parenthèses sont évaluées en premier.</span><span class="sxs-lookup"><span data-stu-id="cfdff-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="cfdff-122">Pour substituer la priorité des opérateurs normale</span><span class="sxs-lookup"><span data-stu-id="cfdff-122">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="cfdff-123">Utilisez des parenthèses pour encadrer les opérations que vous souhaitez être exécutée en premier.</span><span class="sxs-lookup"><span data-stu-id="cfdff-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="cfdff-124">L’exemple suivant montre deux résultats différents avec les mêmes opérandes et opérateurs.</span><span class="sxs-lookup"><span data-stu-id="cfdff-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     <span data-ttu-id="cfdff-125">[!code-vb[83 VbVbalrOperators](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cfdff-125">[!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span></span>  
  
     <span data-ttu-id="cfdff-126">Dans l’exemple précédent, le calcul de `j` effectue l’opérateur d’addition (`+`) première parce que les parenthèses autour de `(67 + i)` substituer la priorité normale et la valeur affectée à `j` est de 276 (4 fois 69).</span><span class="sxs-lookup"><span data-stu-id="cfdff-126">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="cfdff-127">Le calcul de `k` exécute les opérateurs dans leur priorité normale (`*` avant `+`) et la valeur affectée à `k` est de 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="cfdff-127">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="cfdff-128">Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="cfdff-128">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdff-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfdff-129">See Also</span></span>  
 <span data-ttu-id="cfdff-130">[Opérateurs et Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfdff-130">[Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="cfdff-131"> [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="cfdff-131"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="cfdff-132"> [Instructions](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfdff-132"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="cfdff-133"> [Priorité des opérateurs dans Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="cfdff-133"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="cfdff-134"> [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="cfdff-134"> [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="cfdff-135"> [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="cfdff-135"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
