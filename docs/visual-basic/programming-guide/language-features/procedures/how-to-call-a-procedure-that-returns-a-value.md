---
title: "Comment : appeler une procédure qui retourne une valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6d408eed67fa417f42252bb49ecea28d4458382
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="28243-102">Comment : appeler une procédure qui retourne une valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28243-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="28243-103">A `Function` procédure retourne une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="28243-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="28243-104">Vous appeler en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="28243-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="28243-105">Pour appeler une procédure de fonction dans une expression</span><span class="sxs-lookup"><span data-stu-id="28243-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="28243-106">Utilisez le `Function` la même manière que vous utiliseriez une variable de nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="28243-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="28243-107">Vous pouvez utiliser un `Function` partout où vous pouvez utiliser une variable ou une constante dans une expression d’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="28243-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="28243-108">Suivez le nom de la procédure avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="28243-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="28243-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28243-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="28243-110">Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="28243-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="28243-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="28243-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="28243-112">Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="28243-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="28243-113">Ou bien, vous pouvez passer un ou plusieurs arguments par nom.</span><span class="sxs-lookup"><span data-stu-id="28243-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="28243-114">Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="28243-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="28243-115">La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou constante le ferait.</span><span class="sxs-lookup"><span data-stu-id="28243-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="28243-116">Pour appeler une procédure Function dans une instruction d’assignation</span><span class="sxs-lookup"><span data-stu-id="28243-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="28243-117">Utilisez le `Function` nom de la procédure suivante égaux (`=`) connectez-vous à l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="28243-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="28243-118">Suivez le nom de la procédure avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="28243-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="28243-119">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28243-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="28243-120">Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="28243-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="28243-121">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="28243-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="28243-122">Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants, sauf si vous les passez par nom.</span><span class="sxs-lookup"><span data-stu-id="28243-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="28243-123">La valeur retournée par la procédure est stockée dans la variable ou une propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="28243-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28243-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="28243-124">Example</span></span>  
 <span data-ttu-id="28243-125">L’exemple suivant appelle la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d’une variable d’environnement de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="28243-125">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="28243-126">La première ligne appelle `Environ` au sein d’une expression et la deuxième ligne l’appelle dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="28243-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="28243-127">`Environ`prend le nom de variable comme unique argument.</span><span class="sxs-lookup"><span data-stu-id="28243-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="28243-128">Elle retourne la valeur de la variable au code appelant.</span><span class="sxs-lookup"><span data-stu-id="28243-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="28243-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28243-129">See Also</span></span>  
 [<span data-ttu-id="28243-130">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="28243-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="28243-131">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="28243-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="28243-132">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="28243-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="28243-133">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="28243-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="28243-134">Guide pratique : retourner une valeur d’une procédure</span><span class="sxs-lookup"><span data-stu-id="28243-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="28243-135">Guide pratique : appeler une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="28243-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
