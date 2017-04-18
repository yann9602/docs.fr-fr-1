---
title: "Comment : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic) | Documents Microsoft"
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
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 46c5cb9328f2fa1a4ffc5116d318bc3286419e13
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Comment : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)
Vous pouvez améliorer les performances de la solution async dans [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) à l’aide de la <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>méthode.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> Cette méthode attend plusieurs opérations asynchrones, qui sont représentées sous la forme d’une collection de tâches de façon asynchrone.  
  
 Vous aurez peut-être remarqué dans la procédure pas à pas par les sites Web de téléchargement à différentes vitesses. Un des sites Web est parfois très lent, ce qui retarde tous les autres téléchargements. Lorsque vous exécutez les solutions asynchrones que vous créez dans la procédure pas à pas, vous pouvez quitter le programme facilement si vous ne souhaitez pas attendre, mais une meilleure option consisterait à démarrer tous les téléchargements en même temps et attendre plus rapidement téléchargements se poursuivre sans attendre de celui qui est retardée.  
  
 Vous appliquez le `Task.WhenAll` méthode à une collection de tâches. L’application de `WhenAll` retourne une tâche unique qui n’est pas terminée avant la fin de chaque tâche dans la collection. Les tâches s’exécutent en parallèle, mais aucun des threads supplémentaires ne sont créés. Les tâches peuvent effectuer dans n’importe quel ordre.  
  
> [!IMPORTANT]
>  Les procédures suivantes décrivent les extensions pour les applications asynchrones qui sont développées dans [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez développer les applications à la fin de la procédure pas à pas ou de téléchargement à partir du code de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=255191).  
>   
>  Pour exécuter l’exemple, vous devez disposer de Visual Studio 2012 ou version ultérieure est installé sur votre ordinateur.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Pour ajouter Task.WhenAll à votre solution GetURLContentsAsync  
  
1.  Ajouter la `ProcessURLAsync` méthode à la première application qui est développée dans [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Si vous avez téléchargé le code à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=255191), ouvrez le projet AsyncWalkthrough, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.vb.  
  
    -   Si vous avez développé le code en suivant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui inclut le `GetURLContentsAsync` (méthode). Le fichier MainWindow.xaml.vb pour cette application est le premier exemple dans la section « Code exemples à partir de la procédure complète ».  
  
     Le `ProcessURLAsync` méthode consolide les actions dans le corps de la `For Each` dans une boucle `SumPageSizesAsync` dans la procédure d’origine. La méthode de façon asynchrone télécharge le contenu d’un site Web spécifié en tant que tableau d’octets, affiche et retourne la longueur du tableau d’octets.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Commentez ou supprimez la `For Each` boucle dans `SumPageSizesAsync`, comme illustré dans le code suivant.  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  Créer une collection de tâches. Le code suivant définit un [requête](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) qui, lorsqu’elle est exécutée par le <xref:System.Linq.Enumerable.ToArray%2A>méthode crée une collection de tâches qui téléchargent le contenu de chaque site Web.</xref:System.Linq.Enumerable.ToArray%2A> Les tâches sont démarrés lorsque la requête est évaluée.  
  
     Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Appliquer `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll`Retourne une tâche unique qui se termine lorsque toutes les tâches dans la collection de tâches terminées.  
  
     Dans l’exemple suivant, la `Await` expression attend l’achèvement de l’unique tâche `WhenAll` retourne. L’expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site Web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code que vous avez ajouté à l’étape précédente.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Enfin, utilisez la <xref:System.Linq.Enumerable.Sum%2A>méthode pour calculer la somme des longueurs de tous les sites Web.</xref:System.Linq.Enumerable.Sum%2A> Ajoutez la ligne suivante à `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Pour ajouter Task.WhenAll à la solution HttpClient.GetByteArrayAsync  
  
1.  Ajoutez la version suivante de `ProcessURLAsync` à l’autre application est développée dans [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Si vous avez téléchargé le code à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=255191), ouvrez le projet AsyncWalkthrough_HttpClient, puis ajoutez `ProcessURLAsync` au fichier MainWindow.xaml.vb.  
  
    -   Si vous avez développé le code en suivant la procédure pas à pas, ajoutez `ProcessURLAsync` à l’application qui utilise le `HttpClient.GetByteArrayAsync` (méthode). Le fichier MainWindow.xaml.vb pour cette application est le deuxième exemple dans la section « Code exemples à partir de la procédure complète ».  
  
     Le `ProcessURLAsync` méthode consolide les actions dans le corps de la `For Each` dans une boucle `SumPageSizesAsync` dans la procédure d’origine. La méthode de façon asynchrone télécharge le contenu d’un site Web spécifié en tant que tableau d’octets, affiche et retourne la longueur du tableau d’octets.  
  
     La seule différence avec le `ProcessURLAsync` méthode dans la procédure précédente est l’utilisation de la <xref:System.Net.Http.HttpClient>instance `client`.</xref:System.Net.Http.HttpClient>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Commentez ou supprimez la `For Each` boucle dans `SumPageSizesAsync`, comme illustré dans le code suivant.  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
  
    ```  
  
3.  Définir un [requête](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) qui, lorsqu’elle est exécutée par le <xref:System.Linq.Enumerable.ToArray%2A>méthode crée une collection de tâches qui téléchargent le contenu de chaque site Web.</xref:System.Linq.Enumerable.ToArray%2A> Les tâches sont démarrés lorsque la requête est évaluée.  
  
     Ajoutez le code suivant à la méthode `SumPageSizesAsync` après la déclaration de `client` et `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Ensuite, appliquez `Task.WhenAll` à la collection de tâches, `downloadTasks`. `Task.WhenAll`Retourne une tâche unique qui se termine lorsque toutes les tâches dans la collection de tâches terminées.  
  
     Dans l’exemple suivant, la `Await` expression attend l’achèvement de l’unique tâche `WhenAll` retourne. Lorsque vous avez terminé, le `Await` expression correspond à un tableau d’entiers, où chaque entier est la longueur d’un site Web téléchargé. Ajoutez le code suivant à `SumPageSizesAsync`, juste après le code que vous avez ajouté à l’étape précédente.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Enfin, utilisez la <xref:System.Linq.Enumerable.Sum%2A>méthode pour obtenir la somme des longueurs de tous les sites Web.</xref:System.Linq.Enumerable.Sum%2A> Ajoutez la ligne suivante à `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Pour tester les solutions Task.WhenAll  
  
-   Pour une solution, choisissez la touche F5 pour exécuter le programme, puis le **Démarrer** bouton. La sortie doit ressembler à la sortie de solutions async [procédure pas à pas : accès Web à l’aide de Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Toutefois, notez que les sites Web apparaissent dans un ordre différent chaque fois.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre les extensions pour le projet qui utilise le `GetURLContentsAsync` méthode pour télécharger du contenu à partir du web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
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
  
## <a name="example"></a>Exemple  
 Le code suivant montre les extensions pour le projet qui utilise la méthode `HttpClient.GetByteArrayAsync` pour télécharger le contenu à partir du web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>   
 [Procédure pas à pas : Accès Web en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
