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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e50593e76afecfe8807c3cb5bac479245d2feaef
ms.lasthandoff: 03/13/2017

---
# <a name="lambda-expressions-visual-basic"></a>Expressions lambda (Visual Basic)
A *expression lambda* est une fonction ou une sous-routine sans nom qui peut être utilisé partout où un délégué est valide. Les expressions lambda peuvent être des fonctions ou des sous-routines et peuvent être une ou plusieurs lignes. Vous pouvez passer des valeurs de l’étendue actuelle à une expression lambda.  
  
> [!NOTE]
>  La `RemoveHandler` instruction est une exception. Vous ne pouvez pas passer une expression lambda pour le paramètre de délégué de `RemoveHandler`.  
  
 Vous créez des expressions lambda à l’aide de la `Function` ou `Sub` (mot clé), tout comme une fonction standard ou une sous-routine. Toutefois, les expressions lambda sont incluses dans une instruction.  
  
 L’exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur. L’exemple montre à la fois la syntaxe d’expression lambda sur plusieurs lignes ou de plusieurs lignes pour une fonction.  
  
 [!code-vb[VbVbalrLambdas&#14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 L’exemple suivant est une expression lambda qui écrit une valeur dans la console. L’exemple montre à la fois la syntaxe d’expression lambda sur plusieurs lignes ou de plusieurs lignes d’une sous-routine.  
  
 [!code-vb[VbVbalrLambdas&#15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Notez que, dans les exemples précédents, les expressions lambda sont affectées à un nom de variable. Chaque fois que vous faites référence à la variable, vous appelez l’expression lambda. Vous pouvez également déclarer et appeler une expression lambda en même temps, comme indiqué dans l’exemple suivant.  
  
 [!code-vb[VbVbalrLambdas n °&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Une expression lambda peut être retournée comme valeur d’un appel de fonction (comme illustré dans l’exemple de la [contexte](#context) plus loin dans cette rubrique), ou passé comme argument à un paramètre qui accepte un type délégué, comme indiqué dans l’exemple suivant.  
  
 [!code-vb[VbVbalrLambdas n °&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda  
 La syntaxe d’une expression lambda ressemble à celle d’une fonction standard ou une sous-routine. Les différences sont les suivantes :  
  
-   Une expression lambda n’a pas de nom.  
  
-   Les expressions lambda ne peuvent pas avoir modificateurs, tels que `Overloads` ou `Overrides`.  
  
-   Les fonctions lambda sur une ligne n’utilisent pas une `As` clause pour désigner le type de retour. Au lieu de cela, le type est déduit à partir de la valeur que le corps de l’expression lambda prend la valeur. Par exemple, si le corps de l’expression lambda est `cust.City = "London"`, son type de retour est `Boolean`.  
  
-   Dans les fonctions lambda sur plusieurs lignes, vous pouvez spécifier un type de retour à l’aide un `As` clause, ou omettre le `As` clause afin que le type de retour est déduit. Lors de la `As` clause est omise pour une fonction lambda sur plusieurs lignes, le type de retour est déduit pour être le type dominant de toutes les `Return` instructions dans la fonction lambda sur plusieurs lignes. Le *type dominant* est un type unique auquel tous les autres types peuvent s’étendre. Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types dans le tableau peuvent se limiter. Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`. Dans ce cas, si `Option Strict` est défini sur `On`, une erreur de compilation se produit.  
  
     Par exemple, si les expressions fournies dans le `Return` instruction contiennent des valeurs de type `Integer`, `Long`, et `Double`, le tableau résultant est de type `Double`. Les deux `Integer` et `Long` s’étendent à `Double` et uniquement `Double`. Par conséquent, `Double` est le type dominant. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Le corps d’une fonction d’une ligne doit être une expression qui retourne une valeur, pas une instruction. Il existe aucune `Return` déclaration de fonctions sur une ligne. La valeur retournée par la fonction d’une ligne est la valeur de l’expression dans le corps de la fonction.  
  
-   Le corps d’une sous-routine sur une ligne doit être l’instruction d’une ligne.  
  
-   Fonctions sur une ligne et des sous-routines n’incluent pas une `End Function` ou `End Sub` instruction.  
  
-   Vous pouvez spécifier le type de données d’un paramètre d’expression lambda à l’aide de la `As` (mot clé), ou le type de données du paramètre peut être déduit. Tous les paramètres doivent avoir indiqué les types de données ou de l’ensemble doit être déduit.  
  
-   `Optional`et `Paramarray` les paramètres ne sont pas autorisés.  
  
-   Paramètres génériques ne sont pas autorisés.  
  
## <a name="async-lambdas"></a>Lambdas asynchrones  
 Vous pouvez facilement créer des expressions lambda et des instructions qui incorporent le traitement asynchrone à l’aide de la [Async](../../../../visual-basic/language-reference/modifiers/async.md) et [opérateur Await](../../../../visual-basic/language-reference/operators/await-operator.md) mots clés. Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.  
  
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
  
 Vous pouvez ajouter le même gestionnaire d’événements à l’aide d’une expression lambda asynchrone dans un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Pour ajouter ce gestionnaire, ajoutez un modificateur `Async` avant la liste des paramètres lambda, comme le montre l'exemple suivant.  
  
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
  
 Pour plus d’informations sur la création et l’utilisation des méthodes asynchrones, consultez [programmation asynchrone avec Async et Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
##  <a name="context"></a>Contexte  
 Une expression lambda partage son contexte avec la portée dans laquelle elle est définie. Il possède les droits d’accès que tout code écrit dans la portée contenante. Cela inclut l’accès aux variables membres, des fonctions et des sous-routines, `Me`, des paramètres et variables locales dans la portée contenante.  
  
 Accès aux variables locales et les paramètres dans la portée contenante peut s’étendre au-delà de la durée de vie de cette étendue. Si un délégué se référant à une expression lambda n’est pas disponible pour le garbage collection, l’accès aux variables dans l’environnement d’origine est conservé. Dans l’exemple suivant, la variable `target` local `makeTheGame`, la méthode dans laquelle l’expression lambda `playTheGame` est défini. Notez que l’expression lambda retournée, assignée à `takeAGuess` dans `Main`, a toujours accès à la variable locale `target`.  
  
 [!code-vb[VbVbalrLambdas&#12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 L’exemple suivant illustre un large éventail de droits d’accès de l’expression lambda imbriquée. Lorsque l’expression lambda retournée est exécutée à partir de `Main` comme `aDel`, il accède aux éléments suivants :  
  
-   Un champ de la classe dans laquelle elle est définie :`aField`  
  
-   Une propriété de la classe dans laquelle elle est définie :`aProp`  
  
-   Un paramètre de méthode `functionWithNestedLambda`, dans lequel elle est définie :`level1`  
  
-   Une variable locale de `functionWithNestedLambda`:`localVar`  
  
-   Un paramètre de l’expression lambda dans laquelle elle est imbriquée :`level2`  
  
 [!code-vb[VbVbalrLambdas&#9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>Conversion d’un type délégué  
 Une expression lambda peut être convertie implicitement en un type délégué compatible. Pour plus d’informations sur la configuration générale requise pour la compatibilité, voir [la Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Par exemple, l’exemple de code suivant montre une expression lambda qui est implicitement convertie vers `Func(Of Integer, Boolean)` ou une signature de délégué correspondante.  
  
 [!code-vb[VbVbalrLambdas&#16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 L’exemple de code suivant montre une expression lambda qui est implicitement convertie vers `Sub(Of Double, String, Double)` ou une signature de délégué correspondante.  
  
 [!code-vb[VbVbalrLambdas n °&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Lorsque vous assignez des expressions lambda aux délégués ou les passer comme arguments à des procédures, vous pouvez spécifier les noms de paramètres, mais omettre leurs types de données, en laissant les types entreprendre à partir du délégué.  
  
## <a name="examples"></a>Exemples  
  
-   L’exemple suivant définit une expression lambda qui retourne `True` si l’argument nullable a une valeur assignée, et `False` si sa valeur est `Nothing`.  
  
     [!code-vb[VbVbalrLambdas n °&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   L’exemple suivant définit une expression lambda qui retourne l’index du dernier élément dans un tableau.  
  
     [!code-vb[VbVbalrLambdas n °&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Comment : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Comment : créer une Expression Lambda](./how-to-create-a-lambda-expression.md)   
 [Conversion simplifiée des délégués](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
