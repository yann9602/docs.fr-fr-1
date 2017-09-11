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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2f0d383cbac639212519177fb1825875682f6233
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="f8dda-102">Comment : modifier des arborescences d’Expression (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8dda-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="f8dda-103">Cette rubrique montre comment modifier une arborescence d’expression.</span><span class="sxs-lookup"><span data-stu-id="f8dda-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="f8dda-104">Les arborescences d’expression sont immuables, ce qui signifie qu’ils ne peuvent pas être modifiés directement.</span><span class="sxs-lookup"><span data-stu-id="f8dda-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="f8dda-105">Pour modifier une arborescence d’expression, vous devez créer une copie d’une arborescence d’expression existante et lorsque vous créez la copie, apportez les modifications requises.</span><span class="sxs-lookup"><span data-stu-id="f8dda-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="f8dda-106">Vous pouvez utiliser la <xref:System.Linq.Expressions.ExpressionVisitor>classe pour parcourir une arborescence d’expression existante et copier chaque nœud visité.</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="f8dda-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="f8dda-107">Pour modifier une arborescence d’expression</span><span class="sxs-lookup"><span data-stu-id="f8dda-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="f8dda-108">Créer un nouveau **Application Console** projet.</span><span class="sxs-lookup"><span data-stu-id="f8dda-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="f8dda-109">Ajouter un `Imports` instruction dans le fichier pour le `System.Linq.Expressions` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f8dda-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="f8dda-110">Ajouter la `AndAlsoModifier` classe à votre projet.</span><span class="sxs-lookup"><span data-stu-id="f8dda-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="f8dda-111">Cette classe hérite de la <xref:System.Linq.Expressions.ExpressionVisitor>classe et est spécialisée pour modifier les expressions qui représentent des conditionnelle `AND` operations.</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="f8dda-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="f8dda-112">Elle fait passer ces opérations d’un conditionnel `AND` à un conditionnel `OR`.</span><span class="sxs-lookup"><span data-stu-id="f8dda-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="f8dda-113">Pour ce faire, la classe substitue la <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>méthode du type de base, étant donné que conditionnelle `AND` expressions sont représentées comme expressions binaires.</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A></span><span class="sxs-lookup"><span data-stu-id="f8dda-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="f8dda-114">Dans le `VisitBinary` méthode, si l’expression passée représente un conditionnel `AND` opération, le code construit une nouvelle expression qui contient la condition `OR` opérateur conditionnel au lieu de `AND` opérateur.</span><span class="sxs-lookup"><span data-stu-id="f8dda-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="f8dda-115">Si l’expression passée à `VisitBinary` ne représente pas un conditionnel `AND` opération, la méthode diffère à l’implémentation de classe de base.</span><span class="sxs-lookup"><span data-stu-id="f8dda-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="f8dda-116">Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expression qui sont passés, mais les nœuds ont des sous-arbres est remplacés par les arborescences d’expression produites de manière récursive par le visiteur.</span><span class="sxs-lookup"><span data-stu-id="f8dda-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="f8dda-117">Ajouter un `Imports` instruction dans le fichier pour le `System.Linq.Expressions` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f8dda-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="f8dda-118">Ajoutez le code pour le `Main` méthode dans le fichier Module1.vb pour créer une arborescence d’expression et passez à la méthode qui sera le modifier.</span><span class="sxs-lookup"><span data-stu-id="f8dda-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="f8dda-119">Le code crée une expression qui contient un conditionnel `AND` opération.</span><span class="sxs-lookup"><span data-stu-id="f8dda-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="f8dda-120">Il crée ensuite une instance de la `AndAlsoModifier` classe et passe l’expression à la `Modify` méthode de cette classe.</span><span class="sxs-lookup"><span data-stu-id="f8dda-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="f8dda-121">L’original et les arborescences d’expression modifiée sont renvoyés pour afficher la modification.</span><span class="sxs-lookup"><span data-stu-id="f8dda-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="f8dda-122">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="f8dda-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8dda-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8dda-123">See Also</span></span>  
 <span data-ttu-id="f8dda-124">[Comment : exécuter des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="f8dda-124">[How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
<span data-ttu-id="f8dda-125"> [Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span><span class="sxs-lookup"><span data-stu-id="f8dda-125"> [Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span></span>
