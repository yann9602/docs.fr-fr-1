---
title: Fonction Expression (Visual Basic) | Documents Microsoft
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
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: c379ed1694f72243ccb8367d5b820803b4fcf190
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="67931-102">Expression de fonction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67931-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="67931-103">Déclare les paramètres et le code qui définissent une expression lambda de fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67931-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67931-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="67931-105">Composants</span><span class="sxs-lookup"><span data-stu-id="67931-105">Parts</span></span>  
  
|<span data-ttu-id="67931-106">Terme</span><span class="sxs-lookup"><span data-stu-id="67931-106">Term</span></span>|<span data-ttu-id="67931-107">Définition</span><span class="sxs-lookup"><span data-stu-id="67931-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="67931-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="67931-108">Optional.</span></span> <span data-ttu-id="67931-109">Liste des noms de variables locales qui représentent les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="67931-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="67931-110">Les parenthèses doivent être présentes même quand la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="67931-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="67931-111">Consultez la page [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="67931-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="67931-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="67931-112">Required.</span></span> <span data-ttu-id="67931-113">Une expression unique.</span><span class="sxs-lookup"><span data-stu-id="67931-113">A single expression.</span></span> <span data-ttu-id="67931-114">Le type de l’expression est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="67931-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="67931-115">Required.</span></span> <span data-ttu-id="67931-116">Une liste d’instructions qui retourne une valeur à l’aide de la `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="67931-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="67931-117">(Voir [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).) Le type de la valeur retournée est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67931-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="67931-118">Remarks</span></span>  
 <span data-ttu-id="67931-119">A *expression lambda* est une fonction sans nom qui calcule et retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="67931-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="67931-120">Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument à `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="67931-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="67931-121">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec les délégués, consultez [instruction Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) et [la Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="67931-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="67931-122">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="67931-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="67931-123">La syntaxe d’une expression lambda ressemble à celle d’une fonction standard.</span><span class="sxs-lookup"><span data-stu-id="67931-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="67931-124">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="67931-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="67931-125">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="67931-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="67931-126">Les expressions lambda ne peuvent pas avoir modificateurs, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="67931-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="67931-127">Les expressions lambda n’utilisent pas une `As` clause pour désigner le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="67931-128">Au lieu de cela, le type est déduit à partir de la valeur que le corps d’une expression lambda sur une ligne prend la valeur ou la valeur de retour d’une expression lambda multiligne.</span><span class="sxs-lookup"><span data-stu-id="67931-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="67931-129">Par exemple, si le corps d’une expression lambda sur une ligne est `Where cust.City = "London"`, son type de retour est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="67931-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="67931-130">Le corps d’une expression lambda sur une ligne doit être une expression, pas une instruction.</span><span class="sxs-lookup"><span data-stu-id="67931-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="67931-131">Le corps peut se composer d’un appel à une procédure de fonction, mais pas d’un appel à une procédure sub.</span><span class="sxs-lookup"><span data-stu-id="67931-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="67931-132">Tous les paramètres doivent avoir indiqué les types de données ou de l’ensemble doit être déduit.</span><span class="sxs-lookup"><span data-stu-id="67931-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="67931-133">Paramètres facultatifs et Paramarray ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="67931-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="67931-134">Paramètres génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="67931-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67931-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="67931-135">Example</span></span>  
 <span data-ttu-id="67931-136">Les exemples suivants montrent deux façons de créer des expressions lambda simples.</span><span class="sxs-lookup"><span data-stu-id="67931-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="67931-137">Le premier utilise un `Dim` pour fournir un nom pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="67931-138">Pour appeler la fonction, vous envoyez une valeur pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="67931-138">To call the function, you send in a value for the parameter.</span></span>  
  
 <span data-ttu-id="67931-139">[!code-vb[VbVbalrLambdas n °&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="67931-139">[!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span></span>  
  
 <span data-ttu-id="67931-140">[!code-vb[VbVbalrLambdas n °&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="67931-140">[!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="67931-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="67931-141">Example</span></span>  
 <span data-ttu-id="67931-142">Vous pouvez également déclarer et exécuter la fonction en même temps.</span><span class="sxs-lookup"><span data-stu-id="67931-142">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 <span data-ttu-id="67931-143">[!code-vb[VbVbalrLambdas n °&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="67931-143">[!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="67931-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="67931-144">Example</span></span>  
 <span data-ttu-id="67931-145">Voici un exemple d’une expression lambda qui incrémente son argument et retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="67931-145">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="67931-146">L’exemple montre à la fois la syntaxe d’expression lambda multiligne ou plusieurs lignes pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="67931-146">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="67931-147">Pour plus d’exemples, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="67931-147">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="67931-148">[!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="67931-148">[!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="67931-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="67931-149">Example</span></span>  
 <span data-ttu-id="67931-150">Expressions lambda offrent de nombreux opérateurs de requête de [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]et peuvent être utilisées explicitement dans les requêtes basées sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="67931-150">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="67931-151">L’exemple suivant montre un type [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] requête, suivie de la traduction de la requête au format de la méthode.</span><span class="sxs-lookup"><span data-stu-id="67931-151">The following example shows a typical [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="67931-152">Pour plus d’informations sur les méthodes de requête, consultez [requêtes](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="67931-152">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="67931-153">Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête Standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="67931-153">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67931-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67931-154">See Also</span></span>  
 <span data-ttu-id="67931-155">[Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="67931-155">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="67931-156"> [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="67931-156"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="67931-157"> [Opérateurs et Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="67931-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="67931-158"> [Instructions](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="67931-158"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="67931-159"> [Comparaisons de valeurs](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="67931-159"> [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="67931-160"> [Expressions booléennes](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="67931-160"> [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="67931-161"> [Si (opérateur)](../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="67931-161"> [If Operator](../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="67931-162"> [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="67931-162"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

