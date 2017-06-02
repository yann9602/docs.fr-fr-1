---
title: "async (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
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
ms.sourcegitcommit: 50e128137fde445f64e10cf7c2a1ee5fdecb34e6
ms.openlocfilehash: e7f4cfa81de3c4db41d9303abf65cfd0edc926a4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/01/2017

---
# <a name="async-c-reference"></a>async (référence C#)
Utilisez le modificateur `async` pour spécifier qu’une méthode, une [expression lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) sont asynchrones. Si vous utilisez ce modificateur sur une méthode ou une expression, il s'agit d'une méthode async.  
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode async utilise le mot clé `await` pour un travail potentiellement long sans bloquer le thread de l’appelant, lisez la présentation dans [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).  
  
```  
string contents = await contentsTask;  
```  
  
 La méthode s'exécute de façon synchrone jusqu'à ce qu'elle atteigne sa première expression `await`, où elle est interrompue jusqu'à ce que la tâche attendue soit terminée. Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.  
  
 Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone. Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas `await`, car cette situation peut indiquer une erreur. Consultez [Avertissement du compilateur (niveau 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme. Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`. Le résultat de la méthode async est la longueur d'un site Web téléchargé. Le code convient pour une application WPF (Windows Presentation Foundation) ou une application du Windows Store que vous créez dans Visual Studio ; consultez les commentaires du code pour configurer l’application.  
  
```csharp  
// You can run this code in Visual Studio as a WPF app or a Windows Store app.  
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
>  Pour plus d’informations sur les tâches et sur le code qui s’exécute en attendant une tâche, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md). Pour obtenir un exemple WPF complet qui utilise des éléments similaires, consultez [Procédure pas à pas : accès au web avec Async et Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger le code de procédure à partir des [Exemples de code du développeur](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
## <a name="return-types"></a>Types de retours  
 Une méthode async peut avoir un type de retour <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou [void](../../../csharp/language-reference/keywords/void.md). La méthode ne peut pas déclarer de paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), mais elle peut appeler des méthodes comportant ces paramètres.  
  
 Vous spécifiez `Task<TResult>` comme type de retour d’une méthode async si l’instruction [return](../../../csharp/language-reference/keywords/return.md) de la méthode spécifie un opérande de type `TResult`. Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée. En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.  
  
 Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour. L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.  
  
 Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [await](../../../csharp/language-reference/keywords/await.md)   
 [Procédure pas à pas : accès au web avec Async et Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Programmation asynchrone avec Async et Await](../../../csharp/programming-guide/concepts/async/index.md)
