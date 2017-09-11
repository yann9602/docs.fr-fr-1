---
title: "Guide pratique pour modifier des arborescences d’expressions (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b665f3bfa1228e2e8834241f010792e9d5975c96
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="d3479-102">Guide pratique pour modifier des arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="d3479-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="d3479-103">Cette rubrique montre comment modifier une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="d3479-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="d3479-104">Les arborescences d’expressions sont immuables, ce qui signifie qu’elles ne peuvent pas être modifiées directement.</span><span class="sxs-lookup"><span data-stu-id="d3479-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="d3479-105">Pour changer une arborescence d’expressions, vous devez créer une copie d’une arborescence d’expressions existante et, quand vous créez la copie, apporter les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d3479-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="d3479-106">Vous pouvez utiliser la classe <xref:System.Linq.Expressions.ExpressionVisitor> pour parcourir une arborescence d’expressions existante et copier chaque nœud visité.</span><span class="sxs-lookup"><span data-stu-id="d3479-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="d3479-107">Pour modifier une arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="d3479-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="d3479-108">Créez un projet d’**Application console**.</span><span class="sxs-lookup"><span data-stu-id="d3479-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="d3479-109">Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="d3479-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="d3479-110">Ajoutez la classe `AndAlsoModifier` à votre projet.</span><span class="sxs-lookup"><span data-stu-id="d3479-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     <span data-ttu-id="d3479-111">Cette classe hérite de la classe `AND` et est spécialisée pour modifier les expressions qui représentent des opérations <xref:System.Linq.Expressions.ExpressionVisitor> conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="d3479-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="d3479-112">Elle convertit ces opérations d’un `AND` conditionnel en un `OR` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="d3479-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="d3479-113">Pour ce faire, la classe substitue la méthode <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> du type de base, car les expressions `AND` conditionnelles sont représentées sous forme d’expressions binaires.</span><span class="sxs-lookup"><span data-stu-id="d3479-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="d3479-114">Dans la méthode `VisitBinary`, si l’expression passée représente une opération `AND` conditionnelle, le code construit une nouvelle expression qui contient l’opérateur `OR` conditionnel au lieu de l’opérateur `AND` conditionnel.</span><span class="sxs-lookup"><span data-stu-id="d3479-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="d3479-115">Si l’expression passée à `VisitBinary` ne représente pas une opération `AND` conditionnelle, la méthode emploie l’implémentation de classe de base.</span><span class="sxs-lookup"><span data-stu-id="d3479-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="d3479-116">Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expressions passées, mais les nœuds voient leurs sous-arborescences remplacées par les arborescences d’expressions produites de manière récursive par le visiteur.</span><span class="sxs-lookup"><span data-stu-id="d3479-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="d3479-117">Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="d3479-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="d3479-118">Ajoutez le code à la méthode `Main` dans le fichier Program.cs pour créer une arborescence d’expressions, et passez-le à la méthode qui le modifiera.</span><span class="sxs-lookup"><span data-stu-id="d3479-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     <span data-ttu-id="d3479-119">Le code crée une expression qui contient une opération `AND` conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="d3479-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="d3479-120">Il crée ensuite une instance de la classe `AndAlsoModifier` et passe l’expression à la méthode `Modify` de cette classe.</span><span class="sxs-lookup"><span data-stu-id="d3479-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="d3479-121">Les arborescences d’expressions d’origine et modifiée sont toutes deux générées pour montrer la modification.</span><span class="sxs-lookup"><span data-stu-id="d3479-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="d3479-122">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d3479-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3479-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3479-123">See Also</span></span>  
 <span data-ttu-id="d3479-124">[Guide pratique pour exécuter des arborescences d’expressions (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="d3479-124">[How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
 [<span data-ttu-id="d3479-125">Arborescences d’expressions (C#)</span><span class="sxs-lookup"><span data-stu-id="d3479-125">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)

