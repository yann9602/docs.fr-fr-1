---
title: "Annuler les tâches Asynch restantes après une est terminée (Visual Basic) | Documents Microsoft"
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
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
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
ms.openlocfilehash: 1b70822edd972ac33614ab49faad6ff50b0e80b7
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Annuler les tâches Asynch restantes après une est terminée (Visual Basic)
À l’aide de la <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>méthode avec un <xref:System.Threading.CancellationToken>, vous pouvez annuler toutes les tâches restantes lorsqu’une tâche est terminée.</xref:System.Threading.CancellationToken> </xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> Le `WhenAny` méthode prend un argument qui est une collection de tâches. La méthode démarre toutes les tâches et renvoie une seule tâche. La tâche est terminée lorsque toutes les tâches dans la collection sont terminée.  
  
 Cet exemple montre comment utiliser un jeton d’annulation avec `WhenAny` à maintenir la première tâche à la fin de la collection de tâches et d’annuler les tâches restantes. Chaque tâche télécharge le contenu d’un site Web. L’exemple affiche la longueur du contenu de la fin du premier téléchargement et annule les autres téléchargements.  
  
> [!NOTE]
>  Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.  
  
## <a name="downloading-the-example"></a>Téléchargement de l'exemple  
 Vous pouvez télécharger le projet Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046) puis procédez comme suit.  
  
1.  Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui contient l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **CancelAfterOneTask** de projet, puis choisissez **définir comme projet de démarrage**.  
  
5.  Appuyez sur la touche F5 pour exécuter le projet.  
  
     Choisissez les touches Ctrl + F5 pour exécuter le projet sans le déboguer.  
  
6.  Exécutez le programme plusieurs fois pour vérifier que les téléchargements différents termine d’abord.  
  
 Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.  
  
## <a name="building-the-example"></a>Création de l’exemple  
 L’exemple de cette rubrique ajoute au projet développé dans [annuler une tâche asynch ou une liste de tâches](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) pour annuler une liste de tâches. L’exemple utilise la même interface utilisateur, bien que le **Annuler** bouton n’est pas utilisé de manière explicite.  
  
 Pour générer l’exemple vous-même, étape par étape, suivez les instructions dans la téléchargement de la section « Exemple », mais choisissez **CancelAListOfTasks** comme le **projet de démarrage**. À ce projet, ajoutez les modifications dans cette rubrique.  
  
 Dans le fichier MainWindow.xaml.vb de la **CancelAListOfTasks** de projet, démarrez la transition en déplaçant les étapes de traitement pour chaque site Web à partir de la boucle de `AccessTheWebAsync` à la méthode asynchrone suivant.  
  
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
  
 Dans `AccessTheWebAsync`, cet exemple utilise une requête, le <xref:System.Linq.Enumerable.ToArray%2A>(méthode) et le `WhenAny` pour créer et démarrer un tableau de tâches.</xref:System.Linq.Enumerable.ToArray%2A> L’application de `WhenAny` dans le tableau renvoie une seule tâche qui, pendant l’attente, prend la valeur de la première tâche pour atteindre la fin du tableau de tâches.  
  
 Apportez les modifications suivantes dans `AccessTheWebAsync`. Les astérisques marquer les modifications dans le fichier de code.  
  
1.  Commentez ou supprimez la boucle.  
  
2.  Créer une requête qui, lorsqu’elle est exécutée, produit une collection de tâches génériques. Chaque appel à `ProcessURLAsync` renvoie un <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier.</xref:System.Threading.Tasks.Task%601>  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
3.  Appelez `ToArray` pour exécuter la requête et de démarrer les tâches. L’application de la `WhenAny` méthode à l’étape suivante serait exécuter la requête et lancer les tâches sans utiliser `ToArray`, mais les autres méthodes ne peuvent pas. La plus sûre consiste à forcer l’exécution de la requête explicitement.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
4.  Appeler `WhenAny` sur la collection de tâches. `WhenAny`Retourne un `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.  Autrement dit, `WhenAny` retourne une tâche qui évalue à un seul `Task(Of Integer)` ou `Task<int>` lorsqu’il est attendu. Cette tâche unique est la première tâche dans la collection se termine. La tâche terminé est affectée à `firstFinishedTask`. Le type de `firstFinishedTask` est <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier, car c’est le type de retour de `ProcessURLAsync`.</xref:System.Threading.Tasks.Task%601>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  Dans cet exemple, vous êtes uniquement intéressé par la tâche se termine en premier. Par conséquent, utilisez <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>pour annuler les tâches restantes.</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Enfin, await `firstFinishedTask` pour extraire la longueur du contenu téléchargé.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Exécutez le programme plusieurs fois pour vérifier que les téléchargements différents termine d’abord.  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est le fichier MainWindow.xaml.vb ou MainWindow.xaml.cs complet pour l’exemple. Les astérisques marquent les éléments qui ont été ajoutés pour cet exemple.  
  
 Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</xref:System.Net.Http>  
  
 Vous pouvez télécharger le projet à partir de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
 <xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Réglage de votre Application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Exemple Async : Réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046)
