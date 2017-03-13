---
title: "How to: Create a Lambda Expression (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# How to: Create a Lambda Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une *expression lambda* est une fonction ou une sous\-routine qui n'a pas de nom.  Une expression lambda peut être utilisée chaque fois qu'un type délégué est valide.  
  
### Pour créer une fonction d'expression lambda sur une ligne  
  
1.  Dans tous les cas où un type délégué peut être utilisé, tapez le mot clé `Function`, comme dans l'exemple suivant :  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.  Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  À la suite de la liste de paramètres, tapez une expression unique comme corps de la fonction.  La valeur que prend l'expression est celle retournée par la fonction.  Vous n'utilisez pas de clause `As` pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Vous appelez l'expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Le même résultat est également obtenu par l'exemple suivant :  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### Pour créer une sous\-routine d'expression lambda sur une ligne  
  
1.  Dans tous les cas où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme dans l'exemple suivant.  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous\-routine.  Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  À la suite de la liste de paramètres, tapez une instruction unique comme corps de la sous\-routine.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Vous appelez l'expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### Pour créer une fonction d'expression lambda sur plusieurs lignes  
  
1.  Dans tous les cas où un type délégué peut être utilisé, tapez le mot clé `Function`, comme dans l'exemple suivant.  
  
     `Dim add1 =`   `Function`  
  
2.  Entre parenthèses, directement après `Function`, tapez les paramètres de la fonction.  Notez que vous ne spécifiez pas de nom après `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Appuyez sur ENTRÉE.  L'instruction `End Function` est ajoutée automatiquement.  
  
4.  Dans le corps de la fonction, ajoutez le code suivant pour créer une expression et retourner la valeur.  Vous n'utilisez pas de clause `As` pour spécifier le type de retour.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Vous appelez l'expression lambda en passant un argument entier.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### Pour créer une sous\-routine d'expression lambda sur plusieurs lignes  
  
1.  Dans tous les cas où un type délégué peut être utilisé, tapez le mot clé `Sub`, comme dans l'exemple suivant :  
  
     `Dim add1 =`   `Sub`  
  
2.  Entre parenthèses, directement après `Sub`, tapez les paramètres de la sous\-routine.  Notez que vous ne spécifiez pas de nom après `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Appuyez sur ENTRÉE.  L'instruction `End Sub` est ajoutée automatiquement.  
  
4.  Dans le corps de la fonction, ajoutez le code suivant à exécuter lorsque la sous\-routine est appelée.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Vous appelez l'expression lambda en passant un argument de chaîne.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## Exemple  
 Les expressions lambda sont couramment utilisées pour définir une fonction qui peut être passée comme argument pour un paramètre dont le type est `Delegate`.  Dans l'exemple suivant, la méthode <xref:System.Diagnostics.Process.GetProcesses%2A> retourne un tableau des processus en cours d'exécution sur l'ordinateur local.  La méthode <xref:System.Linq.Enumerable.Where%2A> de la classe <xref:System.Linq.Enumerable> requiert un délégué `Boolean` comme argument.  L'expression lambda de l'exemple est utilisée à cette fin.  Elle retourne la valeur `True` pour chacun des processus possédant un thread unique, ceux\-ci étant sélectionnés dans `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 L'exemple précédent est équivalent au code suivant, écrit en syntaxe [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] :  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## Voir aussi  
 <xref:System.Linq.Enumerable>   
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)