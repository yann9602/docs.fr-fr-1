---
title: "Comment : retourner une valeur d’une procédure (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 601cd3adca0105eb829bb6156f94289b5c9f5f72
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="28854-102">Comment : retourner une valeur d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28854-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="28854-103">A `Function` procédure retourne une valeur au code appelant soit en exécutant une `Return` instruction ou en utilisant un `Exit Function` ou `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="28854-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="28854-104">Pour retourner une valeur à l’aide de l’instruction Return</span><span class="sxs-lookup"><span data-stu-id="28854-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="28854-105">Placer un `Return` instruction au point où la tâche de la procédure est terminée.</span><span class="sxs-lookup"><span data-stu-id="28854-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="28854-106">Suivez le `Return` mot clé avec une expression qui retourne la valeur que vous souhaitez retourner au code appelant.</span><span class="sxs-lookup"><span data-stu-id="28854-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="28854-107">Vous pouvez avoir plusieurs `Return` instruction dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="28854-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="28854-108">Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle et le retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="28854-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     <span data-ttu-id="28854-109">[!code-vb[VbVbcnProcedures n °&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="28854-109">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="28854-110">L’exemple suivant montre un appel typique à `hypotenuse`, qui stocke la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="28854-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     <span data-ttu-id="28854-111">[!code-vb[VbVbcnProcedures n °&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="28854-111">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span></span>  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="28854-112">Pour retourner une valeur à l’aide de la fonction de sortie ou fin</span><span class="sxs-lookup"><span data-stu-id="28854-112">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="28854-113">Au moins un endroit dans le `Function` procédure, assignez une valeur au nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="28854-113">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="28854-114">Lorsque vous exécutez un `Exit Function` ou `End Function` instruction, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] renvoie la valeur la plus récemment assignée au nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="28854-114">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="28854-115">Vous pouvez avoir plusieurs `Exit Function` instruction dans la même procédure et vous pouvez mélanger `Return` et `Exit Function` instructions dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="28854-115">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="28854-116">Vous pouvez avoir un seul `End Function` instruction dans un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="28854-116">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="28854-117">Pour plus d’informations et un exemple, consultez « Valeur de retour » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="28854-117">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28854-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28854-118">See Also</span></span>  
 <span data-ttu-id="28854-119">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="28854-119">[Procedures](./index.md) </span></span>  
<span data-ttu-id="28854-120"> [Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="28854-120"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="28854-121"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="28854-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="28854-122"> [Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="28854-122"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="28854-123"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="28854-123"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="28854-124"> [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="28854-124"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="28854-125"> [Return (instruction)](../../../../visual-basic/language-reference/statements/return-statement.md) </span><span class="sxs-lookup"><span data-stu-id="28854-125"> [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md) </span></span>  
<span data-ttu-id="28854-126"> [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="28854-126"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="28854-127"> [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="28854-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
