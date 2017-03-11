---
title: "Await Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Await"
helpviewer_keywords: 
  - "Await operator [Visual Basic]"
  - "Await [Visual Basic]"
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Await Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous appliquez l'opérateur d'un `Await` à un opérande dans une méthode asynchrone ou une expression lambda pour interrompre l'exécution de la méthode jusqu'à ce que la tâche attendue se termine.  La tâche représente le travail en cours.  
  
 La méthode dans laquelle `Await` est utilisé doit avoir un modificateur d' [Async](../../../visual-basic/language-reference/modifiers/async.md).  Une telle méthode, définie en utilisant le modificateur `Async`, et contenant généralement une ou plusieurs expressions `Await`, est appelée *méthode asynchrone*.  
  
> [!NOTE]
>  Les mots clés `Async` et `Await` ont été introduits dans Visual Studio 2012.  Pour une présentation de la programmation asynchrone, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Généralement, la tâche à laquelle l'opérateur `Await` est appliqué est la valeur de retour d'un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](http://go.microsoft.com/fwlink/?LinkId=204847), c'est à dire, un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.  
  
 Dans le code suivant, la méthode <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retourne `getContentsTask`, une `Task(Of Byte())`.  La tâche est la promesse de produire le tableau d'octets réel lorsque l'opération est terminée.  L'opérateur `Await` est appliqué à `getContentsTask` pour interrompre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé.  Dans le même temps, le contrôle retourne à l'appelant de `SumPageSizesAsync`, .  Lorsque `getContentsTask` est terminé, l'expression `Await` correspond à un tableau d'octets.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  Pour obtenir un exemple complet, consultez [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Vous pouvez télécharger l'exemple à partir de [Exemples de code du développeur](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) sur le site Web Microsoft.  L'exemple se trouve dans le projet AsyncWalkthrough\_HttpClient.  
  
 Si `Await` est appliqué au résultat d'un appel de méthode qui retourne une `Task(Of TResult)`, le type de l'expression `Await` est void.  Si `Await` est appliqué au résultat d'un appel de méthode qui retourne une `Task`, l'expression `Await` ne retourne pas de valeur.  La différence est illustrée dans l'exemple suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Une expression ou un état `Await` ne bloque pas le thread sur lequel elle s'exécute.  À la place, cela provoque la connexion du compilateur au reste de la méthode async, après l'expression `Await`, comme une continuation sur la tâche attendue.  Contrôle, puis retourne à l'appelant de la méthode async.  Lorsque la tâche se termine, elle appelle sa continuation, et l'exécution de la méthode async reprend où elle a été arrêtée.  
  
 Une expression `Await` ne peut se produire que dans le corps d'une méthode immédiatement englobante, ou d'une expression lambda, ou d'une méthode anonyme qui est marquée par un modificateur `Async`.  Le terme *await* sert de mot clé uniquement dans ce contexte.  Ailleurs, il est interprété comme un identificateur.  Dans la méthode async ou l'expression lambda, une expression `Await` ne peut pas apparaître dans une expression de requête, dans un bloc `catch` ou `finally` d'une instruction [Try… Catch… Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md), dans l'expression variable de contrôle de boucle d'une boucle `For` ou `For Each`, ou dans le corps d'une instruction [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
## Exceptions  
 La plupart des méthodes async retournent <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  Les propriétés de la tâche retournée contiennent des informations sur son état et son historique, par exemple si la tâche est terminée, si la méthode async a provoqué une exception ou a été annulée ainsi que le résultat final.  L'opérateur `Await` accède à ces propriétés.  
  
 Si vous attendez une méthode asynchrone de retour de tâche qui provoque une exception, l'opérateur `Await` relève l'exception.  
  
 Si vous attendez une méthode asynchrone de retour de tâche qui est annulée, l'opérateur `Await` relève une <xref:System.OperationCanceledException>.  
  
 Une tâche unique avec un état d'erreur peut refléter plusieurs exceptions.  Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Lorsque vous attendez une telle tâche, l'opération await lève à nouveau une seule des exceptions.  Toutefois, vous ne pouvez pas prédire quelles exceptions seront immédiatement levées.  
  
 Pour obtenir des exemples de gestion des erreurs dans des méthodes async, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Exemple  
 L'exemple Windows Forms suivant illustre l'utilisation d'`Await` dans une méthode async, `WaitAsynchronouslyAsync`.  Comparez le comportement de cette méthode avec le comportement de `WaitSynchronously`.  Sans un opérateur `Await` appliqué à une tâche, `WaitSynchronously` s'exécute de façon synchrone malgré l'utilisation du modificateur `Async` dans sa définition et un appel à <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> dans son corps.  
  
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
  
## Voir aussi  
 [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)