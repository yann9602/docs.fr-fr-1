---
title: "async (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "async_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "async [C#]"
  - "mot clé async [C#]"
  - "méthode async [C#]"
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 52
---
# async (r&#233;f&#233;rence C#)
Utilisez le modificateur `async` pour spécifier qu'une méthode, une [expression lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) sont asynchrones.  Si vous utilisez ce modificateur sur une méthode ou une expression, il s'agit d'une méthode async.  
  
```c#  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode async utilise le mot clé `await` un travail potentiellement long sans bloquer le thread de l'appelant, lisez la présentation dans [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
```  
string contents = await contentsTask;  
```  
  
 La méthode s'exécute de façon synchrone jusqu'à ce qu'elle atteigne sa première expression `await`, où elle est interrompue jusqu'à ce que la tâche attendue soit terminée.  Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.  
  
 Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone.  Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas `await`, car cette situation peut indiquer une erreur.  Consultez [Avertissement du compilateur \(niveau 1\) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme.  Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## Exemple  
 L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`.  Le résultat de la méthode async est la longueur d'un site Web téléchargé.  Le code convient pour une application Windows Presentation Foundation \(WPF\) ou une application Windows Store que vous créez dans [!INCLUDE[vs_dev12](../../../csharp/getting-started/includes/vs-dev12-md.md)] ; consultez les commentaires du code pour configurer l'application.  
  
```c#  
// You can run this code in Visual Studio 2013 as a WPF app or a Windows Store app.  
// You need a button (StartButton) and a textbox (ResultsTextBox).  
// Remember to set the names and handler so that you have something like this:  
// <Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
//         Click="StartButton_Click" Name="StartButton"/>  
// <TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
//          Text="TextBox" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
  
// To run the code as a WPF app:  
//    paste this code into the MainWindow class in MainWindow.xaml.cs,  
//    add a reference to System.Net.Http, and  
//    add a using directive for System.Net.Http.  
  
// To run the code as a Windows Store app:  
//    paste this code into the MainPage class in MainPage.xaml.cs, and  
//    add using directives for System.Net.Http and System.Threading.Tasks.  
  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ExampleMethodAsync returns a Task<int>, which means that the method  
    // eventually produces an int result. However, ExampleMethodAsync returns  
    // the Task<int> value as soon as it reaches an await.  
    ResultsTextBox.Text += "\n";  
    try  
    {  
        int length = await ExampleMethodAsync();  
        // Note that you could put "await ExampleMethodAsync()" in the next line where  
        // "length" is, but due to when '+=' fetches the value of ResultsTextBox, you  
        // would not see the global side effect of ExampleMethodAsync setting the text.  
        ResultsTextBox.Text += String.Format("Length: {0}\n", length);  
    }  
    catch (Exception)  
    {  
        // Process the exception if one occurs.  
    }  
}  
  
public async Task<int> ExampleMethodAsync()  
{  
    var httpClient = new HttpClient();  
    int exampleInt = (await httpClient.GetStringAsync("http://msdn.microsoft.com")).Length;  
    ResultsTextBox.Text += "Preparing to finish ExampleMethodAsync.\n";  
    // After the following return statement, any method that's awaiting  
    // ExampleMethodAsync (in this case, StartButton_Click) can get the   
    // integer result.  
    return exampleInt;  
}  
// Output:  
// Preparing to finish ExampleMethodAsync.  
// Length: 53292  
  
```  
  
> [!IMPORTANT]
>  Pour plus d'informations sur les tâches et le code qui s'exécute en attendant une tâche, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Pour obtenir un exemple WPF complet qui utilise des éléments semblables, consultez [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Vous pouvez télécharger le code de procédure depuis [Exemples de code du développeur](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
## Types de retours  
 Une méthode async peut avoir un type de retour <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, ou [void](../../../csharp/language-reference/keywords/void.md).  La méthode ne peut pas déclarer de paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), mais elle peut appeler des méthodes comportant ces paramètres.  
  
 Vous spécifiez `Task<TResult>` comme type de retour d'une méthode async si l'instruction [return](../../../csharp/language-reference/keywords/return.md) de la méthode spécifie un opérande de type `TResult`.  Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.  En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.  
  
 Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour.  L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.  
  
 Pour plus d'informations et d'exemples, consultez [Types de retour Async](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [await](../../../csharp/language-reference/keywords/await.md)   
 [Procédure pas à pas : accès au Web avec Async et Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)