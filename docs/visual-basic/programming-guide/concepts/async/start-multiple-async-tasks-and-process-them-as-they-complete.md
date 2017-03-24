---
title: "Démarrer plusieurs tâches Asynch et les traiter comme terminées (Visual Basic) | Documents Microsoft"
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
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
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
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Démarrer plusieurs tâches Asynch et les traiter comme terminées (Visual Basic)
À l’aide de <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, vous pouvez démarrer plusieurs tâches en même temps et traiter un par un, comme ils sont terminées au lieu de les traitent dans l’ordre dans lequel ils sont démarrés.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>  
  
 L’exemple suivant utilise une requête pour créer une collection de tâches. Chaque tâche télécharge le contenu d’un site Web spécifié. Dans chaque itération d’un certain temps en boucle, un appel à attendue `WhenAny` retourne la tâche dans la collection de tâches qui se termine en premier téléchargement. Cette tâche est supprimée de la collection et traitée. La boucle se répète jusqu'à ce que la collection ne contient aucun davantage de tâches.  
  
> [!NOTE]
>  Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.  
  
## <a name="downloading-the-example"></a>Téléchargement de l'exemple  
 Vous pouvez télécharger le projet Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046) puis procédez comme suit.  
  
1.  Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui contient l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProcessTasksAsTheyFinish** de projet, puis choisissez **définir comme projet de démarrage**.  
  
5.  Appuyez sur la touche F5 pour exécuter le projet.  
  
     Choisissez les touches Ctrl + F5 pour exécuter le projet sans le déboguer.  
  
6.  Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargés n’apparaissent pas toujours dans le même ordre.  
  
 Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.  
  
## <a name="building-the-example"></a>Création de l’exemple  
 Cet exemple ajoute le code développé dans [annuler les tâches Asynch restantes après une est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) et utilise la même interface utilisateur.  
  
 Pour générer l’exemple vous-même, étape par étape, suivez les instructions dans la téléchargement de la section « Exemple », mais choisissez **CancelAfterOneTask** comme le **projet de démarrage**. Ajoutez les modifications de cette rubrique pour le `AccessTheWebAsync` méthode dans le projet. Les modifications sont marquées par des astérisques.  
  
 Le **CancelAfterOneTask** projet inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches. Chaque appel à `ProcessURLAsync` dans le code suivant renvoie une <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier.</xref:System.Threading.Tasks.Task%601>  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Dans le fichier MainWindow.xaml.vb du projet, apportez les modifications suivantes à la `AccessTheWebAsync` (méthode).  
  
-   Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>au lieu de <xref:System.Linq.Enumerable.ToArray%2A>.</xref:System.Linq.Enumerable.ToArray%2A> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
-   Ajouter un certain temps boucle qui effectue les étapes suivantes pour chaque tâche dans la collection.  
  
    1.  Attend un appel à `WhenAny` pour identifier la première tâche dans la collection à la fin de son téléchargement.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
    2.  Cette tâche supprime de la collection.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
    3.  Attend de `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`. Le `firstFinishedTask` variable est une <xref:System.Threading.Tasks.Task%601>où `TReturn` est un entier.</xref:System.Threading.Tasks.Task%601> La tâche est déjà terminée, mais vous await pour récupérer la longueur du site Web téléchargé, comme le montre l’exemple suivant.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Vous devez exécuter le projet plusieurs fois pour vérifier que les longueurs téléchargés n’apparaissent pas toujours dans le même ordre.  
  
> [!CAUTION]
>  Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes impliquant un petit nombre de tâches. Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter. Pour plus d’informations et d’exemples, consultez [tâches de traitement qu’elles complète](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est le texte complet du fichier MainWindow.xaml.vb pour l’exemple. Les astérisques marquent les éléments qui ont été ajoutés pour cet exemple.  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Réglage de votre Application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Exemple Async : Réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046)
