---
title: "Procédures Function (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9520a6555e65fd801a5c40d40748028e04a10739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="d3520-102">Procédures Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3520-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="d3520-103">A `Function` procédure est une série de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instructions délimitée par le `Function` et `End Function` instructions.</span><span class="sxs-lookup"><span data-stu-id="d3520-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="d3520-104">Le `Function` procédure effectue une tâche, puis retourne le contrôle au code appelant.</span><span class="sxs-lookup"><span data-stu-id="d3520-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="d3520-105">Lorsqu’elle retourne le contrôle, il retourne également une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="d3520-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="d3520-106">Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après le `Function` instruction et en terminant par la première `End Function`, `Exit Function`, ou `Return` instruction rencontrée.</span><span class="sxs-lookup"><span data-stu-id="d3520-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="d3520-107">Vous pouvez définir un `Function` procédure dans un module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="d3520-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="d3520-108">Il est `Public` par défaut, ce qui signifie que vous pouvez l’appeler à partir de n’importe où dans votre application qui a accès pour le module, classe ou structure dans laquelle vous l’avez définie.</span><span class="sxs-lookup"><span data-stu-id="d3520-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="d3520-109">A `Function` procédure peut prendre des arguments, tels que des constantes, variables ou expressions qui lui sont passées par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d3520-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="d3520-110">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="d3520-110">Declaration Syntax</span></span>  
 <span data-ttu-id="d3520-111">La syntaxe de déclaration d’un `Function` comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3520-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="d3520-112">Le *modificateurs* peut spécifier des informations concernant la surcharge, la substitution, le partage et l’occultation et niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="d3520-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="d3520-113">Pour plus d’informations, consultez [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3520-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="d3520-114">Vous déclarez chaque paramètre de la même façon que vous le feriez pour [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d3520-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="d3520-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="d3520-115">Data Type</span></span>  
 <span data-ttu-id="d3520-116">Chaque `Function` procédure possède un type de données, de fait de simplement chaque variable.</span><span class="sxs-lookup"><span data-stu-id="d3520-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="d3520-117">Ce type de données est spécifié par le `As` clause dans la `Function` instruction, qui détermine le type de données de la valeur de la fonction retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="d3520-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="d3520-118">Les exemples de déclarations suivantes illustrent ce principe.</span><span class="sxs-lookup"><span data-stu-id="d3520-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="d3520-119">Pour plus d’informations, consultez « Éléments » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3520-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="d3520-120">Retour de valeurs</span><span class="sxs-lookup"><span data-stu-id="d3520-120">Returning Values</span></span>  
 <span data-ttu-id="d3520-121">La valeur un `Function` procédure envoie précédent pour le code appelant est appelée sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="d3520-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="d3520-122">La procédure retourne cette valeur de deux manières :</span><span class="sxs-lookup"><span data-stu-id="d3520-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="d3520-123">Elle utilise le `Return` contrôler l’instruction pour spécifier la valeur de retour et retourne immédiatement au programme appelant.</span><span class="sxs-lookup"><span data-stu-id="d3520-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="d3520-124">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="d3520-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="d3520-125">Il assigne une valeur à son propre nom de fonction dans une ou plusieurs instructions de la procédure.</span><span class="sxs-lookup"><span data-stu-id="d3520-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="d3520-126">Contrôle ne retourne pas au programme appelant jusqu'à un `Exit Function` ou `End Function` instruction est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d3520-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="d3520-127">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="d3520-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="d3520-128">L’avantage de l’affectation de la valeur de retour pour le nom de fonction est que le contrôle ne retourne pas de la procédure, jusqu'à ce qu’il rencontre un `Exit Function` ou `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="d3520-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="d3520-129">Cela vous permet d’assigner une valeur préliminaire ajuster ultérieurement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d3520-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="d3520-130">Pour plus d’informations sur le renvoi de valeurs, consultez [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3520-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="d3520-131">Pour plus d’informations sur le renvoi des tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3520-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="d3520-132">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="d3520-132">Calling Syntax</span></span>  
 <span data-ttu-id="d3520-133">Vous appelez un `Function` procédure en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="d3520-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="d3520-134">Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d3520-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="d3520-135">Si aucun argument n’est fourni, vous pouvez omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d3520-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="d3520-136">La syntaxe d’un appel à un `Function` comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3520-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="d3520-137">*lvalue*`=`*functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="d3520-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="d3520-138">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=` *expression*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="d3520-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="d3520-139">Lorsque vous appelez un `Function` procédure, il est inutile d’utiliser sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="d3520-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="d3520-140">Si vous ne le faites pas, toutes les actions de la fonction sont effectuées, mais la valeur de retour est ignorée.</span><span class="sxs-lookup"><span data-stu-id="d3520-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="d3520-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>est souvent appelé de cette manière.</span><span class="sxs-lookup"><span data-stu-id="d3520-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="d3520-142">Illustration de déclaration et d’appel</span><span class="sxs-lookup"><span data-stu-id="d3520-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="d3520-143">Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, selon les valeurs des deux autres côtés.</span><span class="sxs-lookup"><span data-stu-id="d3520-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="d3520-144">L’exemple suivant montre un appel typique à `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="d3520-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3520-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3520-145">See Also</span></span>  
 [<span data-ttu-id="d3520-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="d3520-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d3520-147">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="d3520-147">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="d3520-148">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="d3520-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="d3520-149">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="d3520-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="d3520-150">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="d3520-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d3520-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="d3520-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="d3520-152">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="d3520-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="d3520-153">Guide pratique : retourner une valeur d’une procédure</span><span class="sxs-lookup"><span data-stu-id="d3520-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="d3520-154">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="d3520-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
