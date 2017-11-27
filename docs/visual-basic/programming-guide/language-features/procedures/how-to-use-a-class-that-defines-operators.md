---
title: "Comment : utiliser une classe qui définit des opérateurs (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="082ef-102">Comment : utiliser une classe qui définit des opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="082ef-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="082ef-103">Si vous utilisez une classe ou structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs à partir de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="082ef-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="082ef-104">Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="082ef-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="082ef-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="082ef-105">Example</span></span>  
 <span data-ttu-id="082ef-106">L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString>, qui définit les opérateurs de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) dans les deux sens entre une chaîne SQL et une [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chaîne.</span><span class="sxs-lookup"><span data-stu-id="082ef-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="082ef-107">Utilisez `CType(` *expression de chaîne SQL*, `String)` pour convertir une chaîne SQL pour un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chaîne, et `CType(` *expression de chaîne Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` à convertir dans l’autre direction.</span><span class="sxs-lookup"><span data-stu-id="082ef-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="082ef-108">Le <xref:System.Data.SqlTypes.SqlString> structure définit un opérateur de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) à partir de `String` à <xref:System.Data.SqlTypes.SqlString> et l’autre à partir de <xref:System.Data.SqlTypes.SqlString> à `String`.</span><span class="sxs-lookup"><span data-stu-id="082ef-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="082ef-109">L’instruction qui assigne `title` à `jobTitle` utilise le premier opérateur et la <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> appel de fonction utilise le second.</span><span class="sxs-lookup"><span data-stu-id="082ef-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="082ef-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="082ef-110">Compiling the Code</span></span>  
 <span data-ttu-id="082ef-111">Assurez-vous que la classe ou structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="082ef-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="082ef-112">Ne supposez pas que la classe ou structure a défini chaque opérateur disponible pour la surcharge.</span><span class="sxs-lookup"><span data-stu-id="082ef-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="082ef-113">Pour obtenir la liste des opérateurs disponibles, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="082ef-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="082ef-114">Inclure les `Imports` instruction pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="082ef-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="082ef-115">Votre projet doit avoir des références à System.Data et System.XML.</span><span class="sxs-lookup"><span data-stu-id="082ef-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="082ef-116">See Also</span></span>  
 [<span data-ttu-id="082ef-117">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="082ef-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="082ef-118">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="082ef-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="082ef-119">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="082ef-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="082ef-120">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="082ef-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="082ef-121">Widening</span><span class="sxs-lookup"><span data-stu-id="082ef-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="082ef-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="082ef-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="082ef-123">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="082ef-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="082ef-124">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="082ef-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="082ef-125">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="082ef-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="082ef-126">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="082ef-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
