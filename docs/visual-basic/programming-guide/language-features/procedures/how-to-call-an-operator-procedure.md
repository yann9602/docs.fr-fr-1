---
title: "Comment : appeler une procédure d’opérateur (Visual Basic) | Documents Microsoft"
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
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
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
ms.openlocfilehash: cd85a14a6f5534e90497268134f4b2b0cc292249
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="663b5-102">Comment : appeler une procédure d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="663b5-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="663b5-103">Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="663b5-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="663b5-104">Dans le cas d’un opérateur de conversion, vous appelez le [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données à un autre.</span><span class="sxs-lookup"><span data-stu-id="663b5-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="663b5-105">Vous n’appelez pas explicitement de procédures d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="663b5-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="663b5-106">Vous utilisez l’opérateur, ou la `CType` fonction, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez normalement un opérateur.</span><span class="sxs-lookup"><span data-stu-id="663b5-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="663b5-107">effectue l’appel à la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="663b5-107"> makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="663b5-108">Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="663b5-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="663b5-109">Pour appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="663b5-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="663b5-110">Utilisez le symbole d’opérateur dans une expression de la façon habituelle.</span><span class="sxs-lookup"><span data-stu-id="663b5-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="663b5-111">Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans l’ordre correct.</span><span class="sxs-lookup"><span data-stu-id="663b5-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="663b5-112">L’opérateur contribue à la valeur de l’expression comme prévu.</span><span class="sxs-lookup"><span data-stu-id="663b5-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="663b5-113">Pour appeler une procédure d’opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="663b5-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="663b5-114">Utilisez `CType` à l’intérieur d’une expression.</span><span class="sxs-lookup"><span data-stu-id="663b5-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="663b5-115">Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans l’ordre correct.</span><span class="sxs-lookup"><span data-stu-id="663b5-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="663b5-116">`CType`appelle la procédure d’opérateur de conversion et retourne la valeur convertie.</span><span class="sxs-lookup"><span data-stu-id="663b5-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="663b5-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="663b5-117">Example</span></span>  
 <span data-ttu-id="663b5-118">L’exemple suivant crée deux <xref:System.TimeSpan>structures, les additionne et stocke le résultat dans une troisième <xref:System.TimeSpan>structure.</xref:System.TimeSpan> </xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="663b5-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="663b5-119">Le <xref:System.TimeSpan>structure définit des procédures d’opérateur pour surcharger plusieurs opérateurs standards.</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="663b5-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 <span data-ttu-id="663b5-120">[!code-vb[VbVbcnProcedures&#29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="663b5-120">[!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="663b5-121">Étant donné que <xref:System.TimeSpan>surcharges de la norme `+` (opérateur), l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan`.</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="663b5-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="663b5-122">Pour obtenir un exemple de l’appel de procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit les opérateurs](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="663b5-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="663b5-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="663b5-123">Compiling the Code</span></span>  
 <span data-ttu-id="663b5-124">Assurez-vous que la classe ou structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="663b5-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663b5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="663b5-125">See Also</span></span>  
 <span data-ttu-id="663b5-126">[Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-126">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="663b5-127"> [Comment : définir un opérateur](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-127"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="663b5-128"> [Comment : définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-128"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="663b5-129"> [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-129"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="663b5-130"> [Conversions étendues](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-130"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="663b5-131"> [Restrictives](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-131"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="663b5-132"> [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-132"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="663b5-133"> [Comment : déclarer une Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-133"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="663b5-134"> [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="663b5-134"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="663b5-135"> [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="663b5-135"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
