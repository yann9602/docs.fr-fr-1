---
title: "Comment : modifier des arborescences d’Expression (Visual Basic) | Documents Microsoft"
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
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fb4e818eed7d6547e091c914d40b3ce87af59512
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Comment : modifier des arborescences d’Expression (Visual Basic)
Cette rubrique montre comment modifier une arborescence d’expression. Les arborescences d’expression sont immuables, ce qui signifie qu’ils ne peuvent pas être modifiés directement. Pour modifier une arborescence d’expression, vous devez créer une copie d’une arborescence d’expression existante et lorsque vous créez la copie, apportez les modifications requises. Vous pouvez utiliser la <xref:System.Linq.Expressions.ExpressionVisitor>classe pour parcourir une arborescence d’expression existante et copier chaque nœud visité.</xref:System.Linq.Expressions.ExpressionVisitor>  
  
### <a name="to-modify-an-expression-tree"></a>Pour modifier une arborescence d’expression  
  
1.  Créer un nouveau **Application Console** projet.  
  
2.  Ajouter un `Imports` instruction dans le fichier pour le `System.Linq.Expressions` espace de noms.  
  
3.  Ajouter la `AndAlsoModifier` classe à votre projet.  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     Cette classe hérite de la <xref:System.Linq.Expressions.ExpressionVisitor>classe et est spécialisée pour modifier les expressions qui représentent des conditionnelle `AND` operations.</xref:System.Linq.Expressions.ExpressionVisitor> Elle fait passer ces opérations d’un conditionnel `AND` à un conditionnel `OR`. Pour ce faire, la classe substitue la <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>méthode du type de base, étant donné que conditionnelle `AND` expressions sont représentées comme expressions binaires.</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> Dans le `VisitBinary` méthode, si l’expression passée représente un conditionnel `AND` opération, le code construit une nouvelle expression qui contient la condition `OR` opérateur conditionnel au lieu de `AND` opérateur. Si l’expression passée à `VisitBinary` ne représente pas un conditionnel `AND` opération, la méthode diffère à l’implémentation de classe de base. Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expression qui sont passés, mais les nœuds ont des sous-arbres est remplacés par les arborescences d’expression produites de manière récursive par le visiteur.  
  
4.  Ajouter un `Imports` instruction dans le fichier pour le `System.Linq.Expressions` espace de noms.  
  
5.  Ajoutez le code pour le `Main` méthode dans le fichier Module1.vb pour créer une arborescence d’expression et passez à la méthode qui sera le modifier.  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     Le code crée une expression qui contient un conditionnel `AND` opération. Il crée ensuite une instance de la `AndAlsoModifier` classe et passe l’expression à la `Modify` méthode de cette classe. L’original et les arborescences d’expression modifiée sont renvoyés pour afficher la modification.  
  
6.  Compilez et exécutez l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : exécuter des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
