---
title: "Await, opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
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
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a>Await, opérateur (Visual Basic)
Vous appliquez le `Await` opérateur à un opérande dans une expression lambda ou de méthode asynchrone pour suspendre l’exécution de la méthode jusqu'à ce que la tâche attendue se termine. La tâche représente un travail en cours.  
  
 La méthode dans laquelle `Await` utilisé doit avoir un [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur. Une telle méthode, définie à l’aide de la `Async` modificateur et généralement contenant un ou plusieurs `Await` expressions, est appelé un *méthode async*.  
  
> [!NOTE]
>  Les mots clés `Async` et `Await` ont été introduites dans Visual Studio 2012. Pour une introduction à la programmation asynchrone, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 En règle générale, la tâche à laquelle vous appliquez le `Await` opérateur est la valeur de retour d’un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](http://go.microsoft.com/fwlink/?LinkId=204847), autrement dit, un <xref:System.Threading.Tasks.Task>ou un <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 Dans le code suivant, la <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>retourne `getContentsTask`, un `Task(Of Byte())`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient> La tâche est une promesse de produire le tableau d’octets réel lorsque l’opération est terminée. L'opérateur `Await` est appliqué à `getContentsTask` pour suspendre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé. Entre-temps, le contrôle revient à l'appelant de `SumPageSizesAsync`. Quand `getContentsTask` est terminé, l'expression `Await` s'évalue en tableau d'octets.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  Pour un exemple complet, consultez la page [procédure pas à pas : accès Web à l’aide de Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger l’exemple à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) sur le site Web Microsoft. L'exemple est dans le projet AsyncWalkthrough_HttpClient.  
  
 Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task(Of TResult)`, le type de la `Await` expression est TResult. Si `Await` est appliqué au résultat d’un appel de méthode qui retourne un `Task`, le `Await` expression ne retourne aucune valeur. L'exemple suivant illustre la différence.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Un `Await` expression ou une instruction ne bloque pas le thread sur lequel il s’exécute. Au lieu de cela, elle entraîne le compilateur à inscrire le reste de la méthode async, après le `Await` expression, comme une liaison dans la tâche attendue. Le contrôle revient alors à l'appelant de la méthode async. Quand la tâche est terminée, elle appelle sa continuation et l’exécution de la méthode async reprend là où elle s’était arrêtée.  
  
 Un `Await` expression peut se produire uniquement dans le corps d’une expression lambda ou de la méthode englobante immédiate marquée par une `Async` modificateur. Le terme *Await* sert à un mot clé uniquement dans ce contexte. Partout ailleurs, il est interprété en tant qu'identificateur. Dans l’expression lambda ou de la méthode async, un `Await` expression ne peut pas se produire dans une expression de requête, dans le `catch` ou `finally` bloquer d’un [essayez... Catch... Enfin](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instruction, dans l’expression de variable de contrôle de boucle d’une `For` ou `For Each` boucle, ou dans le corps d’un [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instruction.  
  
## <a name="exceptions"></a>Exceptions  
 La plupart des méthodes async retourne <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final. L'opérateur `Await` accède à ces propriétés.  
  
 Si vous attendez une méthode async retournant des tâches qui lève une exception, l'opérateur `Await` lève de nouveau l'exception.  
  
 Si vous attendez une méthode async retournant des tâches qui est annulée, la `Await` opérateur lève à nouveau une <xref:System.OperationCanceledException>.</xref:System.OperationCanceledException>  
  
 Une tâche qui se trouve dans un état d’erreur peut refléter plusieurs exceptions.  Par exemple, la tâche peut être le résultat d’un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> Quand vous attendez une telle tâche, l’opération await lève à nouveau une seule des exceptions. Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.  
  
 Pour obtenir des exemples de gestion des erreurs dans les méthodes asynchrones, consultez [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Exemple  
 L'exemple Windows Forms suivant illustre l'utilisation de `Await` dans une méthode async, `WaitAsynchronouslyAsync`. Comparez le comportement de cette méthode avec celui de `WaitSynchronously`. Sans un `Await` (opérateur), `WaitSynchronously` s’exécute de façon synchrone en dépit de l’utilisation de la `Async` modificateur dans sa définition et un appel à <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>dans son corps.</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Procédure pas à pas : Accès Web en utilisant Async et Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
