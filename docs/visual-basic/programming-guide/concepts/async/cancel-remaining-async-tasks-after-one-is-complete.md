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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1b70822edd972ac33614ab49faad6ff50b0e80b7
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="1e68e-102">Annuler les tâches Asynch restantes après une est terminée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e68e-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="1e68e-103">À l’aide de la <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>méthode avec un <xref:System.Threading.CancellationToken>, vous pouvez annuler toutes les tâches restantes lorsqu’une tâche est terminée.</xref:System.Threading.CancellationToken> </xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1e68e-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="1e68e-104">Le `WhenAny` méthode prend un argument qui est une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="1e68e-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="1e68e-105">La méthode démarre toutes les tâches et renvoie une seule tâche.</span><span class="sxs-lookup"><span data-stu-id="1e68e-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="1e68e-106">La tâche est terminée lorsque toutes les tâches dans la collection sont terminée.</span><span class="sxs-lookup"><span data-stu-id="1e68e-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="1e68e-107">Cet exemple montre comment utiliser un jeton d’annulation avec `WhenAny` à maintenir la première tâche à la fin de la collection de tâches et d’annuler les tâches restantes.</span><span class="sxs-lookup"><span data-stu-id="1e68e-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="1e68e-108">Chaque tâche télécharge le contenu d’un site Web.</span><span class="sxs-lookup"><span data-stu-id="1e68e-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="1e68e-109">L’exemple affiche la longueur du contenu de la fin du premier téléchargement et annule les autres téléchargements.</span><span class="sxs-lookup"><span data-stu-id="1e68e-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e68e-110">Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1e68e-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="1e68e-111">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="1e68e-111">Downloading the Example</span></span>  
 <span data-ttu-id="1e68e-112">Vous pouvez télécharger le projet Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046) puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="1e68e-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1e68e-113">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e68e-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1e68e-114">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="1e68e-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1e68e-115">Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui contient l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="1e68e-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="1e68e-116">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **CancelAfterOneTask** de projet, puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="1e68e-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1e68e-117">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="1e68e-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1e68e-118">Choisissez les touches Ctrl + F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="1e68e-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="1e68e-119">Exécutez le programme plusieurs fois pour vérifier que les téléchargements différents termine d’abord.</span><span class="sxs-lookup"><span data-stu-id="1e68e-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="1e68e-120">Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1e68e-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="1e68e-121">Création de l’exemple</span><span class="sxs-lookup"><span data-stu-id="1e68e-121">Building the Example</span></span>  
 <span data-ttu-id="1e68e-122">L’exemple de cette rubrique ajoute au projet développé dans [annuler une tâche asynch ou une liste de tâches](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="1e68e-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="1e68e-123">L’exemple utilise la même interface utilisateur, bien que le **Annuler** bouton n’est pas utilisé de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="1e68e-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="1e68e-124">Pour générer l’exemple vous-même, étape par étape, suivez les instructions dans la téléchargement de la section « Exemple », mais choisissez **CancelAListOfTasks** comme le **projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="1e68e-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="1e68e-125">À ce projet, ajoutez les modifications dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1e68e-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="1e68e-126">Dans le fichier MainWindow.xaml.vb de la **CancelAListOfTasks** de projet, démarrez la transition en déplaçant les étapes de traitement pour chaque site Web à partir de la boucle de `AccessTheWebAsync` à la méthode asynchrone suivant.</span><span class="sxs-lookup"><span data-stu-id="1e68e-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="1e68e-127">Dans `AccessTheWebAsync`, cet exemple utilise une requête, le <xref:System.Linq.Enumerable.ToArray%2A>(méthode) et le `WhenAny` pour créer et démarrer un tableau de tâches.</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="1e68e-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="1e68e-128">L’application de `WhenAny` dans le tableau renvoie une seule tâche qui, pendant l’attente, prend la valeur de la première tâche pour atteindre la fin du tableau de tâches.</span><span class="sxs-lookup"><span data-stu-id="1e68e-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="1e68e-129">Apportez les modifications suivantes dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="1e68e-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="1e68e-130">Les astérisques marquer les modifications dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="1e68e-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="1e68e-131">Commentez ou supprimez la boucle.</span><span class="sxs-lookup"><span data-stu-id="1e68e-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="1e68e-132">Créer une requête qui, lorsqu’elle est exécutée, produit une collection de tâches génériques.</span><span class="sxs-lookup"><span data-stu-id="1e68e-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="1e68e-133">Chaque appel à `ProcessURLAsync` renvoie un <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="1e68e-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="1e68e-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1e68e-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
3.  <span data-ttu-id="1e68e-135">Appelez `ToArray` pour exécuter la requête et de démarrer les tâches.</span><span class="sxs-lookup"><span data-stu-id="1e68e-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="1e68e-136">L’application de la `WhenAny` méthode à l’étape suivante serait exécuter la requête et lancer les tâches sans utiliser `ToArray`, mais les autres méthodes ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="1e68e-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="1e68e-137">La plus sûre consiste à forcer l’exécution de la requête explicitement.</span><span class="sxs-lookup"><span data-stu-id="1e68e-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
<span data-ttu-id="1e68e-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1e68e-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="1e68e-139">Appeler `WhenAny` sur la collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="1e68e-139">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="1e68e-140">`WhenAny`Retourne un `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="1e68e-140">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="1e68e-141">Autrement dit, `WhenAny` retourne une tâche qui évalue à un seul `Task(Of Integer)` ou `Task<int>` lorsqu’il est attendu.</span><span class="sxs-lookup"><span data-stu-id="1e68e-141">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="1e68e-142">Cette tâche unique est la première tâche dans la collection se termine.</span><span class="sxs-lookup"><span data-stu-id="1e68e-142">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="1e68e-143">La tâche terminé est affectée à `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="1e68e-143">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="1e68e-144">Le type de `firstFinishedTask` est <xref:System.Threading.Tasks.Task%601>où `TResult` est un entier, car c’est le type de retour de `ProcessURLAsync`.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="1e68e-144">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="1e68e-145">Dans cet exemple, vous êtes uniquement intéressé par la tâche se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="1e68e-145">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="1e68e-146">Par conséquent, utilisez <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>pour annuler les tâches restantes.</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1e68e-146">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="1e68e-147">Enfin, await `firstFinishedTask` pour extraire la longueur du contenu téléchargé.</span><span class="sxs-lookup"><span data-stu-id="1e68e-147">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="1e68e-148">Exécutez le programme plusieurs fois pour vérifier que les téléchargements différents termine d’abord.</span><span class="sxs-lookup"><span data-stu-id="1e68e-148">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="1e68e-149">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="1e68e-149">Complete Example</span></span>  
 <span data-ttu-id="1e68e-150">Le code suivant est le fichier MainWindow.xaml.vb ou MainWindow.xaml.cs complet pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="1e68e-150">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="1e68e-151">Les astérisques marquent les éléments qui ont été ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="1e68e-151">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="1e68e-152">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="1e68e-152">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1e68e-153">Vous pouvez télécharger le projet à partir de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="1e68e-153">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e68e-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e68e-154">See Also</span></span>  
 <span data-ttu-id="1e68e-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="1e68e-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="1e68e-156"> [Réglage de votre Application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="1e68e-156"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="1e68e-157"> [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="1e68e-157"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="1e68e-158"> [Exemple Async : Réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="1e68e-158"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
