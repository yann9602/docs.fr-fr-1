---
title: Expressions lambda (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
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
ms.openlocfilehash: e4624e5f20beeebf85656c893043030566200557
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="c71ad-102">Expressions lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c71ad-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="c71ad-103">A *expression lambda* est une fonction ou une sous-routine sans nom qui peut être utilisé partout où un délégué est valide.</span><span class="sxs-lookup"><span data-stu-id="c71ad-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="c71ad-104">Les expressions lambda peuvent être des fonctions ou des sous-routines et peuvent être une ou plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="c71ad-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="c71ad-105">Vous pouvez passer des valeurs de l’étendue actuelle à une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="c71ad-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c71ad-106">La `RemoveHandler` instruction est une exception.</span><span class="sxs-lookup"><span data-stu-id="c71ad-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="c71ad-107">Vous ne pouvez pas passer une expression lambda pour le paramètre de délégué de `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="c71ad-108">Vous créez des expressions lambda à l’aide de la `Function` ou `Sub` (mot clé), tout comme une fonction standard ou une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="c71ad-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="c71ad-109">Toutefois, les expressions lambda sont incluses dans une instruction.</span><span class="sxs-lookup"><span data-stu-id="c71ad-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="c71ad-110">L’exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="c71ad-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="c71ad-111">L’exemple montre à la fois la syntaxe d’expression lambda sur plusieurs lignes ou de plusieurs lignes pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="c71ad-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 <span data-ttu-id="c71ad-112">[!code-vb[VbVbalrLambdas&#14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-112">[!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-113">L’exemple suivant est une expression lambda qui écrit une valeur dans la console.</span><span class="sxs-lookup"><span data-stu-id="c71ad-113">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="c71ad-114">L’exemple montre à la fois la syntaxe d’expression lambda sur plusieurs lignes ou de plusieurs lignes d’une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="c71ad-114">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 <span data-ttu-id="c71ad-115">[!code-vb[VbVbalrLambdas&#15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-115">[!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-116">Notez que, dans les exemples précédents, les expressions lambda sont affectées à un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="c71ad-116">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="c71ad-117">Chaque fois que vous faites référence à la variable, vous appelez l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="c71ad-117">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="c71ad-118">Vous pouvez également déclarer et appeler une expression lambda en même temps, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c71ad-118">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c71ad-119">[!code-vb[VbVbalrLambdas n °&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-119">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-120">Une expression lambda peut être retournée comme valeur d’un appel de fonction (comme illustré dans l’exemple de la [contexte](#context) plus loin dans cette rubrique), ou passé comme argument à un paramètre qui accepte un type délégué, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c71ad-120">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c71ad-121">[!code-vb[VbVbalrLambdas n °&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-121">[!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="c71ad-122">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="c71ad-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="c71ad-123">La syntaxe d’une expression lambda ressemble à celle d’une fonction standard ou une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="c71ad-123">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="c71ad-124">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c71ad-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="c71ad-125">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="c71ad-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="c71ad-126">Les expressions lambda ne peuvent pas avoir modificateurs, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="c71ad-127">Les fonctions lambda sur une ligne n’utilisent pas une `As` clause pour désigner le type de retour.</span><span class="sxs-lookup"><span data-stu-id="c71ad-127">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="c71ad-128">Au lieu de cela, le type est déduit à partir de la valeur que le corps de l’expression lambda prend la valeur.</span><span class="sxs-lookup"><span data-stu-id="c71ad-128">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="c71ad-129">Par exemple, si le corps de l’expression lambda est `cust.City = "London"`, son type de retour est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-129">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="c71ad-130">Dans les fonctions lambda sur plusieurs lignes, vous pouvez spécifier un type de retour à l’aide un `As` clause, ou omettre le `As` clause afin que le type de retour est déduit.</span><span class="sxs-lookup"><span data-stu-id="c71ad-130">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="c71ad-131">Lors de la `As` clause est omise pour une fonction lambda sur plusieurs lignes, le type de retour est déduit pour être le type dominant de toutes les `Return` instructions dans la fonction lambda sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="c71ad-131">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="c71ad-132">Le *type dominant* est un type unique auquel tous les autres types peuvent s’étendre.</span><span class="sxs-lookup"><span data-stu-id="c71ad-132">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="c71ad-133">Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types dans le tableau peuvent se limiter.</span><span class="sxs-lookup"><span data-stu-id="c71ad-133">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="c71ad-134">Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-134">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="c71ad-135">Dans ce cas, si `Option Strict` est défini sur `On`, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="c71ad-135">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="c71ad-136">Par exemple, si les expressions fournies dans le `Return` instruction contiennent des valeurs de type `Integer`, `Long`, et `Double`, le tableau résultant est de type `Double`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-136">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="c71ad-137">Les deux `Integer` et `Long` s’étendent à `Double` et uniquement `Double`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-137">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="c71ad-138">Par conséquent, `Double` est le type dominant.</span><span class="sxs-lookup"><span data-stu-id="c71ad-138">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="c71ad-139">Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c71ad-139">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="c71ad-140">Le corps d’une fonction d’une ligne doit être une expression qui retourne une valeur, pas une instruction.</span><span class="sxs-lookup"><span data-stu-id="c71ad-140">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="c71ad-141">Il existe aucune `Return` déclaration de fonctions sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="c71ad-141">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="c71ad-142">La valeur retournée par la fonction d’une ligne est la valeur de l’expression dans le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c71ad-142">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="c71ad-143">Le corps d’une sous-routine sur une ligne doit être l’instruction d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="c71ad-143">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="c71ad-144">Fonctions sur une ligne et des sous-routines n’incluent pas une `End Function` ou `End Sub` instruction.</span><span class="sxs-lookup"><span data-stu-id="c71ad-144">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="c71ad-145">Vous pouvez spécifier le type de données d’un paramètre d’expression lambda à l’aide de la `As` (mot clé), ou le type de données du paramètre peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="c71ad-145">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="c71ad-146">Tous les paramètres doivent avoir indiqué les types de données ou de l’ensemble doit être déduit.</span><span class="sxs-lookup"><span data-stu-id="c71ad-146">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="c71ad-147">`Optional`et `Paramarray` les paramètres ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="c71ad-147">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="c71ad-148">Paramètres génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="c71ad-148">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="c71ad-149">Lambdas asynchrones</span><span class="sxs-lookup"><span data-stu-id="c71ad-149">Async Lambdas</span></span>  
 <span data-ttu-id="c71ad-150">Vous pouvez facilement créer des expressions lambda et des instructions qui incorporent le traitement asynchrone à l’aide de la [Async](../../../../visual-basic/language-reference/modifiers/async.md) et [opérateur Await](../../../../visual-basic/language-reference/operators/await-operator.md) mots clés.</span><span class="sxs-lookup"><span data-stu-id="c71ad-150">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="c71ad-151">Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-151">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="c71ad-152">Vous pouvez ajouter le même gestionnaire d’événements à l’aide d’une expression lambda asynchrone dans un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c71ad-152">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="c71ad-153">Pour ajouter ce gestionnaire, ajoutez un modificateur `Async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c71ad-153">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="c71ad-154">Pour plus d’informations sur la création et l’utilisation des méthodes asynchrones, consultez [programmation asynchrone avec Async et Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="c71ad-154">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <span data-ttu-id="c71ad-155"><a name="context"></a>Contexte</span><span class="sxs-lookup"><span data-stu-id="c71ad-155"><a name="context"></a> Context</span></span>  
 <span data-ttu-id="c71ad-156">Une expression lambda partage son contexte avec la portée dans laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="c71ad-156">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="c71ad-157">Il possède les droits d’accès que tout code écrit dans la portée contenante.</span><span class="sxs-lookup"><span data-stu-id="c71ad-157">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="c71ad-158">Cela inclut l’accès aux variables membres, des fonctions et des sous-routines, `Me`, des paramètres et variables locales dans la portée contenante.</span><span class="sxs-lookup"><span data-stu-id="c71ad-158">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="c71ad-159">Accès aux variables locales et les paramètres dans la portée contenante peut s’étendre au-delà de la durée de vie de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="c71ad-159">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="c71ad-160">Si un délégué se référant à une expression lambda n’est pas disponible pour le garbage collection, l’accès aux variables dans l’environnement d’origine est conservé.</span><span class="sxs-lookup"><span data-stu-id="c71ad-160">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="c71ad-161">Dans l’exemple suivant, la variable `target` local `makeTheGame`, la méthode dans laquelle l’expression lambda `playTheGame` est défini.</span><span class="sxs-lookup"><span data-stu-id="c71ad-161">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="c71ad-162">Notez que l’expression lambda retournée, assignée à `takeAGuess` dans `Main`, a toujours accès à la variable locale `target`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-162">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 <span data-ttu-id="c71ad-163">[!code-vb[VbVbalrLambdas&#12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-163">[!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-164">L’exemple suivant illustre un large éventail de droits d’accès de l’expression lambda imbriquée.</span><span class="sxs-lookup"><span data-stu-id="c71ad-164">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="c71ad-165">Lorsque l’expression lambda retournée est exécutée à partir de `Main` comme `aDel`, il accède aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c71ad-165">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="c71ad-166">Un champ de la classe dans laquelle elle est définie :`aField`</span><span class="sxs-lookup"><span data-stu-id="c71ad-166">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="c71ad-167">Une propriété de la classe dans laquelle elle est définie :`aProp`</span><span class="sxs-lookup"><span data-stu-id="c71ad-167">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="c71ad-168">Un paramètre de méthode `functionWithNestedLambda`, dans lequel elle est définie :`level1`</span><span class="sxs-lookup"><span data-stu-id="c71ad-168">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="c71ad-169">Une variable locale de `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="c71ad-169">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="c71ad-170">Un paramètre de l’expression lambda dans laquelle elle est imbriquée :`level2`</span><span class="sxs-lookup"><span data-stu-id="c71ad-170">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 <span data-ttu-id="c71ad-171">[!code-vb[VbVbalrLambdas&#9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-171">[!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span></span>  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="c71ad-172">Conversion d’un type délégué</span><span class="sxs-lookup"><span data-stu-id="c71ad-172">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="c71ad-173">Une expression lambda peut être convertie implicitement en un type délégué compatible.</span><span class="sxs-lookup"><span data-stu-id="c71ad-173">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="c71ad-174">Pour plus d’informations sur la configuration générale requise pour la compatibilité, voir [la Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="c71ad-174">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="c71ad-175">Par exemple, l’exemple de code suivant montre une expression lambda qui est implicitement convertie vers `Func(Of Integer, Boolean)` ou une signature de délégué correspondante.</span><span class="sxs-lookup"><span data-stu-id="c71ad-175">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="c71ad-176">[!code-vb[VbVbalrLambdas&#16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-176">[!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-177">L’exemple de code suivant montre une expression lambda qui est implicitement convertie vers `Sub(Of Double, String, Double)` ou une signature de délégué correspondante.</span><span class="sxs-lookup"><span data-stu-id="c71ad-177">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="c71ad-178">[!code-vb[VbVbalrLambdas n °&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-178">[!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span></span>  
  
 <span data-ttu-id="c71ad-179">Lorsque vous assignez des expressions lambda aux délégués ou les passer comme arguments à des procédures, vous pouvez spécifier les noms de paramètres, mais omettre leurs types de données, en laissant les types entreprendre à partir du délégué.</span><span class="sxs-lookup"><span data-stu-id="c71ad-179">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c71ad-180">Exemples</span><span class="sxs-lookup"><span data-stu-id="c71ad-180">Examples</span></span>  
  
-   <span data-ttu-id="c71ad-181">L’exemple suivant définit une expression lambda qui retourne `True` si l’argument nullable a une valeur assignée, et `False` si sa valeur est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c71ad-181">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     <span data-ttu-id="c71ad-182">[!code-vb[VbVbalrLambdas n °&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-182">[!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span></span>  
  
-   <span data-ttu-id="c71ad-183">L’exemple suivant définit une expression lambda qui retourne l’index du dernier élément dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="c71ad-183">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     <span data-ttu-id="c71ad-184">[!code-vb[VbVbalrLambdas n °&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="c71ad-184">[!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71ad-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c71ad-185">See Also</span></span>  
 <span data-ttu-id="c71ad-186">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-186">[Procedures](./index.md) </span></span>  
<span data-ttu-id="c71ad-187"> [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-187"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="c71ad-188"> [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-188"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="c71ad-189"> [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-189"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="c71ad-190"> [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-190"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="c71ad-191"> [Types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-191"> [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="c71ad-192"> [Comment : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-192"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="c71ad-193"> [Comment : créer une Expression Lambda](./how-to-create-a-lambda-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c71ad-193"> [How to: Create a Lambda Expression](./how-to-create-a-lambda-expression.md) </span></span>  
<span data-ttu-id="c71ad-194"> [Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="c71ad-194"> [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

