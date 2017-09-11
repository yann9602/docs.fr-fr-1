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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="b7960-102">Démarrer plusieurs tâches Asynch et les traiter comme terminées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7960-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="b7960-103">À l’aide de <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, vous pouvez démarrer plusieurs tâches en même temps et traiter un par un, comme ils sont terminées au lieu de les traitent dans l’ordre dans lequel ils sont démarrés.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b7960-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="b7960-104">L’exemple suivant utilise une requête pour créer une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="b7960-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="b7960-105">Chaque tâche télécharge le contenu d’un site Web spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7960-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="b7960-106">Dans chaque itération d’un certain temps en boucle, un appel à attendue `WhenAny` retourne la tâche dans la collection de tâches qui se termine en premier téléchargement.</span><span class="sxs-lookup"><span data-stu-id="b7960-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="b7960-107">Cette tâche est supprimée de la collection et traitée.</span><span class="sxs-lookup"><span data-stu-id="b7960-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="b7960-108">La boucle se répète jusqu'à ce que la collection ne contient aucun davantage de tâches.</span><span class="sxs-lookup"><span data-stu-id="b7960-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7960-109">Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7960-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="b7960-110">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="b7960-110">Downloading the Example</span></span>  
 <span data-ttu-id="b7960-111">Vous pouvez télécharger le projet Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046) puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="b7960-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="b7960-112">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b7960-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b7960-113">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="b7960-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="b7960-114">Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui contient l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="b7960-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="b7960-115">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProcessTasksAsTheyFinish** de projet, puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="b7960-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="b7960-116">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="b7960-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="b7960-117">Choisissez les touches Ctrl + F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="b7960-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="b7960-118">Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargés n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="b7960-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="b7960-119">Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b7960-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="b7960-120">Création de l’exemple</span><span class="sxs-lookup"><span data-stu-id="b7960-120">Building the Example</span></span>  
 <span data-ttu-id="b7960-121">Cet exemple ajoute le code développé dans [annuler les tâches Asynch restantes après une est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) et utilise la même interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7960-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="b7960-122">Pour générer l’exemple vous-même, étape par étape, suivez les instructions dans la téléchargement de la section « Exemple », mais choisissez **CancelAfterOneTask** comme le **projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="b7960-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="b7960-123">Ajoutez les modifications de cette rubrique pour le `AccessTheWebAsync` méthode dans le projet.</span><span class="sxs-lookup"><span data-stu-id="b7960-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="b7960-124">Les modifications sont marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="b7960-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="b7960-125">Le **CancelAfterOneTask** projet inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="b7960-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="b7960-126">Chaque appel à `ProcessURLAsync` dans le code suivant renvoie une <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="b7960-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="b7960-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b7960-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="b7960-128">Dans le fichier MainWindow.xaml.vb du projet, apportez les modifications suivantes à la `AccessTheWebAsync` (méthode).</span><span class="sxs-lookup"><span data-stu-id="b7960-128">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="b7960-129">Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>au lieu de <xref:System.Linq.Enumerable.ToArray%2A>.</xref:System.Linq.Enumerable.ToArray%2A> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b7960-129">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
<span data-ttu-id="b7960-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b7960-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
-   <span data-ttu-id="b7960-131">Ajouter un certain temps boucle qui effectue les étapes suivantes pour chaque tâche dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b7960-131">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="b7960-132">Attend un appel à `WhenAny` pour identifier la première tâche dans la collection à la fin de son téléchargement.</span><span class="sxs-lookup"><span data-stu-id="b7960-132">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
<span data-ttu-id="b7960-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b7960-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
    2.  <span data-ttu-id="b7960-134">Cette tâche supprime de la collection.</span><span class="sxs-lookup"><span data-stu-id="b7960-134">Removes that task from the collection.</span></span>  
  
<span data-ttu-id="b7960-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b7960-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
    3.  <span data-ttu-id="b7960-136">Attend de `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="b7960-136">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="b7960-137">Le `firstFinishedTask` variable est une <xref:System.Threading.Tasks.Task%601>où `TReturn` est un entier.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="b7960-137">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="b7960-138">La tâche est déjà terminée, mais vous await pour récupérer la longueur du site Web téléchargé, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7960-138">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="b7960-139">Vous devez exécuter le projet plusieurs fois pour vérifier que les longueurs téléchargés n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="b7960-139">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b7960-140">Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes impliquant un petit nombre de tâches.</span><span class="sxs-lookup"><span data-stu-id="b7960-140">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="b7960-141">Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter.</span><span class="sxs-lookup"><span data-stu-id="b7960-141">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="b7960-142">Pour plus d’informations et d’exemples, consultez [tâches de traitement qu’elles complète](http://go.microsoft.com/fwlink/?LinkId=260810).</span><span class="sxs-lookup"><span data-stu-id="b7960-142">For more information and examples, see [Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="b7960-143">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="b7960-143">Complete Example</span></span>  
 <span data-ttu-id="b7960-144">Le code suivant est le texte complet du fichier MainWindow.xaml.vb pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b7960-144">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="b7960-145">Les astérisques marquent les éléments qui ont été ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b7960-145">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="b7960-146">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="b7960-146">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="b7960-147">Vous pouvez télécharger le projet à partir de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="b7960-147">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7960-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7960-148">See Also</span></span>  
 <span data-ttu-id="b7960-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="b7960-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="b7960-150"> [Réglage de votre Application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="b7960-150"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="b7960-151"> [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="b7960-151"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="b7960-152"> [Exemple Async : Réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="b7960-152"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
