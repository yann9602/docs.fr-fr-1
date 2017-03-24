---
title: "Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e4c41cc3813a9f96d944d115c6aaa5c5842a629b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await (Visual Basic)
Dans une méthode asynchrone, les tâches sont démarrées lorsqu’elles sont créées. Le [Await](../../../../visual-basic/language-reference/operators/await-operator.md) opérateur est appliqué à la tâche au point dans la méthode où le traitement ne peut pas se poursuivre jusqu'à ce que la tâche se termine. Fréquence à laquelle une tâche est attendue dès sa création, comme le montre l’exemple suivant.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Toutefois, vous pouvez séparer la création de la tâche qui ne dépend de l’achèvement de la tâche à partir de l’attente de la tâche si votre programme présente d’autres tâches à accomplir.  
  
```vb  
' The following line creates and starts the task.  
Dim myTask = someWebAccessMethodAsync(url)  
  
' While the task is running, you can do other work that does not depend  
' on the results of the task.  
' . . . . .  
  
' The application of Await suspends the rest of this method until the task is   
' complete.  
Dim result = Await myTask  
  
```  
  
 Entre une tâche et en lui, vous pouvez démarrer d’autres tâches. Les tâches supplémentaires implicitement exécutées en parallèle, mais aucun des threads supplémentaires ne sont créés.  
  
 Le programme suivant démarre trois téléchargements web asynchrones et les attend ensuite dans l’ordre dans lequel ils sont appelés. Notez que, lorsque vous exécutez le programme, ce qui les tâches ne se terminent toujours dans l’ordre dans lequel elles sont créées et attendues. Ils commencent à s’exécuter lorsqu’ils sont créés, et un ou plusieurs des tâches peuvent se terminer avant que la méthode n’atteigne les expressions await.  
  
> [!NOTE]
>  Pour mener à bien ce projet, vous devez disposer Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure est installé sur votre ordinateur.  
  
 Pour un autre exemple lancer plusieurs tâches en même temps, consultez [Comment : étendre le Walkthrough asynchrone à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Vous pouvez télécharger le code de cet exemple à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=254906).  
  
### <a name="to-set-up-the-project"></a>Pour configurer le projet  
  
1.  Pour configurer une application WPF, procédez comme suit. Vous trouverez des instructions détaillées sur ces étapes de [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Créer une application WPF qui contient une zone de texte et un bouton. Nommez le bouton `startButton`et le nom de la zone de texte `resultsTextBox`.  
  
    -   Ajoutez une référence pour <xref:System.Net.Http>.</xref:System.Net.Http>  
  
    -   Dans le fichier MainWindow.xaml.vb, ajoutez un `Imports` instruction pour `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Pour ajouter le code  
  
1.  Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton pour créer la `startButton_Click` MainWindow.xaml.vb Gestionnaire d’événements.  
  
2.  Copiez le code suivant et collez-le dans le corps de `startButton_Click` dans MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Le code appelle une méthode asynchrone, `CreateMultipleTasksAsync`, ce qui implique l’application.  
  
3.  Ajoutez les méthodes suivantes de la prise en charge pour le projet :  
  
    -   `ProcessURLAsync`utilise un <xref:System.Net.Http.HttpClient>méthode pour télécharger le contenu d’un site Web en tant que tableau d’octets.</xref:System.Net.Http.HttpClient> La méthode prise en charge, `ProcessURLAsync` affiche ensuite et retourne la longueur du tableau.  
  
    -   `DisplayResults`Affiche le nombre d’octets dans le tableau d’octets pour chaque URL. Cette affiche présente lorsque chaque tâche de téléchargement est terminé.  
  
     Copiez les méthodes suivantes et collez-les après le `startButton_Click` MainWindow.xaml.vb Gestionnaire d’événements.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  Enfin, définissez la méthode `CreateMultipleTasksAsync`, qui effectue les étapes suivantes.  
  
    -   La méthode déclare une `HttpClient` objet, que vous devez accéder à la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>dans `ProcessURLAsync`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>  
  
    -   Cette méthode crée et démarre les trois tâches de type <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier.</xref:System.Threading.Tasks.Task%601> Que chaque tâche se termine, `DisplayResults` affiche URL son et la longueur du contenu téléchargé. Étant donné que les tâches sont exécutent de façon asynchrone, l’ordre dans lequel les résultats peuvent différer de l’ordre dans lequel ils ont été déclarés.  
  
    -   La méthode attend l’achèvement de chaque tâche. Chaque `Await` opérateur suspend l’exécution de `CreateMultipleTasksAsync` jusqu'à la fin de la tâche attendue. L’opérateur récupère également la valeur de retour de l’appel à `ProcessURLAsync` à partir de chaque tâche terminée.  
  
    -   Lorsque les tâches ont été effectuées et les valeurs entières ont été récupérées, la méthode additionne les longueurs des sites Web et affiche le résultat.  
  
     Copiez la méthode suivante et collez-la dans votre solution.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
    ```  
  
5.  Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .  
  
     Exécutez le programme plusieurs fois pour vérifier que les trois tâches ne se terminer toujours dans le même ordre et que l’ordre dans lequel ils ont terminé n’est pas nécessairement l’ordre dans lequel elles sont créées et attendues.  
  
## <a name="example"></a>Exemple  
 Le code suivant contient l’exemple complet.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
        resultsTextBox.Clear()  
        Await CreateMultipleTasksAsync()  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Accès Web en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Comment : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
