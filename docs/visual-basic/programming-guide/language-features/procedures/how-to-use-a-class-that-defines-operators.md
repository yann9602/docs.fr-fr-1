---
title: "Comment : utiliser une classe qui définit des opérateurs (Visual Basic) | Documents Microsoft"
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
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
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
ms.openlocfilehash: e4d76788346e08123102d56088c0a1e0f5f2238f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="456ab-102">Comment : utiliser une classe qui définit des opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456ab-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="456ab-103">Si vous utilisez une classe ou structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="456ab-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="456ab-104">Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="456ab-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="456ab-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="456ab-105">Example</span></span>  
 <span data-ttu-id="456ab-106">L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString>, qui définit les opérateurs de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) dans les deux sens entre une chaîne SQL et une [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chaîne.</xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="456ab-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string.</span></span> <span data-ttu-id="456ab-107">Utilisez `CType(` *expression de chaîne SQL*, `String)` pour convertir une chaîne SQL pour un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chaîne, et `CType(` *expression de chaîne Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` convertir dans l’autre direction.</xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="456ab-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 <span data-ttu-id="456ab-108">[!code-vb[30 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="456ab-108">[!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="456ab-109">[!code-vb[VbVbcnProcedures&#31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="456ab-109">[!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="456ab-110">Le <xref:System.Data.SqlTypes.SqlString>structure définit un opérateur de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) à partir de `String` à <xref:System.Data.SqlTypes.SqlString>et l’autre à partir de <xref:System.Data.SqlTypes.SqlString>à `String`.</xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="456ab-110">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="456ab-111">L’instruction qui assigne `title` à `jobTitle` utilise le premier opérateur et le <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>appel de fonction utilise le second.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="456ab-111">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="456ab-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="456ab-112">Compiling the Code</span></span>  
 <span data-ttu-id="456ab-113">Assurez-vous que la classe ou structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="456ab-113">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="456ab-114">Ne supposez pas que la classe ou la structure a défini chaque opérateur comme disponible pour la surcharge.</span><span class="sxs-lookup"><span data-stu-id="456ab-114">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="456ab-115">Pour obtenir la liste des opérateurs disponibles, consultez la page [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="456ab-115">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="456ab-116">Inclure approprié `Imports` instruction pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes>).</xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="456ab-116">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="456ab-117">Votre projet doit contenir des références à System.Data et System.XML.</span><span class="sxs-lookup"><span data-stu-id="456ab-117">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456ab-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="456ab-118">See Also</span></span>  
 <span data-ttu-id="456ab-119">[Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-119">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="456ab-120"> [Comment : définir un opérateur](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-120"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="456ab-121"> [Comment : définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-121"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="456ab-122"> [Comment : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-122"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="456ab-123"> [Conversions étendues](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-123"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="456ab-124"> [Restrictives](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-124"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="456ab-125"> [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-125"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="456ab-126"> [Comment : déclarer une Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-126"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="456ab-127"> [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="456ab-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="456ab-128"> [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="456ab-128"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
