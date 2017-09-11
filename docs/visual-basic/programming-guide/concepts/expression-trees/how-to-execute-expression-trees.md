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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4cc2c9890c1f5efbc4036d94eef1adb05094ae40
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="0df31-102">Comment : exécuter des arborescences d’Expression (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0df31-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="0df31-103">Cette rubrique montre comment exécuter une arborescence d’expression.</span><span class="sxs-lookup"><span data-stu-id="0df31-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="0df31-104">L’exécution d’une arborescence d’expression peut retourner une valeur, ou il peut simplement effectuer une action telle que l’appel d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="0df31-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="0df31-105">Seules les arborescences d’expression qui représentent des expressions lambda peuvent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="0df31-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="0df31-106">Arborescences d’expression qui représentent des expressions lambda sont de type <xref:System.Linq.Expressions.LambdaExpression>ou <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="0df31-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="0df31-107">Pour exécuter ces arborescences d’expression, appelez le <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>méthode pour créer un délégué exécutable, puis appelez le délégué.</xref:System.Linq.Expressions.LambdaExpression.Compile%2A></span><span class="sxs-lookup"><span data-stu-id="0df31-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0df31-108">Si le type du délégué n’est pas connu, autrement dit, l’expression lambda est de type <xref:System.Linq.Expressions.LambdaExpression>et non <xref:System.Linq.Expressions.Expression%601>, vous devez appeler la <xref:System.Delegate.DynamicInvoke%2A>méthode sur le délégué au lieu d’appeler directement.</xref:System.Delegate.DynamicInvoke%2A> </xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="0df31-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="0df31-109">Si une arborescence d’expression ne représente pas une expression lambda, vous pouvez créer une expression lambda qui possède l’arborescence d’expression d’origine comme étant son corps, en appelant le <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>méthode.</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29></span><span class="sxs-lookup"><span data-stu-id="0df31-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="0df31-110">Ensuite, vous pouvez exécuter l’expression lambda comme décrit précédemment dans cette section.</span><span class="sxs-lookup"><span data-stu-id="0df31-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0df31-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0df31-111">Example</span></span>  
 <span data-ttu-id="0df31-112">L’exemple de code suivant montre comment exécuter une arborescence d’expression qui représente l’élévation d’un nombre à une puissance en créant une expression lambda et en l’exécutant.</span><span class="sxs-lookup"><span data-stu-id="0df31-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="0df31-113">Le résultat, qui représente le nombre élevé à la puissance, est affiché.</span><span class="sxs-lookup"><span data-stu-id="0df31-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0df31-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="0df31-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0df31-115">Ajoutez une référence de projet à System.Core.dll si elle n’est pas déjà référencée.</span><span class="sxs-lookup"><span data-stu-id="0df31-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="0df31-116">Inclure l’espace de noms System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="0df31-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df31-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0df31-117">See Also</span></span>  
 <span data-ttu-id="0df31-118">[Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="0df31-118">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="0df31-119"> [Comment : modifier des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="0df31-119"> [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span></span>
