---
title: Async (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: fa15daee8f3b6ddcc137356896a20cf82e0cc1d0
ms.lasthandoff: 03/13/2017

---
# <a name="async-visual-basic"></a>Async (Visual Basic)
Le `Async` modificateur indique que la méthode ou [expression lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) qu’elle modifie est asynchrone. Ces méthodes sont appelées *les méthodes async*.  
  
 Une méthode async offre un moyen pratique d'exécuter un travail potentiellement long sans bloquer le thread de l'appelant. L’appelant d’une méthode async peut reprendre son travail sans attendre que la méthode asynchrone se termine.  
  
> [!NOTE]
>  Les mots clés `Async` et `Await` ont été introduites dans Visual Studio 2012. Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 L’exemple suivant montre la structure d’une méthode asynchrone. Par convention, les noms de méthode asynchrone se terminent par « Async ».  
  
```vb  
  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 En règle générale, une méthode est modifié par la `Async` (mot clé) contient au moins un [Await](../../../visual-basic/language-reference/modifiers/async.md) expression ou une instruction. La méthode s’exécute de façon synchrone jusqu'à ce qu’il atteigne le premier `Await`, moment auquel il s’interrompt jusqu'à ce que la tâche attendue se termine. Entre-temps, le contrôle est renvoyé à l’appelant de la méthode. Si la méthode ne contient pas une `Await` expression ou une instruction, la méthode n’est pas interrompue et qu’il s’exécute comme une méthode synchrone. Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas `Await` , car cette situation peut indiquer une erreur. Pour plus d’informations, consultez la [erreur du compilateur](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 Le `Async` mot clé est un mot clé non réservé. Il est un mot clé lorsqu’il modifie une méthode ou une expression lambda. Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## <a name="return-types"></a>Types de retours  
 Une méthode asynchrone est un [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procédure, ou un [fonction](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procédure qui a un type de retour de <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> La méthode ne peut pas déclarer de [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) paramètres.  
  
 Vous spécifiez `Task(Of TResult)` pour le type de retour d’une méthode async si le [retourner](../../../visual-basic/language-reference/statements/return-statement.md) instruction de la méthode a un opérande de type TResult. Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée. Autrement dit, un appel à la méthode retourne un `Task`, mais lorsque le `Task` terminée, n’importe quel `Await` instruction qui est en attente le `Task` ne produit pas une valeur de résultat.  
  
 Async sous-routines sont principalement utilisés pour définir des gestionnaires d’événements dans lequel un `Sub` procédure n’est requise. L’appelant d’une sous-routine async ne peut pas attendre et ne peut pas intercepter des exceptions levées par la méthode.  
  
 Pour plus d’informations et d’exemples, consultez [les Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent un gestionnaire d’événements asynchrones, une expression lambda d’async et une méthode async. Pour obtenir un exemple complet qui utilise ces éléments, consultez [procédure pas à pas : accès Web à l’aide de Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger le code de procédure pas à pas de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
```vb  
  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute></xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Procédure pas à pas : accès au web avec Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
