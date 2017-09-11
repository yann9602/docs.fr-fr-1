---
title: "Contrôler le flux dans les programmes Async (Visual Basic) | Documents Microsoft"
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
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
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
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="ac479-102">Flux de contrôle dans les programmes Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac479-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="ac479-103">Vous pouvez écrire et maintenir plus facilement des programmes asynchrones à l’aide de la `Async` et `Await` mots clés.</span><span class="sxs-lookup"><span data-stu-id="ac479-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="ac479-104">Toutefois, les résultats peuvent vous surprendre si vous ne comprenez pas le fonctionnement de votre programme.</span><span class="sxs-lookup"><span data-stu-id="ac479-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="ac479-105">Traces de cette rubrique le flux de contrôle via un programme asynchrone simple pour vous montrer lorsque le contrôle passe à partir d’une méthode à un autre et les informations est transféré à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="ac479-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac479-106">Les mots clés `Async` et `Await` ont été introduites dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ac479-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="ac479-107">En général, vous marquez les méthodes qui contiennent du code asynchrone avec le [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="ac479-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="ac479-108">Dans une méthode qui est marquée avec un modificateur async, vous pouvez utiliser un [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) (opérateur) pour spécifier où la méthode Pause pour attendre un processus asynchrone appelé terminer.</span><span class="sxs-lookup"><span data-stu-id="ac479-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="ac479-109">Pour plus d’informations, consultez [programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac479-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="ac479-110">L’exemple suivant utilise les méthodes async pour télécharger le contenu d’un site Web spécifié sous forme de chaîne et afficher la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ac479-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="ac479-111">L’exemple contient deux méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ac479-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="ac479-112">`startButton_Click`, qui appelle la méthode `AccessTheWebAsync` et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="ac479-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="ac479-113">`AccessTheWebAsync`, qui télécharge le contenu d’un site Web sous forme de chaîne et retourne la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ac479-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="ac479-114">`AccessTheWebAsync`utilise asynchrone <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>permet de télécharger le contenu.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="ac479-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="ac479-115">Numérotées affichage lignes apparaissent aux points stratégiques tout au long du programme pour vous aider à comprendre comment le programme s’exécute et d’expliquer ce qui se produit à chaque point est marqué.</span><span class="sxs-lookup"><span data-stu-id="ac479-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="ac479-116">Les lignes d’affichage sont étiquetés « Un » à « 6. »</span><span class="sxs-lookup"><span data-stu-id="ac479-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="ac479-117">Les étiquettes représentent l’ordre dans lequel le programme atteint ces lignes de code.</span><span class="sxs-lookup"><span data-stu-id="ac479-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="ac479-118">Le code suivant montre un plan du programme.</span><span class="sxs-lookup"><span data-stu-id="ac479-118">The following code shows an outline of the program.</span></span>  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
    End Sub  
  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' TWO  
        Dim client As HttpClient = New HttpClient()   
        Dim getStringTask As Task(Of String) =   
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
  
```  
  
 <span data-ttu-id="ac479-119">Chaque emplacement étiqueté, « Un » à « 6, » affiche des informations sur l’état actuel du programme.</span><span class="sxs-lookup"><span data-stu-id="ac479-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="ac479-120">La sortie suivante est produite.</span><span class="sxs-lookup"><span data-stu-id="ac479-120">The following output is produced.</span></span>  
  
```  
  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a><span data-ttu-id="ac479-121">Configurer le programme</span><span class="sxs-lookup"><span data-stu-id="ac479-121">Set Up the Program</span></span>  
 <span data-ttu-id="ac479-122">Vous pouvez télécharger le code qui utilise cette rubrique à partir de MSDN, ou vous pouvez la créer vous-même.</span><span class="sxs-lookup"><span data-stu-id="ac479-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac479-123">Pour exécuter l’exemple, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ac479-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="ac479-124">Téléchargez le programme</span><span class="sxs-lookup"><span data-stu-id="ac479-124">Download the Program</span></span>  
 <span data-ttu-id="ac479-125">Vous pouvez télécharger l’application de cette rubrique à partir de [exemple Async : flux de contrôle dans les programmes Async](http://go.microsoft.com/fwlink/?LinkId=255285).</span><span class="sxs-lookup"><span data-stu-id="ac479-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="ac479-126">Les étapes suivantes, ouvrent et exécutez le programme.</span><span class="sxs-lookup"><span data-stu-id="ac479-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="ac479-127">Décompressez le fichier téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac479-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ac479-128">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="ac479-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="ac479-129">Accédez au dossier qui contient le code exemple décompressé, ouvrez le fichier solution (.sln), puis appuyez sur F5 pour générer et exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="ac479-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="ac479-130">Générer le programme vous-même</span><span class="sxs-lookup"><span data-stu-id="ac479-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="ac479-131">Le projet Windows Presentation Foundation (WPF) suivant contient l’exemple de code de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ac479-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="ac479-132">Pour exécuter le projet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac479-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="ac479-133">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac479-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ac479-134">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="ac479-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="ac479-135">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ac479-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ac479-136">Dans le **modèles installés** volet, choisissez **Visual Basic**, puis choisissez **Application WPF** dans la liste des types de projet.</span><span class="sxs-lookup"><span data-stu-id="ac479-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="ac479-137">Entrez `AsyncTracer` comme nom du projet, puis choisissez le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="ac479-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="ac479-138">Le nouveau projet s’affiche dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="ac479-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="ac479-139">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="ac479-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="ac479-140">Si l’onglet n’est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans **l’Explorateur de solutions**, puis choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="ac479-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="ac479-141">Dans le **XAML** du MainWindow.xaml, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ac479-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"  
        Title="Control Flow Trace" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     <span data-ttu-id="ac479-142">Une fenêtre simple contenant une zone de texte et un bouton s’affiche dans le **conception** vue de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ac479-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="ac479-143">Ajoutez une référence pour <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="ac479-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="ac479-144">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.vb, puis choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="ac479-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="ac479-145">Dans MainWindow.xaml.vb, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ac479-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add an Imports statement and a reference for System.Net.Http.  
    Imports System.Net.Http  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
            ' The display lines in the example lead you through the control shifts.  
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &  
                "           Calling AccessTheWebAsync." & vbCrLf  
  
            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is started." & vbCrLf &  
                "           About to await getLengthTask -- no caller to return to." & vbCrLf  
  
            Dim contentLength As Integer = Await getLengthTask  
  
            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is finished." & vbCrLf &  
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &  
                "           About to display contentLength and exit." & vbCrLf  
  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
        End Sub  
  
        Async Function AccessTheWebAsync() As Task(Of Integer)  
  
            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."  
  
            ' Declare an HttpClient object.  
            Dim client As HttpClient = New HttpClient()  
  
            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf  
  
            ' GetStringAsync returns a Task(Of String).   
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &  
                "           Task getStringTask is started."  
  
            ' AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
            ResultsTextBox.Text &=  
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf  
  
            ' Retrieve the website contents when task is complete.  
            Dim urlContents As String = Await getStringTask  
  
            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &  
                vbCrLf & "           Task getStringTask is complete." &  
                vbCrLf & "           Processing the return statement." &  
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf  
  
            Return urlContents.Length  
        End Function  
  
    End Class  
    ```  
  
10. <span data-ttu-id="ac479-146">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="ac479-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ac479-147">La sortie suivante doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="ac479-147">The following output should appear.</span></span>  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a><span data-ttu-id="ac479-148">Le programme de trace</span><span class="sxs-lookup"><span data-stu-id="ac479-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="ac479-149">Étapes UNE et DEUX</span><span class="sxs-lookup"><span data-stu-id="ac479-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="ac479-150">Les deux premières afficher des lignes de suivre le chemin d’accès en tant que `startButton_Click` appelle `AccessTheWebAsync`, et `AccessTheWebAsync` appelle la <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient> de asynchrone</span><span class="sxs-lookup"><span data-stu-id="ac479-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="ac479-151">L’image suivante présente les appels de méthode en méthode.</span><span class="sxs-lookup"><span data-stu-id="ac479-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="ac479-152">![Étapes un et deux](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="ac479-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="ac479-153">Le type de retour de `AccessTheWebAsync` et `client.GetStringAsync` est <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="ac479-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ac479-154">Pour `AccessTheWebAsync`, TResult est un entier.</span><span class="sxs-lookup"><span data-stu-id="ac479-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="ac479-155">Pour `GetStringAsync`, TResult est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ac479-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="ac479-156">Pour plus d’informations sur les types de retour de méthode asynchrone, consultez [les Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ac479-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="ac479-157">Une méthode async retournant des tâches renvoie une instance de tâche lorsque le contrôle passe à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ac479-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="ac479-158">Le contrôle retourne d’une méthode async à son appelant soit lorsque un `Await` opérateur est rencontrée dans la méthode appelée ou lorsque la méthode appelée se termine.</span><span class="sxs-lookup"><span data-stu-id="ac479-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="ac479-159">Les lignes d’affichage portant le nom « Trois » à « 6 » de cette partie du processus de suivi.</span><span class="sxs-lookup"><span data-stu-id="ac479-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="ac479-160">Étape TROIS</span><span class="sxs-lookup"><span data-stu-id="ac479-160">Step THREE</span></span>  
 <span data-ttu-id="ac479-161">Dans `AccessTheWebAsync`, la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>est appelée pour télécharger le contenu de la page Web cible.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="ac479-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="ac479-162">Le contrôle retourne de `client.GetStringAsync` à `AccessTheWebAsync` lorsque `client.GetStringAsync` renvoie.</span><span class="sxs-lookup"><span data-stu-id="ac479-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="ac479-163">Le `client.GetStringAsync` méthode retourne une tâche de la chaîne est assignée à la `getStringTask` variable `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ac479-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ac479-164">La ligne suivante dans l’exemple de programme illustre l’appel à `client.GetStringAsync` et l’affectation.</span><span class="sxs-lookup"><span data-stu-id="ac479-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
<span data-ttu-id="ac479-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-166">Vous pouvez considérer la tâche en tant qu’une promesse par `client.GetStringAsync` pour produire une chaîne réelle par la suite.</span><span class="sxs-lookup"><span data-stu-id="ac479-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="ac479-167">En attendant, si `AccessTheWebAsync` a du travail à faire qui ne dépend de la chaîne de promis `client.GetStringAsync`, que le travail peut continuer pendant que `client.GetStringAsync` attend.</span><span class="sxs-lookup"><span data-stu-id="ac479-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="ac479-168">Dans l’exemple, les lignes suivantes de sortie, qui sont étiquetés « Trois », représentent l’opportunité d’effectuer un travail indépendant</span><span class="sxs-lookup"><span data-stu-id="ac479-168">In the example, the following lines of output, which are labeled "THREE,” represent the opportunity to do independent work</span></span>  
  
<span data-ttu-id="ac479-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-170">L’instruction suivante interrompt la progression dans `AccessTheWebAsync` lorsque `getStringTask` est attendue.</span><span class="sxs-lookup"><span data-stu-id="ac479-170">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
<span data-ttu-id="ac479-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-172">L’illustration suivante montre le flux de contrôle à partir de `client.GetStringAsync` pour l’assignation à `getStringTask` et de la création de `getStringTask` à l’application d’un opérateur Await.</span><span class="sxs-lookup"><span data-stu-id="ac479-172">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="ac479-173">![Étape&3;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-3")</span><span class="sxs-lookup"><span data-stu-id="ac479-173">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="ac479-174">L’expression await suspend `AccessTheWebAsync` jusqu'à ce que `client.GetStringAsync` retourne.</span><span class="sxs-lookup"><span data-stu-id="ac479-174">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="ac479-175">Entre-temps, le contrôle retourne à l’appelant de `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ac479-175">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac479-176">En règle générale, vous attendez immédiatement l’appel à une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ac479-176">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="ac479-177">Par exemple, l’assignation suivante pourrait remplacer le code précédent qui crée et puis attend `getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="ac479-177">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="ac479-178">Dans cette rubrique, l’opérateur await est appliqué ultérieurement pour prendre en compte les lignes de sortie qui marquent le flux de contrôle via le programme.</span><span class="sxs-lookup"><span data-stu-id="ac479-178">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="ac479-179">Étape QUATRE</span><span class="sxs-lookup"><span data-stu-id="ac479-179">Step FOUR</span></span>  
 <span data-ttu-id="ac479-180">Type de retour le déclaré `AccessTheWebAsync` est `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="ac479-180">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="ac479-181">Par conséquent, lorsque `AccessTheWebAsync` est suspendue, elle retourne une tâche d’entier `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ac479-181">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="ac479-182">Vous devez comprendre que la tâche retournée n’est pas `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="ac479-182">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="ac479-183">La tâche retournée est une tâche d’entier qui représente ce qui reste à faire dans la méthode suspendue, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ac479-183">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="ac479-184">La tâche est une promesse de `AccessTheWebAsync` pour produire un entier lorsque la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="ac479-184">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="ac479-185">L’instruction suivante assigne cette tâche à la `getLengthTask` variable.</span><span class="sxs-lookup"><span data-stu-id="ac479-185">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
<span data-ttu-id="ac479-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-187">Comme dans `AccessTheWebAsync`, `startButton_Click` peut poursuivre une tâche qui ne dépende pas des résultats de la tâche asynchrone (`getLengthTask`) jusqu'à ce que la tâche est attendue.</span><span class="sxs-lookup"><span data-stu-id="ac479-187">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="ac479-188">Les lignes de sortie suivantes représentent ce travail.</span><span class="sxs-lookup"><span data-stu-id="ac479-188">The following output lines represent that work.</span></span>  
  
<span data-ttu-id="ac479-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-190">Progresser dans `startButton_Click` est suspendue lorsque `getLengthTask` est attendue.</span><span class="sxs-lookup"><span data-stu-id="ac479-190">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="ac479-191">L’instruction d’assignation suivante interrompt `startButton_Click` jusqu'à ce que `AccessTheWebAsync` est terminée.</span><span class="sxs-lookup"><span data-stu-id="ac479-191">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
<span data-ttu-id="ac479-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-193">Dans l’illustration suivante, les flèches indiquent le flux de contrôle de l’expression await dans `AccessTheWebAsync` à l’affectation d’une valeur à `getLengthTask`, suivi par le traitement normal de `startButton_Click` jusqu'à ce que `getLengthTask` est attendue.</span><span class="sxs-lookup"><span data-stu-id="ac479-193">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="ac479-194">![Étape&4;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-quatre")</span><span class="sxs-lookup"><span data-stu-id="ac479-194">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="ac479-195">Étape CINQ</span><span class="sxs-lookup"><span data-stu-id="ac479-195">Step FIVE</span></span>  
 <span data-ttu-id="ac479-196">Lors de la `client.GetStringAsync` signale qu’elle est terminée, le traitement de `AccessTheWebAsync` est libéré de la suspension et pouvez passer à l’instruction await.</span><span class="sxs-lookup"><span data-stu-id="ac479-196">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="ac479-197">Les lignes de sortie suivantes représentent la reprise du traitement.</span><span class="sxs-lookup"><span data-stu-id="ac479-197">The following lines of output represent the resumption of processing.</span></span>  
  
<span data-ttu-id="ac479-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-199">L’opérande de l’instruction return, `urlContents.Length`, est stocké dans la tâche qui `AccessTheWebAsync` retourne.</span><span class="sxs-lookup"><span data-stu-id="ac479-199">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="ac479-200">L’expression await récupère cette valeur à partir de `getLengthTask` dans `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ac479-200">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="ac479-201">L’illustration suivante montre le transfert du contrôle après `client.GetStringAsync` (et `getStringTask`) sont terminées.</span><span class="sxs-lookup"><span data-stu-id="ac479-201">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="ac479-202">![Étape&5;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-cinq")</span><span class="sxs-lookup"><span data-stu-id="ac479-202">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="ac479-203">`AccessTheWebAsync`s’exécute jusqu'à achèvement et le contrôle retourne à `startButton_Click`, qui est en attente de l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="ac479-203">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="ac479-204">Étape SIX</span><span class="sxs-lookup"><span data-stu-id="ac479-204">Step SIX</span></span>  
 <span data-ttu-id="ac479-205">Lors de la `AccessTheWebAsync` signale qu’il est terminé, le traitement peut continuer après l’instruction await dans `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="ac479-205">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="ac479-206">En fait, le programme n’a plus rien à faire.</span><span class="sxs-lookup"><span data-stu-id="ac479-206">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="ac479-207">Les lignes de sortie suivantes représentent la reprise du traitement `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="ac479-207">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
<span data-ttu-id="ac479-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-209">L’extrait de l’expression await `getLengthTask` la valeur entière qui est l’opérande de l’instruction return dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ac479-209">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ac479-210">L’instruction suivante assigne la valeur à la `contentLength` variable.</span><span class="sxs-lookup"><span data-stu-id="ac479-210">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
<span data-ttu-id="ac479-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ac479-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ac479-212">L’illustration suivante montre le retour du contrôle à partir de `AccessTheWebAsync` à `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ac479-212">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="ac479-213">![Étape&6;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="ac479-213">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac479-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac479-214">See Also</span></span>  
 <span data-ttu-id="ac479-215">[Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac479-215">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="ac479-216"> [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="ac479-216"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="ac479-217"> [Procédure pas à pas : Accès Web en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="ac479-217"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="ac479-218"> [Exemple Async : Contrôle de flux dans les programmes Async (c# et Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span><span class="sxs-lookup"><span data-stu-id="ac479-218"> [Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span></span>
