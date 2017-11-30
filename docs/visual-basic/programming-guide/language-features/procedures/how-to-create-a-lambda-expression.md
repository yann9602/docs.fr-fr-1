---
title: "Comment : créer une expression lambda (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Comment : créer une expression lambda (Visual Basic)
A *expression lambda* est une fonction ou une sous-routine qui n’a pas de nom. Une expression lambda peut être utilisée partout où un type délégué est valid.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Pour créer une fonction d’expression lambda sur une ligne  
  
1.  Dans toute situation où un type délégué peut être utilisé, tapez le mot clé `Function`, comme dans l’exemple suivant :  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction. Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Après la liste de paramètres, tapez une expression unique comme corps de la fonction. La valeur de l’expression prend la valeur est la valeur retournée par la fonction. Vous n’utilisez pas un `As` clause pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Vous appelez l’expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Vous pouvez également le même résultat s’effectue par l’exemple suivant :  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Pour créer une sous-routine d’expression lambda sur une ligne  
  
1.  Dans toute situation où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme illustré dans l’exemple suivant.  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine. Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  À la suite de la liste de paramètres, tapez une instruction unique comme corps de la sous-routine.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Vous appelez l’expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Pour créer une fonction d’expression lambda multiligne  
  
1.  Dans toute situation où un type délégué peut être utilisé, tapez le mot clé `Function`, comme illustré dans l’exemple suivant.  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction. Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Appuyez sur Entrée. La `End Function` instruction est ajoutée automatiquement.  
  
4.  Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et la valeur de retour. Vous n’utilisez pas un `As` clause pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Vous appelez l’expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Pour créer une sous-routine d’expression lambda multiligne  
  
1.  Dans toute situation où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme illustré dans l’exemple suivant :  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous-routine. Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Appuyez sur Entrée. La `End Sub` instruction est ajoutée automatiquement.  
  
4.  Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous-routine est appelée.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Vous appelez l’expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Exemple  
 Une utilisation courante des expressions lambda consiste à définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate`. Dans l’exemple suivant, la <xref:System.Diagnostics.Process.GetProcesses%2A> méthode retourne un tableau des processus en cours d’exécution sur l’ordinateur local. Le <xref:System.Linq.Enumerable.Where%2A> méthode à partir de la <xref:System.Linq.Enumerable> classe requiert un `Boolean` délégué en tant que son argument. L’expression lambda dans l’exemple est utilisée à cet effet. Elle retourne `True` pour chaque processus qui a un seul thread, et ceux sélectionnés dans `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 L’exemple précédent équivaut au code suivant, qui est écrit dans [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxe :  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable>  
 [Expressions lambda](./lambda-expressions.md)  
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Guide pratique : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Delegate (instruction)](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
