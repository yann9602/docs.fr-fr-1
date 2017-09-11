---
title: "Comment : appeler une procédure qui retourne une valeur (Visual Basic) | Documents Microsoft"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
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
ms.openlocfilehash: cc1e274a705618213c830d7cf4f61a5e64afd980
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="03502-102">Comment : appeler une procédure qui retourne une valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03502-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="03502-103">Un `Function` procédure retourne une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="03502-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="03502-104">Vous l’appeler en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="03502-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="03502-105">Pour appeler une procédure Function dans une expression</span><span class="sxs-lookup"><span data-stu-id="03502-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="03502-106">Utilisez la `Function` la même manière que vous utiliseriez une variable de nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="03502-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="03502-107">Vous pouvez utiliser un `Function` partout où vous pouvez utiliser une variable ou une constante dans une expression d’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="03502-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="03502-108">Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="03502-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="03502-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="03502-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="03502-110">Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="03502-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="03502-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="03502-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="03502-112">Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="03502-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="03502-113">Vous pouvez également passer un ou plusieurs arguments par nom.</span><span class="sxs-lookup"><span data-stu-id="03502-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="03502-114">Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="03502-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="03502-115">La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou constante le ferait.</span><span class="sxs-lookup"><span data-stu-id="03502-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="03502-116">Pour appeler une procédure Function dans une instruction d’assignation</span><span class="sxs-lookup"><span data-stu-id="03502-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="03502-117">Utilisez le `Function` nom de procédure suivant égaux (`=`) connectez-vous à l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="03502-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="03502-118">Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="03502-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="03502-119">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="03502-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="03502-120">Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="03502-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="03502-121">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="03502-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="03502-122">Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants, à moins que vous les passiez par nom.</span><span class="sxs-lookup"><span data-stu-id="03502-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="03502-123">La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="03502-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03502-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="03502-124">Example</span></span>  
 <span data-ttu-id="03502-125">L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>pour récupérer la valeur d’une variable d’environnement de système d’exploitation.</xref:Microsoft.VisualBasic.Interaction.Environ%2A></span><span class="sxs-lookup"><span data-stu-id="03502-125">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="03502-126">La première ligne appelle `Environ` au sein d’une expression et la deuxième ligne l’appelle dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="03502-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="03502-127">`Environ`prend le nom de variable comme unique argument.</span><span class="sxs-lookup"><span data-stu-id="03502-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="03502-128">Elle retourne la valeur de la variable au code appelant.</span><span class="sxs-lookup"><span data-stu-id="03502-128">It returns the variable's value to the calling code.</span></span>  
  
 <span data-ttu-id="03502-129">[!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="03502-129">[!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03502-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03502-130">See Also</span></span>  
 <span data-ttu-id="03502-131">[Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="03502-131">[Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="03502-132"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="03502-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="03502-133"> [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="03502-133"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="03502-134"> [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="03502-134"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="03502-135"> [Comment : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="03502-135"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="03502-136"> [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="03502-136"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
