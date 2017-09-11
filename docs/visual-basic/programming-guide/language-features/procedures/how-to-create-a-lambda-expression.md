---
title: "Comment : créer une Expression Lambda (Visual Basic) | Documents Microsoft"
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
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.openlocfilehash: edd475490dce81ff9cca32b5f9a5090d99f4d80d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="b5d2a-102">Comment : créer une expression lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5d2a-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="b5d2a-103">A *expression lambda* est une fonction ou une sous-routine qui n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="b5d2a-104">Une expression lambda peut être utilisée partout où un type délégué est valide.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="b5d2a-105">Pour créer une fonction d’expression lambda sur une ligne</span><span class="sxs-lookup"><span data-stu-id="b5d2a-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="b5d2a-106">Dans les cas où un type délégué peut être utilisé, tapez le mot clé `Function`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b5d2a-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="b5d2a-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="b5d2a-108">Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b5d2a-109">Notez que vous ne spécifiez pas de nom après `Function`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b5d2a-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="b5d2a-111">À la suite de la liste de paramètres, tapez une expression unique dans le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="b5d2a-112">La valeur que l’expression prend la valeur est la valeur retournée par la fonction.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="b5d2a-113">Vous n’utilisez pas un `As` clause pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="b5d2a-114">[!code-vb[VbVbalrLambdas n °&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-114">[!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span></span>  
  
     <span data-ttu-id="b5d2a-115">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="b5d2a-116">[!code-vb[VbVbalrLambdas n °&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-116">[!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span></span>  
  
4.  <span data-ttu-id="b5d2a-117">Vous pouvez également le même résultat est effectué par l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b5d2a-117">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     <span data-ttu-id="b5d2a-118">[!code-vb[VbVbalrLambdas n °&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-118">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="b5d2a-119">Pour créer une sous-routine d’expression lambda sur une ligne</span><span class="sxs-lookup"><span data-stu-id="b5d2a-119">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="b5d2a-120">Dans les cas où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-120">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b5d2a-121">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-121">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="b5d2a-122">Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-122">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b5d2a-123">Notez que vous ne spécifiez pas de nom après `Sub`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-123">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b5d2a-124">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-124">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="b5d2a-125">À la suite de la liste de paramètres, tapez une instruction unique comme corps de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-125">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     <span data-ttu-id="b5d2a-126">[!code-vb[VbVbalrLambdas&#17;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-126">[!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span></span>  
  
     <span data-ttu-id="b5d2a-127">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-127">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="b5d2a-128">[!code-vb[VbVbalrLambdas&#18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-128">[!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="b5d2a-129">Pour créer une fonction d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="b5d2a-129">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="b5d2a-130">Dans les cas où un type délégué peut être utilisé, tapez le mot clé `Function`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-130">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b5d2a-131">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-131">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="b5d2a-132">Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-132">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b5d2a-133">Notez que vous ne spécifiez pas de nom après `Function`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-133">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b5d2a-134">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-134">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="b5d2a-135">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-135">Press ENTER.</span></span> <span data-ttu-id="b5d2a-136">La `End Function` instruction est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-136">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="b5d2a-137">Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-137">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="b5d2a-138">Vous n’utilisez pas un `As` clause pour spécifier le type de retour.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-138">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="b5d2a-139">[!code-vb[VbVbalrLambdas n °&19;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-139">[!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span></span>  
  
     <span data-ttu-id="b5d2a-140">Vous appelez l’expression lambda en passant un argument entier.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-140">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="b5d2a-141">[!code-vb[VbVbalrLambdas&#20;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-141">[!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="b5d2a-142">Pour créer une sous-routine d’expression lambda multiligne</span><span class="sxs-lookup"><span data-stu-id="b5d2a-142">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="b5d2a-143">Dans les cas où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b5d2a-143">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="b5d2a-144">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-144">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="b5d2a-145">Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-145">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b5d2a-146">Notez que vous ne spécifiez pas de nom après `Sub`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-146">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b5d2a-147">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b5d2a-147">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="b5d2a-148">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-148">Press ENTER.</span></span> <span data-ttu-id="b5d2a-149">La `End Sub` instruction est automatiquement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-149">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="b5d2a-150">Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous-routine est appelée.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-150">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     <span data-ttu-id="b5d2a-151">[!code-vb[VbVbalrLambdas n °&21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-151">[!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span></span>  
  
     <span data-ttu-id="b5d2a-152">Vous appelez l’expression lambda en passant un argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-152">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="b5d2a-153">[!code-vb[VbVbalrLambdas&#22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-153">[!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5d2a-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5d2a-154">Example</span></span>  
 <span data-ttu-id="b5d2a-155">Une utilisation courante des expressions lambda est de définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-155">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="b5d2a-156">Dans l’exemple suivant, le <xref:System.Diagnostics.Process.GetProcesses%2A>renvoie un tableau des processus en cours d’exécution sur l’ordinateur local.</xref:System.Diagnostics.Process.GetProcesses%2A></span><span class="sxs-lookup"><span data-stu-id="b5d2a-156">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="b5d2a-157">Le <xref:System.Linq.Enumerable.Where%2A>méthode à partir de la <xref:System.Linq.Enumerable>classe nécessite une `Boolean` délégué comme argument.</xref:System.Linq.Enumerable> </xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="b5d2a-157">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="b5d2a-158">L’expression lambda dans l’exemple est utilisée à cet effet.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-158">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="b5d2a-159">Elle retourne `True` pour chaque processus qui n’a qu’un seul thread et celles sélectionnées dans `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="b5d2a-159">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 <span data-ttu-id="b5d2a-160">[!code-vb[VbVbalrLambdas&#10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-160">[!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span></span>  
  
 <span data-ttu-id="b5d2a-161">L’exemple précédent équivaut au code suivant, qui est écrit dans [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] syntaxe :</span><span class="sxs-lookup"><span data-stu-id="b5d2a-161">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] syntax:</span></span>  
  
 <span data-ttu-id="b5d2a-162">[!code-vb[VbVbalrLambdas&#11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="b5d2a-162">[!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d2a-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5d2a-163">See Also</span></span>  
 <span data-ttu-id="b5d2a-164"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="b5d2a-164"><xref:System.Linq.Enumerable></span></span>   
<span data-ttu-id="b5d2a-165"> [Expressions lambda](./lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-165"> [Lambda Expressions](./lambda-expressions.md) </span></span>  
<span data-ttu-id="b5d2a-166"> [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-166"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="b5d2a-167"> [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-167"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="b5d2a-168"> [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-168"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="b5d2a-169"> [Comment : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-169"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="b5d2a-170"> [Delegate, instruction](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b5d2a-170"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="b5d2a-171"> [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b5d2a-171"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
