---
title: "Annuler des tâches Asynch après une période de temps (Visual Basic) | Documents Microsoft"
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
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c2c7c09f9af7c9b7bdcb6411b6db6e2ca4984cb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="6f76c-102">Annuler des tâches Asynch après une période de temps (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f76c-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>
<span data-ttu-id="6f76c-103">Vous pouvez annuler une opération asynchrone après une période de temps à l’aide de la <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName>méthode si vous ne souhaitez pas attendre la fin de l’opération.</xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6f76c-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="6f76c-104">Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas complètes dans la période de temps indiquée par le `CancelAfter` expression.</span><span class="sxs-lookup"><span data-stu-id="6f76c-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="6f76c-105">Cet exemple ajoute le code développé dans [annuler une tâche asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites Web et afficher la longueur du contenu de chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="6f76c-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f76c-106">Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou version ultérieure et le .NET Framework 4.5 ou version ultérieure installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6f76c-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="6f76c-107">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6f76c-107">Downloading the Example</span></span>  
 <span data-ttu-id="6f76c-108">Vous pouvez télécharger le projet Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046) puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="6f76c-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="6f76c-109">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6f76c-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6f76c-110">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="6f76c-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="6f76c-111">Dans le **ouvrir un projet** boîte de dialogue, ouvrez le dossier qui contient l’exemple de code qui vous décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="6f76c-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="6f76c-112">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **CancelAfterTime** de projet, puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="6f76c-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="6f76c-113">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="6f76c-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="6f76c-114">Choisissez les touches Ctrl + F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="6f76c-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="6f76c-115">Exécutez le programme plusieurs fois pour vérifier que la sortie peut afficher la sortie de tous les sites Web, aucun site Web ou des sites web.</span><span class="sxs-lookup"><span data-stu-id="6f76c-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="6f76c-116">Si vous ne souhaitez pas télécharger le projet, vous pouvez consulter le fichier MainWindow.xaml.vb à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6f76c-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="6f76c-117">Création de l’exemple</span><span class="sxs-lookup"><span data-stu-id="6f76c-117">Building the Example</span></span>  
 <span data-ttu-id="6f76c-118">L’exemple de cette rubrique ajoute au projet développé dans [annuler une tâche asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="6f76c-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="6f76c-119">L’exemple utilise la même interface utilisateur, bien que le **Annuler** bouton n’est pas utilisé de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="6f76c-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="6f76c-120">Pour générer l’exemple vous-même, étape par étape, suivez les instructions dans la téléchargement de la section « Exemple », mais choisissez **CancelAListOfTasks** comme le **projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="6f76c-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="6f76c-121">À ce projet, ajoutez les modifications dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6f76c-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="6f76c-122">Pour spécifier une durée maximale avant que les tâches sont marquées comme annulées, ajoutez un appel à `CancelAfter` à `startButton_Click`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6f76c-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="6f76c-123">L’ajout est marqué par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="6f76c-123">The addition is marked with asterisks.</span></span>  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
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
```  
  
 <span data-ttu-id="6f76c-124">Exécutez le programme plusieurs fois pour vérifier que la sortie peut afficher la sortie de tous les sites Web, aucun site Web ou des sites web.</span><span class="sxs-lookup"><span data-stu-id="6f76c-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="6f76c-125">La sortie suivante est un exemple.</span><span class="sxs-lookup"><span data-stu-id="6f76c-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="6f76c-126">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="6f76c-126">Complete Example</span></span>  
 <span data-ttu-id="6f76c-127">Le code suivant est le texte complet du fichier MainWindow.xaml.vb pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="6f76c-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="6f76c-128">Les astérisques marquent les éléments qui ont été ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6f76c-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="6f76c-129">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="6f76c-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="6f76c-130">Vous pouvez télécharger le projet à partir de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="6f76c-130">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
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
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
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
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f76c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f76c-131">See Also</span></span>  
 <span data-ttu-id="6f76c-132">[Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f76c-132">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="6f76c-133"> [Procédure pas à pas : Accès Web en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="6f76c-133"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="6f76c-134"> [Annuler une tâche asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="6f76c-134"> [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span></span>  
<span data-ttu-id="6f76c-135"> [Réglage de votre Application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="6f76c-135"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="6f76c-136"> [Exemple Async : Réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="6f76c-136"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
