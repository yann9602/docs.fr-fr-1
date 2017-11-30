---
title: "Comment : définir un opérateur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="70b51-102">Comment : définir un opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70b51-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="70b51-103">Si vous avez défini une classe ou structure, vous pouvez définir le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) lorsqu’au moins des opérandes est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="70b51-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="70b51-104">Définissez l’opérateur standard comme une procédure d’opérateur dans la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="70b51-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="70b51-105">Toutes les procédures d’opérateur doivent être `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="70b51-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="70b51-106">Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="70b51-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b51-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="70b51-107">Example</span></span>  
 <span data-ttu-id="70b51-108">L’exemple suivant définit la `+` opérateur pour une structure appelée `height`.</span><span class="sxs-lookup"><span data-stu-id="70b51-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="70b51-109">La structure utilise des hauteurs exprimées en pieds et pouces.</span><span class="sxs-lookup"><span data-stu-id="70b51-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="70b51-110">Un *pouces* 2,54 centimètres, et à un *foot* est de 12 pouces.</span><span class="sxs-lookup"><span data-stu-id="70b51-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="70b51-111">Pour garantir des valeurs normalisées (pouces < 12.0), le constructeur effectue *modulo* 12 arithmétique.</span><span class="sxs-lookup"><span data-stu-id="70b51-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="70b51-112">Le `+` opérateur utilise le constructeur pour générer des valeurs normalisées.</span><span class="sxs-lookup"><span data-stu-id="70b51-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="70b51-113">Vous pouvez tester la structure `height` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="70b51-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="70b51-114">Pour obtenir plus d’informations et des exemples, consultez [Surcharge d’opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="70b51-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b51-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70b51-115">See Also</span></span>  
 [<span data-ttu-id="70b51-116">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="70b51-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="70b51-117">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="70b51-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="70b51-118">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="70b51-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="70b51-119">Guide pratique : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="70b51-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="70b51-120">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="70b51-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="70b51-121">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="70b51-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="70b51-122">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="70b51-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="70b51-123">Mod (opérateur)</span><span class="sxs-lookup"><span data-stu-id="70b51-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
