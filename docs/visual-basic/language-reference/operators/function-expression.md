---
title: Expression de fonction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="64520-102">Expression de fonction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64520-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="64520-103">Déclare les paramètres et le code qui définissent une expression lambda de fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64520-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64520-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="64520-105">Composants</span><span class="sxs-lookup"><span data-stu-id="64520-105">Parts</span></span>  
  
|<span data-ttu-id="64520-106">Terme</span><span class="sxs-lookup"><span data-stu-id="64520-106">Term</span></span>|<span data-ttu-id="64520-107">Définition</span><span class="sxs-lookup"><span data-stu-id="64520-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="64520-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="64520-108">Optional.</span></span> <span data-ttu-id="64520-109">Liste des noms de variables locales qui représentent les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="64520-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="64520-110">Les parenthèses doivent être présents même lorsque la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="64520-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="64520-111">Consultez [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="64520-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="64520-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="64520-112">Required.</span></span> <span data-ttu-id="64520-113">Une expression unique.</span><span class="sxs-lookup"><span data-stu-id="64520-113">A single expression.</span></span> <span data-ttu-id="64520-114">Le type de l’expression est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="64520-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="64520-115">Required.</span></span> <span data-ttu-id="64520-116">Une liste d’instructions qui retourne une valeur à l’aide de la `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="64520-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="64520-117">(Consultez [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).) Le type de la valeur retournée est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64520-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="64520-118">Remarks</span></span>  
 <span data-ttu-id="64520-119">A *expression lambda* est une fonction sans nom qui calcule et retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="64520-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="64520-120">Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument à `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="64520-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="64520-121">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec les délégués, consultez [instruction Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) et [Conversion souple en délégué](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="64520-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="64520-122">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="64520-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="64520-123">La syntaxe d’une expression lambda ressemble à celle d’une fonction standard.</span><span class="sxs-lookup"><span data-stu-id="64520-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="64520-124">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="64520-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="64520-125">Une expression lambda n’a pas un nom.</span><span class="sxs-lookup"><span data-stu-id="64520-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="64520-126">Expressions lambda ne peut pas avoir de modificateurs, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="64520-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="64520-127">Les expressions lambda n’utilisent pas une `As` clause pour désigner le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="64520-128">Au lieu de cela, le type est déduit à partir de la valeur que le corps d’une expression lambda sur une ligne a la valeur ou la valeur de retour d’une expression lambda multiligne.</span><span class="sxs-lookup"><span data-stu-id="64520-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="64520-129">Par exemple, si le corps d’une expression lambda sur une ligne est `Where cust.City = "London"`, son type de retour est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="64520-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="64520-130">Le corps d’une expression lambda sur une ligne doit être une expression, pas une instruction.</span><span class="sxs-lookup"><span data-stu-id="64520-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="64520-131">Le corps peut se composer d’un appel à une procédure function, mais pas d’un appel à une procédure sub.</span><span class="sxs-lookup"><span data-stu-id="64520-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="64520-132">Tous les paramètres doivent avoir indiqué les types de données ou de l’ensemble doit être déduit.</span><span class="sxs-lookup"><span data-stu-id="64520-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="64520-133">Paramètres facultatifs et Paramarray ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="64520-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="64520-134">Paramètres génériques ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="64520-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64520-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="64520-135">Example</span></span>  
 <span data-ttu-id="64520-136">Les exemples suivants montrent deux façons de créer des expressions lambda simples.</span><span class="sxs-lookup"><span data-stu-id="64520-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="64520-137">Le premier utilise un `Dim` pour fournir un nom pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="64520-138">Pour appeler la fonction, vous envoyez une valeur pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="64520-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="64520-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="64520-139">Example</span></span>  
 <span data-ttu-id="64520-140">Vous pouvez également déclarer et exécuter la fonction en même temps.</span><span class="sxs-lookup"><span data-stu-id="64520-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="64520-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="64520-141">Example</span></span>  
 <span data-ttu-id="64520-142">Voici un exemple d’une expression lambda qui incrémente son argument et retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="64520-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="64520-143">L’exemple montre les deux la syntaxe d’expression lambda multiligne ou de plusieurs lignes pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="64520-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="64520-144">Pour plus d’exemples, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="64520-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="64520-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="64520-145">Example</span></span>  
 <span data-ttu-id="64520-146">Expressions lambda sous-tendent à de nombreux opérateurs de requête de [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]et peuvent être utilisées explicitement dans les requêtes basées sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="64520-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="64520-147">L’exemple suivant montre une manière classique [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête, suivie de la traduction de la requête au format de la méthode.</span><span class="sxs-lookup"><span data-stu-id="64520-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="64520-148">Pour plus d’informations sur les méthodes de requête, consultez [requêtes](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="64520-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="64520-149">Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête Standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="64520-149">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64520-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64520-150">See Also</span></span>  
 [<span data-ttu-id="64520-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="64520-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="64520-152">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="64520-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="64520-153">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="64520-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="64520-154">Instructions</span><span class="sxs-lookup"><span data-stu-id="64520-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="64520-155">Comparaisons de valeurs</span><span class="sxs-lookup"><span data-stu-id="64520-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="64520-156">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="64520-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="64520-157">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="64520-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="64520-158">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="64520-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
