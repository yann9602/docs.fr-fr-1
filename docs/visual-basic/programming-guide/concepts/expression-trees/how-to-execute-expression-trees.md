---
title: "Comment : exécuter des arborescences d’Expression (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e12c45b417310f097d597561b2652ee793a4b2c0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Comment : exécuter des arborescences d’Expression (Visual Basic)
Cette rubrique montre comment exécuter une arborescence d’expression. L’exécution d’une arborescence d’expression peut retourner une valeur, ou il peut simplement effectuer une action telle que l’appel d’une méthode.  
  
 Seules les arborescences d’expression qui représentent des expressions lambda peuvent être exécutées. Arborescences d’expression qui représentent des expressions lambda sont de type <xref:System.Linq.Expressions.LambdaExpression>ou <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression> Pour exécuter ces arborescences d’expression, appelez le <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>méthode pour créer un délégué exécutable, puis appelez le délégué.</xref:System.Linq.Expressions.LambdaExpression.Compile%2A>  
  
> [!NOTE]
>  Si le type du délégué n’est pas connu, autrement dit, l’expression lambda est de type <xref:System.Linq.Expressions.LambdaExpression>et non <xref:System.Linq.Expressions.Expression%601>, vous devez appeler la <xref:System.Delegate.DynamicInvoke%2A>méthode sur le délégué au lieu d’appeler directement.</xref:System.Delegate.DynamicInvoke%2A> </xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression>  
  
 Si une arborescence d’expression ne représente pas une expression lambda, vous pouvez créer une expression lambda qui possède l’arborescence d’expression d’origine comme étant son corps, en appelant le <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>méthode.</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> Ensuite, vous pouvez exécuter l’expression lambda comme décrit précédemment dans cette section.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment exécuter une arborescence d’expression qui représente l’élévation d’un nombre à une puissance en créant une expression lambda et en l’exécutant. Le résultat, qui représente le nombre élevé à la puissance, est affiché.  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Ajoutez une référence de projet à System.Core.dll si elle n’est pas déjà référencée.  
  
-   Inclure l’espace de noms System.Linq.Expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Comment : modifier des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
