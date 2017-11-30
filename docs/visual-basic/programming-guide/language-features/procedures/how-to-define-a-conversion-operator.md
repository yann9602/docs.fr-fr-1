---
title: "Comment : définir un opérateur de conversion (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="7bd98-102">Comment : définir un opérateur de conversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bd98-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="7bd98-103">Si vous avez défini une classe ou structure, vous pouvez définir un opérateur de conversion de type entre le type de votre classe ou structure et un autre type de données (tel que `Integer`, `Double`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="7bd98-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="7bd98-104">Définir la conversion de type comme un [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) procédure au sein de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="7bd98-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="7bd98-105">Toutes les procédures de conversion doivent être `Public Shared`, et chacune d’elles doit spécifier [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="7bd98-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="7bd98-106">Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="7bd98-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd98-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bd98-107">Example</span></span>  
 <span data-ttu-id="7bd98-108">L’exemple suivant définit les opérateurs de conversion entre une structure appelée `digit` et un `Byte`.</span><span class="sxs-lookup"><span data-stu-id="7bd98-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="7bd98-109">Vous pouvez tester la structure `digit` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7bd98-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7bd98-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bd98-110">See Also</span></span>  
 [<span data-ttu-id="7bd98-111">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="7bd98-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="7bd98-112">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="7bd98-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="7bd98-113">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="7bd98-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="7bd98-114">Guide pratique : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="7bd98-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="7bd98-115">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="7bd98-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="7bd98-116">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="7bd98-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="7bd98-117">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="7bd98-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="7bd98-118">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="7bd98-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="7bd98-119">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="7bd98-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
