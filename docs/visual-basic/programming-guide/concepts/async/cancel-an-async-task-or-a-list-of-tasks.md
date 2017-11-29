---
title: "Annuler une tâche asynch ou une liste de tâches (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 916577107bd65559aed71dc9bb2921969a117e90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="f13b0-102">Annuler une tâche asynch ou une liste de tâches (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f13b0-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="f13b0-103">Vous pouvez créer un bouton permettant d’annuler une application asynchrone que vous souhaitez interrompre avant la fin de son exécution.</span><span class="sxs-lookup"><span data-stu-id="f13b0-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="f13b0-104">Les exemples de cette rubrique vous montrent comment ajouter un bouton d’annulation à une application qui télécharge du contenu d’un site web ou une liste de sites web.</span><span class="sxs-lookup"><span data-stu-id="f13b0-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="f13b0-105">Les exemples utilisent l’interface utilisateur qui [réglage (Visual Basic) de votre Application Async](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) décrit.</span><span class="sxs-lookup"><span data-stu-id="f13b0-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f13b0-106">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f13b0-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="f13b0-107"><a name="BKMK_CancelaTask"></a> Annuler une tâche</span><span class="sxs-lookup"><span data-stu-id="f13b0-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="f13b0-108">Le premier exemple associe le bouton **Annuler** à une tâche de téléchargement unique.</span><span class="sxs-lookup"><span data-stu-id="f13b0-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="f13b0-109">Si vous appuyez sur le bouton pendant que l’application télécharge du contenu, le téléchargement est annulé.</span><span class="sxs-lookup"><span data-stu-id="f13b0-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="f13b0-110">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f13b0-110">Downloading the Example</span></span>  
 <span data-ttu-id="f13b0-111">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="f13b0-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="f13b0-112">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f13b0-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f13b0-113">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="f13b0-114">Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui conserve l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="f13b0-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="f13b0-115">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelATask**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="f13b0-116">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="f13b0-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="f13b0-117">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="f13b0-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="f13b0-118">Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter les fichiers MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f13b0-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="f13b0-119">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="f13b0-119">Building the Example</span></span>  
 <span data-ttu-id="f13b0-120">Les modifications suivantes ajoutent un bouton **Annuler** à une application de téléchargement d’un site web.</span><span class="sxs-lookup"><span data-stu-id="f13b0-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="f13b0-121">Si vous ne voulez pas télécharger ou générer l’exemple, vous pouvez examiner le produit final dans la section « Exemples complets », à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f13b0-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="f13b0-122">Les astérisques signalent les modifications du code.</span><span class="sxs-lookup"><span data-stu-id="f13b0-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="f13b0-123">Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **StarterCode** comme **Projet de démarrage** au lieu de **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="f13b0-124">Ensuite, ajoutez les modifications suivantes au fichier MainWindow.xaml.vb de ce projet.</span><span class="sxs-lookup"><span data-stu-id="f13b0-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="f13b0-125">Déclarez une variable `CancellationTokenSource`, `cts`, qui se trouve dans la portée de toutes les méthodes qui y accèdent.</span><span class="sxs-lookup"><span data-stu-id="f13b0-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="f13b0-126">Ajoutez le gestionnaire d’événements suivant pour le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="f13b0-127">Le gestionnaire d’événements utilise la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> pour notifier à `cts` la demande d’annulation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f13b0-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="f13b0-128">Effectuez les modifications suivantes dans le gestionnaire d’événements pour le bouton **Démarrer**, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f13b0-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="f13b0-129">Instanciez le `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="f13b0-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="f13b0-130">Dans l’appel à `AccessTheWebAsync`, qui télécharge le contenu d’un site web spécifié, envoyez la propriété <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> de `cts` comme argument.</span><span class="sxs-lookup"><span data-stu-id="f13b0-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="f13b0-131">La propriété `Token` propage le message si l’annulation est demandée.</span><span class="sxs-lookup"><span data-stu-id="f13b0-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="f13b0-132">Ajoutez un bloc catch qui affiche un message si l’utilisateur choisit d’annuler l’opération de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="f13b0-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="f13b0-133">Le code suivant illustre les modifications.</span><span class="sxs-lookup"><span data-stu-id="f13b0-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="f13b0-134">Dans `AccessTheWebAsync`, utilisez la surcharge <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> de la méthode `GetAsync` dans le type <xref:System.Net.Http.HttpClient> pour télécharger le contenu d’un site web.</span><span class="sxs-lookup"><span data-stu-id="f13b0-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="f13b0-135">Passez `ct`, le paramètre <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, comme deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="f13b0-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="f13b0-136">Le jeton transmet le message si l’utilisateur choisit le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="f13b0-137">Le code suivant illustre les modifications dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f13b0-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="f13b0-138">Si vous n’annulez pas le programme, il génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f13b0-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="f13b0-139">Si vous choisissez le bouton **Annuler** quand le programme est encore en train de télécharger du contenu, le programme génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f13b0-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="f13b0-140"><a name="BKMK_CancelaListofTasks"></a> Annuler une liste de tâches</span><span class="sxs-lookup"><span data-stu-id="f13b0-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="f13b0-141">Vous pouvez étendre l’exemple précédent pour annuler de nombreuses tâches à la fois en associant la même instance `CancellationTokenSource` à chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="f13b0-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="f13b0-142">Si vous choisissez le bouton **Annuler**, vous annulez toutes les tâches qui ne sont pas encore terminées.</span><span class="sxs-lookup"><span data-stu-id="f13b0-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="f13b0-143">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f13b0-143">Downloading the Example</span></span>  
 <span data-ttu-id="f13b0-144">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="f13b0-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="f13b0-145">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f13b0-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f13b0-146">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="f13b0-147">Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui conserve l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="f13b0-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="f13b0-148">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAListOfTasks**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="f13b0-149">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="f13b0-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="f13b0-150">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="f13b0-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="f13b0-151">Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter les fichiers MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f13b0-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="f13b0-152">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="f13b0-152">Building the Example</span></span>  
 <span data-ttu-id="f13b0-153">Pour étendre l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelATask** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f13b0-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="f13b0-154">Apportez les modifications suivantes au projet.</span><span class="sxs-lookup"><span data-stu-id="f13b0-154">Add the following changes to that project.</span></span> <span data-ttu-id="f13b0-155">Les astérisques signalent les modifications effectuées dans le programme.</span><span class="sxs-lookup"><span data-stu-id="f13b0-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="f13b0-156">Ajoutez une méthode pour créer une liste des adresses web.</span><span class="sxs-lookup"><span data-stu-id="f13b0-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  <span data-ttu-id="f13b0-157">Appelez la méthode dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f13b0-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="f13b0-158">Ajoutez la boucle suivante dans `AccessTheWebAsync` pour traiter chaque adresse web dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f13b0-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="f13b0-159">Comme `AccessTheWebAsync` affiche les longueurs, la méthode n’a pas besoin de retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="f13b0-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="f13b0-160">Supprimez l’instruction return et changez le type de retour de la méthode de <xref:System.Threading.Tasks.Task> en <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f13b0-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="f13b0-161">Appelez la méthode à partir de `startButton_Click` à l’aide d’une instruction au lieu d’une expression.</span><span class="sxs-lookup"><span data-stu-id="f13b0-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="f13b0-162">Si vous n’annulez pas le programme, il génère le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f13b0-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="f13b0-163">Si vous choisissez le bouton **Annuler** avant la fin des téléchargements, la sortie contient les longueurs des chaînes ayant été téléchargées avant l’annulation.</span><span class="sxs-lookup"><span data-stu-id="f13b0-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <span data-ttu-id="f13b0-164"><a name="BKMK_CompleteExamples"></a> Exemples complets</span><span class="sxs-lookup"><span data-stu-id="f13b0-164"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="f13b0-165">Les sections suivantes contiennent le code correspondant à chacun des exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="f13b0-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="f13b0-166">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f13b0-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="f13b0-167">Vous pouvez télécharger les projets à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="f13b0-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="f13b0-168">Exemple d’annulation d’une tâche</span><span class="sxs-lookup"><span data-stu-id="f13b0-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="f13b0-169">Le code suivant est le fichier MainWindow.xaml.vb complet pour l’exemple qui annule une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="f13b0-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="f13b0-170">Exemple d’annulation d’une liste de tâches</span><span class="sxs-lookup"><span data-stu-id="f13b0-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="f13b0-171">Le code suivant est le fichier MainWindow.xaml.vb complet pour l’exemple qui annule une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="f13b0-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
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
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="f13b0-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f13b0-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="f13b0-173">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f13b0-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="f13b0-174">Ajuster une application Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f13b0-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="f13b0-175">Exemple Async : ajuster une application</span><span class="sxs-lookup"><span data-stu-id="f13b0-175">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
