---
title: "Async (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Async"
helpviewer_keywords: 
  - "Async [Visual Basic]"
  - "Async keyword [Visual Basic]"
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Async (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le modificateur `Async`, spécifie qu'une méthode, une [expression lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md), ou une méthode anonyme est asynchrone.  Ces méthodes sont nommées *méthodes asynchrones.*  
  
 Une méthode async offre un moyen pratique d'exécuter un travail potentiellement long sans bloquer le thread de l'appelant.  L'appelant d'une méthode async peut reprendre son travail sans attendre la fin de la méthode async.  
  
> [!NOTE]
>  Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012.  Pour une présentation de la programmation asynchrone, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'exemple suivant illustre la structure d'une méthode asynchrone.  Par convention, le nom d'une méthode asynchrone se termine par le suffixe "Async".  
  
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
  
 En général, une méthode que le mot clé `Async` modifie contient au moins une instruction ou une expression [await](../../../visual-basic/language-reference/modifiers/async.md).  La méthode fonctionne de façon synchrone jusqu'à ce qu'elle atteigne le premier `Await`, après quoi elle s'interrompt jusqu'à ce que la tâche attendue se termine.  Entre\-temps, l'appelant récupère le contrôle de la méthode async.  Si la méthode ne contient pas une expression ou une instruction `Await`, la méthode n'est pas interrompue et s'exécute comme une méthode synchrone.  Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas `Await`, car cette situation peut indiquer une erreur.  Pour plus d'informations, consultez le [erreur de compilation](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 Le mot clé `Async` est un mot clé non réservé.  C'est un mot clé lorsqu'il modifie une méthode ou une expression lambda.  Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## Types de retours  
 Une méthode async est soit une procédure [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md), ou une procédure [Fonction](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) qui possède un type de retour de <xref:System.Threading.Tasks.Task> ou de <xref:System.Threading.Tasks.Task%601>.  La méthode ne peut pas déclarer de paramètres [ByRef](../../../visual-basic/language-reference/modifiers/byref.md).  
  
 Vous spécifiez `Task(Of TResult)` comme type de retour d'une méthode async si l'instruction [return](../../../visual-basic/language-reference/statements/return-statement.md) de la méthode possède un opérande de type TResult.  Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.  Autrement dit, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, aucune instruction `Await` qui attend un `Task` ne produit une valeur de résultat.  
  
 Les sous\-routines Async sont principalement utilisées pour définir des gestionnaires d'événements où une procédure `Sub` est requise.  L'appelant d'une sous\-routine async ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.  
  
 Pour plus d'informations et d'exemples, consultez [Types de retour Async](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemple  
 Les exemples suivants montrent un gestionnaire d'événements async, une expression lambda async, et une méthode async.  Pour obtenir un exemple complet qui utilise ces éléments semblables, consultez [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Vous pouvez télécharger le code de procédure depuis [Exemples de code du développeur](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
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
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)