---
title: "await (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 3656141c32a04e3a32a2992185f4c418c6915482
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="await-c-reference"></a>await (référence C#)
L'opérateur `await` est appliqué à une tâche dans une méthode asynchrone pour interrompre l'exécution de la méthode jusqu'à ce que la tâche attendue se termine. La tâche représente un travail en cours.  
  
 La méthode asynchrone dans laquelle `await` est utilisé doit être modifiée par le mot clé [async](../../../csharp/language-reference/keywords/async.md). Cette méthode, définie à l’aide du modificateur `async` et contenant généralement une ou plusieurs expressions `await`, est appelée *méthode async*.  
  
> [!NOTE]
>  Les mots clés `async` et `await` ont été introduites dans Visual Studio 2012. Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).  
  
 La tâche à laquelle l’opérateur `await` est appliqué correspond généralement à la valeur de retour d’un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](http://go.microsoft.com/fwlink/?LinkId=204847). Les valeurs de type <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> en sont des exemples.  
  
 Dans le code suivant, la méthode <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retourne un `Task\<byte[]>`, `getContentsTask`. La tâche est une promesse de produire le tableau d’octets réel quand la tâche est terminée. L'opérateur `await` est appliqué à `getContentsTask` pour suspendre l'exécution dans `SumPageSizesAsync` jusqu'à ce que `getContentsTask` soit terminé. Entre-temps, le contrôle revient à l'appelant de `SumPageSizesAsync`. Quand `getContentsTask` est terminé, l'expression `await` s'évalue en tableau d'octets.  
  
```csharp  
private async Task SumPageSizesAsync()  
{  
    // To use the HttpClient type in desktop apps, you must include a using directive and add a   
    // reference for the System.Net.Http namespace.  
    HttpClient client = new HttpClient();  
    // . . .  
    Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
    byte[] urlContents = await getContentsTask;  
  
    // Equivalently, now that you see how it works, you can write the same thing in a single line.  
    //byte[] urlContents = await client.GetByteArrayAsync(url);  
    // . . .  
}  
```  
  
> [!IMPORTANT]
>  Pour obtenir un exemple complet, consultez [Procédure pas à pas : accès au web avec async et await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger l’exemple à partir des [exemples de code pour les développeurs](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) sur le site web de Microsoft. L'exemple est dans le projet AsyncWalkthrough_HttpClient.  
  
 Comme indiqué dans l'exemple précédent, si `await` est appliqué au résultat d'un appel de méthode qui retourne un `Task<TResult>`, alors le type de l'expression `await` est TResult. Si `await` est appliqué au résultat d'un appel de méthode qui retourne un `Task`, alors le type de l'expression `await` est void. L'exemple suivant illustre la différence.  
  
```csharp  
// Keyword await used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// Keyword await used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  
```  
  
 Une expression `await` ne bloque pas le thread sur lequel elle s'exécute. Elle indique plutôt au compilateur de signer le reste de la méthode async comme une continuation sur la tâche attendue. Le contrôle revient alors à l'appelant de la méthode async. Quand la tâche est terminée, elle appelle sa continuation et l'exécution de la méthode async reprend là où elle s'était arrêtée.  
  
 Une expression `await` peut se produire uniquement dans le corps d'une méthode immédiatement englobante, une expression lambda ou une méthode anonyme marquée par un modificateur `async`. Le terme *await* sert de mot clé uniquement dans ce contexte. Partout ailleurs, il est interprété en tant qu'identificateur. Dans la méthode, l’expression lambda ou la méthode anonyme, une expression `await` ne peut pas se produire dans le corps d’une fonction synchrone, dans une expression de requête, dans le bloc d’une [instruction lock](../../../csharp/language-reference/keywords/lock-statement.md) ou dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exceptions"></a>Exceptions  
 La plupart des méthodes async retournent un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>. Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final. L'opérateur `await` accède à ces propriétés.  
  
 Si vous attendez une méthode async retournant des tâches qui lève une exception, l'opérateur `await` lève de nouveau l'exception.  
  
 Si vous attendez une méthode async retournant des tâches qui est annulée, l’opérateur `await` lève de nouveau une exception <xref:System.OperationCanceledException>.  
  
 Une tâche qui se trouve dans un état d’erreur peut refléter plusieurs exceptions. Par exemple, la tâche peut être le résultat d’un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>. Quand vous attendez une telle tâche, l’opération await lève à nouveau une seule des exceptions. Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.  
  
 Pour obtenir des exemples de gestion des erreurs dans les méthodes asynchrones, consultez [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Exemple  
 L'exemple Windows Forms suivant illustre l'utilisation de `await` dans une méthode async, `WaitAsynchronouslyAsync`. Comparez le comportement de cette méthode avec celui de `WaitSynchronously`. Sans opérateur `await` appliqué à une tâche, `WaitSynchronously` s’exécute de façon synchrone en dépit de l’utilisation du modificateur `async` dans sa définition et d’un appel à <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> dans son corps.  
  
```csharp  
private async void button1_Click(object sender, EventArgs e)  
{  
    // Call the method that runs asynchronously.  
    string result = await WaitAsynchronouslyAsync();  
  
    // Call the method that runs synchronously.  
    //string result = await WaitSynchronously ();  
  
    // Display the result.  
    textBox1.Text += result;  
}  
  
// The following method runs asynchronously. The UI thread is not  
// blocked during the delay. You can move or resize the Form1 window   
// while Task.Delay is running.  
public async Task<string> WaitAsynchronouslyAsync()  
{  
    await Task.Delay(10000);  
    return "Finished";  
}  
  
// The following method runs synchronously, despite the use of async.  
// You cannot move or resize the Form1 window while Thread.Sleep  
// is running because the UI thread is blocked.  
public async Task<string> WaitSynchronously()  
{  
    // Add a using directive for System.Threading.  
    Thread.Sleep(10000);  
    return "Finished";  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md)   
 [Procédure pas à pas : accès au web avec async et await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [async](../../../csharp/language-reference/keywords/async.md)

