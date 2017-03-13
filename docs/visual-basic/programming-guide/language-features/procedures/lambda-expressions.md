---
title: "Lambda Expressions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.LambdaFunction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "functions [Visual Basic], lambda expressions"
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
  - "inline functions [Visual Basic]"
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 52
---
# Lambda Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une *expression lambda* est une fonction ou une sous\-routine sans nom qui peut être utilisée chaque fois qu'un délégué est valide.  Les expressions lambda peuvent être des fonctions ou des sous\-routines, et comporter une ou plusieurs lignes.  Vous pouvez passer des valeurs de la portée actuelle à une expression lambda.  
  
> [!NOTE]
>  L'instruction `RemoveHandler` est une exception.  Vous ne pouvez pas passer d'expression lambda pour le paramètre de délégué de `RemoveHandler`.  
  
 Vous créez des expressions lambda à l'aide du mot clé `Function` ou `Sub`, de la même manière qu'une fonction ou une sous\-routine standard.  Toutefois, les expressions lambda sont incluses dans une instruction.  
  
 L'exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur.  L'exemple montre la syntaxe d'expression lambda sur une ou plusieurs lignes d'une fonction.  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 L'exemple suivant présente une expression lambda qui écrit une valeur sur la console.  L'exemple montre la syntaxe d'expression lambda sur une ou plusieurs lignes d'une sous\-routine.  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Remarquez que dans les exemples précédents, les expressions lambda sont assignées à un nom de variable.  Chaque fois que vous faites référence à la variable, vous appelez l'expression lambda.  Vous pouvez également déclarer et appeler une expression lambda simultanément, comme illustré dans l'exemple suivant.  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Une expression lambda peut être retournée comme valeur d'un appel de fonction \(comme le montre l'exemple de la section [Contexte](#context) ultérieurement dans cette rubrique\) ou passée comme argument à un paramètre qui accepte un type délégué, comme dans l'exemple ci\-dessous.  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## Syntaxe d'expression lambda  
 La syntaxe d'une expression lambda est similaire à celle d'une fonction ou d'une sous\-routine standard.  Les différences sont les suivantes :  
  
-   Une expression lambda n'a pas de nom.  
  
-   Les expressions lambda ne peuvent pas avoir modificateurs, tels que `Overloads` ou `Overrides`.  
  
-   Les expressions lambda sur une ligne n'utilisent pas de clause `As` pour désigner le type de retour.  À la place, le type est déduit de la valeur que le corps de l'expression lambda prend.  Par exemple, si le corps de l'expression lambda est `cust.City = "London"`, son type de retour est `Boolean`.  
  
-   Dans les fonctions lambda sur plusieurs lignes, vous pouvez spécifier un type de retour à l'aide d'une clause `As` ou omettre la clause `As` afin que le type de retour soit déduit.  Lorsque la clause `As` est omise pour une fonction lambda sur plusieurs lignes, le type de retour est déduit pour être le type dominant de toutes les instructions `Return` de la fonction.  Le  *type dominant* est un type unique de tous les autres types peuvent s'étendre à.  Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types du tableau peuvent se limiter.  Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`.  Dans ce cas, si `Option Strict` a la valeur `On`, une erreur de compilateur se produit.  
  
     Par exemple, si les expressions fournies à la `Return` instruction contiennent des valeurs de type `Integer`, `Long`, et `Double`, le tableau résultant est de type `Double`.  `Integer` et `Long` s'étendent à `Double` et uniquement à `Double`.  Par conséquent, `Double` est le type dominant.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Le corps d'une fonction sur une ligne doit être une expression qui retourne une valeur, et non pas une instruction.  Il n'existe aucune instruction `Return` pour les fonctions sur une ligne.  La valeur retournée par la fonction sur une ligne est celle de l'expression du corps de la fonction.  
  
-   Le corps d'une sous\-routine sur une ligne doit être une instruction sur une ligne.  
  
-   Les fonctions et sous\-routines sur une ligne n'incluent pas d'instruction `End Function` ou `End Sub`.  
  
-   Vous pouvez spécifier le type de données d'un paramètre d'expression lambda à l'aide du mot clé `As`, ou le type de données du paramètre peut être déduit.  Tous les paramètres doivent posséder des types de données spécifiés ou être tous déduits.  
  
-   Les paramètres `Optional` et `Paramarray` ne sont pas autorisés.  
  
-   Les paramètres génériques ne sont pas autorisés.  
  
## Async lambda  
 Vous pouvez facilement créer des expressions lambda et les instructions qui incorporent le traitement asynchrone à l'aide de la [Async](../../../../visual-basic/language-reference/modifiers/async.md) et [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) mots clés.  Par exemple, l'exemple suivant de Windows Forms contient un gestionnaire d'événements qui appelle et attend une méthode asynchrone, `ExampleMethodAsync`.  
  
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
  
 Vous pouvez ajouter le Gestionnaire d'événements à l'aide d'une lambda async dans un [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).  Pour ajouter ce gestionnaire, ajoutez un `Async` modificateur avant la liste de paramètre lambda, comme le montre l'exemple suivant.  
  
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
  
 Pour plus d'informations sur comment créer et utiliser des méthodes asynchrones, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
##  <a name="context"></a> Contexte  
 Une expression lambda partage son contexte avec la portée dans laquelle elle est définie.  Elle possède les mêmes droits d'accès que tout code écrit dans la portée contenante.  Cela inclut l'accès aux éléments suivants : variables membres, fonctions, sous\-routines, `Me` , et paramètres et variables locales se trouvant dans la portée contenante.  
  
 L'accès aux variables locales et aux paramètres figurant dans la portée contenante peut s'étendre au\-delà de la durée de vie de cette portée.  Tant qu'un délégué qui fait référence à une expression lambda n'est pas disponible pour l'opération garbage collection, l'accès aux variables dans l'environnement d'origine est conservé.  Dans l'exemple suivant, la variable `target` est locale à `makeTheGame`, la méthode dans laquelle l'expression lambda `playTheGame` est définie.  Notez que l'expression lambda retournée, assignée à `takeAGuess` dans `Main`, a encore accès à la variable locale `target`.  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 L'exemple suivant montre la large gamme de droits d'accès de l'expression lambda imbriquée.  Lorsque l'expression lambda retournée est exécutée depuis `Main` sous la forme `aDel`, elle accède aux éléments suivants :  
  
-   Un champ de la classe dans laquelle elle est définie : `aField`  
  
-   Une propriété de la classe dans laquelle elle est définie : `aProp`  
  
-   Un paramètre de la méthode `functionWithNestedLambda`, dans laquelle elle est définie : `level1`  
  
-   Une variable locale de `functionWithNestedLambda` : `localVar`  
  
-   Un paramètre de l'expression lambda dans laquelle elle est imbriquée : `level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## Conversion en type délégué  
 Une expression lambda peut être convertie implicitement en type délégué compatible.  Pour plus d'informations sur les spécifications générales en matière de compatibilité, consultez [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  L'exemple de code suivant présente une expression lambda qui est implicitement convertie vers `Func(Of Integer, Boolean)` ou une signature de délégué correspondante.  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 L'exemple de code suivant présente une expression lambda qui est implicitement convertie vers `Sub(Of Double, String, Double)` ou une signature de délégué correspondante.  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Lorsque vous assignez des expressions lambda aux délégués ou les passez en tant qu'arguments aux procédures, vous pouvez spécifier les noms de paramètres, mais omettre leurs types de données, en permettant l'extraction des types du délégué.  
  
## Exemples  
  
-   L'exemple suivant définit une expression lambda qui retourne la valeur `True` si l'argument nullable a une valeur assignée, et `False` si sa valeur est `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   L'exemple suivant définit une expression lambda qui retourne l'index du dernier élément dans un tableau.  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [How to: Create a Lambda Expression](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-lambda-expression.md)   
 [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)