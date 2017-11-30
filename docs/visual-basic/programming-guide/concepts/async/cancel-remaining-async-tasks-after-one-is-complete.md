---
title: "Annuler les tâches Asynch restantes, une fois qu’un est terminée (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 698ccf5901a77438368b9bf768b88ca6f90fdcbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Annuler les tâches Asynch restantes, une fois qu’un est terminée (Visual Basic)
Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> avec un <xref:System.Threading.CancellationToken> pour annuler toutes les tâches restantes quand une tâche est terminée. La méthode `WhenAny` accepte un argument qui est une collection de tâches. La méthode démarre toutes les tâches et retourne une tâche unique. Cette dernière est terminée une fois que toutes les tâches de la collection sont terminées.  
  
 Cet exemple montre comment utiliser un jeton d’annulation avec `WhenAny` pour attendre la fin de la première tâche de la collection et annuler les tâches restantes. Chaque tâche télécharge le contenu d’un site web. L’exemple affiche la longueur du contenu du premier téléchargement terminé et annule les autres téléchargements.  
  
> [!NOTE]
>  Pour exécuter les exemples, Visual Studio 2012 ou ultérieur et le .NET Framework 4.5 ou ultérieur doivent être installés sur votre ordinateur.  
  
## <a name="downloading-the-example"></a>Téléchargement de l'exemple  
 Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046), puis procédez comme suit.  
  
1.  Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui conserve l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.  
  
4.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterOneTask**, puis choisissez **Définir comme projet de démarrage**.  
  
5.  Appuyez sur la touche F5 pour exécuter le projet.  
  
     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.  
  
6.  Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.  
  
 Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.  
  
## <a name="building-the-example"></a>Génération de l’exemple  
 L’exemple de cette rubrique ajoute au projet développé dans [annuler une tâche asynch ou une liste de tâches](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) pour annuler une liste de tâches. Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.  
  
 Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**. Ajoutez les changements de cette rubrique à ce projet.  
  
 Dans le fichier MainWindow.xaml.vb de la **CancelAListOfTasks** projet d’équipe, démarrez la transition en déplaçant les étapes de traitement pour chaque site Web à partir de la boucle dans `AccessTheWebAsync` à la méthode asynchrone suivant.  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 Dans `AccessTheWebAsync`, cet exemple utilise une requête, la méthode <xref:System.Linq.Enumerable.ToArray%2A> et la méthode `WhenAny` pour créer et démarrer un tableau de tâches. L’application de `WhenAny` au tableau retourne une tâche unique qui, quand elle est attendue, prend la valeur de la première tâche terminée dans le tableau de tâches.  
  
 Dans `AccessTheWebAsync`, effectuez les changements suivants. Les astérisques signalent les changements dans le fichier de code.  
  
1.  Commentez ou supprimez la boucle.  
  
2.  Créer une requête qui, une fois exécutée, génère une collection de tâches génériques. Chaque appel à `ProcessURLAsync` retourne un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Appelez `ToArray` pour exécuter la requête et démarrer les tâches. L’application de la méthode `WhenAny` à l’étape suivante exécute la requête et démarre les tâches sans utiliser `ToArray`, mais il se peut que d’autres méthodes n’y parviennent pas. L’approche la plus sûre consiste à forcer l’exécution de la requête de manière explicite.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Appelez `WhenAny` sur la collection de tâches. `WhenAny` retourne `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.  Autrement dit, `WhenAny` retourne une tâche qui prend la valeur d’un `Task(Of Integer)` ou `Task<int>` unique quand elle est attendue. Cette tâche unique est la première tâche de la collection à se terminer. La tâche terminée en premier est assignée à `firstFinishedTask`. Le type de `firstFinishedTask` est <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier car il s’agit du type de retour de `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  Dans cet exemple, vous vous intéressez uniquement à la tâche qui se termine en premier. Par conséquent, utilisez <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour annuler les tâches restantes.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Enfin, attendez `firstFinishedTask` pour récupérer la longueur du contenu téléchargé.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Exécutez le programme plusieurs fois pour vérifier que différents téléchargements se terminent en premier.  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est le fichier MainWindow.xaml.vb ou MainWindow.xaml.cs complet pour l’exemple. Des astérisques marquent les éléments ajoutés pour cet exemple.  
  
 Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.  
  
 Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Ajuster une application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Exemple Async : ajuster une application](http://go.microsoft.com/fwlink/?LinkId=255046)
