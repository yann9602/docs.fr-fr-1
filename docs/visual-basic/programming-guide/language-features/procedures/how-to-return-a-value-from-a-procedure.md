---
title: "Comment : retourner une valeur d'une procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="cfd15-102">Comment : retourner une valeur d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfd15-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cfd15-103">A `Function` procédure retourne une valeur au code appelant soit en exécutant une `Return` instruction ou en utilisant un `Exit Function` ou `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="cfd15-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="cfd15-104">Pour retourner une valeur à l’aide de l’instruction Return</span><span class="sxs-lookup"><span data-stu-id="cfd15-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="cfd15-105">Placer un `Return` instruction au point où la procédure est terminée.</span><span class="sxs-lookup"><span data-stu-id="cfd15-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="cfd15-106">Suivez le `Return` mot clé avec une expression qui génère la valeur que vous souhaitez retourner au code appelant.</span><span class="sxs-lookup"><span data-stu-id="cfd15-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="cfd15-107">Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="cfd15-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="cfd15-108">Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle et le retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="cfd15-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="cfd15-109">L’exemple suivant montre un appel typique à `hypotenuse`, qui stocke la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="cfd15-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="cfd15-110">Pour retourner une valeur à l’aide de la fonction de sortie ou fin</span><span class="sxs-lookup"><span data-stu-id="cfd15-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="cfd15-111">Au moins un endroit dans le `Function` procédure, assignez une valeur au nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="cfd15-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="cfd15-112">Lorsque vous exécutez un `Exit Function` ou `End Function` instruction, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] retourne la valeur la plus récemment assignée au nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="cfd15-112">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="cfd15-113">Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="cfd15-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="cfd15-114">Vous pouvez avoir qu’un seul `End Function` instruction dans un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="cfd15-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="cfd15-115">Pour plus d’informations et un exemple, consultez « Valeur de retour » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cfd15-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd15-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfd15-116">See Also</span></span>  
 [<span data-ttu-id="cfd15-117">Procédures</span><span class="sxs-lookup"><span data-stu-id="cfd15-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="cfd15-118">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="cfd15-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="cfd15-119">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="cfd15-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="cfd15-120">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="cfd15-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="cfd15-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="cfd15-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="cfd15-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="cfd15-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="cfd15-123">Return (instruction)</span><span class="sxs-lookup"><span data-stu-id="cfd15-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="cfd15-124">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="cfd15-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="cfd15-125">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="cfd15-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
