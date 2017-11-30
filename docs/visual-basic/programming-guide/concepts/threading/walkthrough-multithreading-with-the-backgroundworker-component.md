---
title: "Multithreading à l’aide du composant BackgroundWorker (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb0734b4bbf3f8bf5b27305754829f1a9f29f42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="f0a34-102">Procédure pas à pas : Multithreading avec le composant BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0a34-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="f0a34-103">Cette procédure pas à pas montre comment créer une application Windows Forms multithread qui recherche les occurrences d’un mot dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f0a34-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="f0a34-104">Elle présente les points suivants :</span><span class="sxs-lookup"><span data-stu-id="f0a34-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="f0a34-105">Définition d’une classe avec une méthode qui peut être appelée par le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="f0a34-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="f0a34-106">Gestion des événements déclenchés par le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="f0a34-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="f0a34-107">Démarrage d’un composant <xref:System.ComponentModel.BackgroundWorker> pour exécuter une méthode.</span><span class="sxs-lookup"><span data-stu-id="f0a34-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="f0a34-108">Implémentation d’un bouton `Cancel` qui arrête le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="f0a34-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="f0a34-109">Pour créer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0a34-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="f0a34-110">Ouvrez un nouveau projet d’Application Windows Forms Visual Basic et créez un formulaire nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="f0a34-111">Ajoutez deux boutons et quatre zones de texte à `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="f0a34-112">Nommez les objets de la façon indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f0a34-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f0a34-113">Objet</span><span class="sxs-lookup"><span data-stu-id="f0a34-113">Object</span></span>|<span data-ttu-id="f0a34-114">Propriété</span><span class="sxs-lookup"><span data-stu-id="f0a34-114">Property</span></span>|<span data-ttu-id="f0a34-115">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f0a34-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="f0a34-116">Premier bouton</span><span class="sxs-lookup"><span data-stu-id="f0a34-116">First button</span></span>|<span data-ttu-id="f0a34-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-117">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-118">Start, Start</span><span class="sxs-lookup"><span data-stu-id="f0a34-118">Start, Start</span></span>|  
    |<span data-ttu-id="f0a34-119">Deuxième bouton</span><span class="sxs-lookup"><span data-stu-id="f0a34-119">Second button</span></span>|<span data-ttu-id="f0a34-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-120">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-121">Cancel, Cancel</span><span class="sxs-lookup"><span data-stu-id="f0a34-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="f0a34-122">Première zone de texte</span><span class="sxs-lookup"><span data-stu-id="f0a34-122">First text box</span></span>|<span data-ttu-id="f0a34-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-123">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="f0a34-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="f0a34-125">Deuxième zone de texte</span><span class="sxs-lookup"><span data-stu-id="f0a34-125">Second text box</span></span>|<span data-ttu-id="f0a34-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-126">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="f0a34-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="f0a34-128">Troisième zone de texte</span><span class="sxs-lookup"><span data-stu-id="f0a34-128">Third text box</span></span>|<span data-ttu-id="f0a34-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-129">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="f0a34-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="f0a34-131">Quatrième zone de texte</span><span class="sxs-lookup"><span data-stu-id="f0a34-131">Fourth text box</span></span>|<span data-ttu-id="f0a34-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f0a34-132">`Name`, `Text`</span></span>|<span data-ttu-id="f0a34-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="f0a34-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="f0a34-134">Ajoutez une étiquette à côté de chaque zone de texte.</span><span class="sxs-lookup"><span data-stu-id="f0a34-134">Add a label next to each text box.</span></span> <span data-ttu-id="f0a34-135">Définissez la propriété `Text` pour chaque étiquette, comme illustré dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f0a34-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f0a34-136">Objet</span><span class="sxs-lookup"><span data-stu-id="f0a34-136">Object</span></span>|<span data-ttu-id="f0a34-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="f0a34-137">Property</span></span>|<span data-ttu-id="f0a34-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f0a34-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="f0a34-139">Première étiquette</span><span class="sxs-lookup"><span data-stu-id="f0a34-139">First label</span></span>|`Text`|<span data-ttu-id="f0a34-140">Fichier source</span><span class="sxs-lookup"><span data-stu-id="f0a34-140">Source File</span></span>|  
    |<span data-ttu-id="f0a34-141">Deuxième étiquette</span><span class="sxs-lookup"><span data-stu-id="f0a34-141">Second label</span></span>|`Text`|<span data-ttu-id="f0a34-142">Compare String</span><span class="sxs-lookup"><span data-stu-id="f0a34-142">Compare String</span></span>|  
    |<span data-ttu-id="f0a34-143">Troisième étiquette</span><span class="sxs-lookup"><span data-stu-id="f0a34-143">Third label</span></span>|`Text`|<span data-ttu-id="f0a34-144">Matching Words</span><span class="sxs-lookup"><span data-stu-id="f0a34-144">Matching Words</span></span>|  
    |<span data-ttu-id="f0a34-145">Quatrième étiquette</span><span class="sxs-lookup"><span data-stu-id="f0a34-145">Fourth label</span></span>|`Text`|<span data-ttu-id="f0a34-146">Lines Counted</span><span class="sxs-lookup"><span data-stu-id="f0a34-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="f0a34-147">Pour créer un composant BackgroundWorker et s’abonner à ses événements</span><span class="sxs-lookup"><span data-stu-id="f0a34-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="f0a34-148">Ajoutez au formulaire un composant <xref:System.ComponentModel.BackgroundWorker> de la section **Composants** de la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="f0a34-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="f0a34-149">Il apparaît dans la barre d’état des composants du formulaire.</span><span class="sxs-lookup"><span data-stu-id="f0a34-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="f0a34-150">Définissez les propriétés suivantes de l’objet BackgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="f0a34-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="f0a34-151">Propriété</span><span class="sxs-lookup"><span data-stu-id="f0a34-151">Property</span></span>|<span data-ttu-id="f0a34-152">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f0a34-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="f0a34-153">True</span><span class="sxs-lookup"><span data-stu-id="f0a34-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="f0a34-154">True</span><span class="sxs-lookup"><span data-stu-id="f0a34-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="f0a34-155">Pour définir la méthode qui s’exécutera sur un thread distinct</span><span class="sxs-lookup"><span data-stu-id="f0a34-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="f0a34-156">Dans le menu **Projet**, sélectionnez **Ajouter une classe** pour ajouter une classe au projet.</span><span class="sxs-lookup"><span data-stu-id="f0a34-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="f0a34-157">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f0a34-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="f0a34-158">Sélectionnez **Classe** dans la fenêtre de modèles, puis entrez `Words.vb` dans le champ Nom.</span><span class="sxs-lookup"><span data-stu-id="f0a34-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="f0a34-159">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f0a34-159">Click **Add**.</span></span> <span data-ttu-id="f0a34-160">La classe `Words` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f0a34-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="f0a34-161">Ajoutez le code suivant à la classe `Words` :</span><span class="sxs-lookup"><span data-stu-id="f0a34-161">Add the following code to the `Words` class:</span></span>  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="f0a34-162">Pour gérer les événements à partir du thread</span><span class="sxs-lookup"><span data-stu-id="f0a34-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="f0a34-163">Ajoutez les gestionnaires d’événements suivants au formulaire principal :</span><span class="sxs-lookup"><span data-stu-id="f0a34-163">Add the following event handlers to your main form:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="f0a34-164">Pour démarrer et appeler un nouveau thread qui exécute la méthode WordCount</span><span class="sxs-lookup"><span data-stu-id="f0a34-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="f0a34-165">Ajoutez les procédures suivantes à votre programme :</span><span class="sxs-lookup"><span data-stu-id="f0a34-165">Add the following procedures to your program:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="f0a34-166">Appelez la méthode `StartThread` à partir du bouton `Start` sur le formulaire :</span><span class="sxs-lookup"><span data-stu-id="f0a34-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="f0a34-167">Pour implémenter un bouton Cancel qui arrête le thread</span><span class="sxs-lookup"><span data-stu-id="f0a34-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="f0a34-168">Appelez la procédure `StopThread` à partir du gestionnaire d’événements `Click` pour le bouton `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="f0a34-169">Test</span><span class="sxs-lookup"><span data-stu-id="f0a34-169">Testing</span></span>  
 <span data-ttu-id="f0a34-170">Vous pouvez à présent tester l’application afin de vérifier qu’elle fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="f0a34-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="f0a34-171">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="f0a34-171">To test the application</span></span>  
  
1.  <span data-ttu-id="f0a34-172">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="f0a34-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="f0a34-173">Quand le formulaire s’affiche, entrez le chemin du fichier que vous souhaitez tester dans la zone `sourceFile`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="f0a34-174">Par exemple, en supposant que le fichier de test se nomme Test.txt, entrez C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="f0a34-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="f0a34-175">Dans la deuxième zone de texte, entrez un mot ou une expression que l’application va devoir rechercher dans le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f0a34-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="f0a34-176">Cliquez sur le bouton `Start`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-176">Click the `Start` button.</span></span> <span data-ttu-id="f0a34-177">Sur le bouton `LinesCounted`, la valeur affichée devrait commencer immédiatement à être incrémentée.</span><span class="sxs-lookup"><span data-stu-id="f0a34-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="f0a34-178">L’application affiche le message « Finished Counting » (Comptage terminé) une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="f0a34-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="f0a34-179">Pour tester le bouton Cancel</span><span class="sxs-lookup"><span data-stu-id="f0a34-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="f0a34-180">Appuyez sur F5 pour démarrer l’application, puis entrez le nom de fichier et le mot à rechercher comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="f0a34-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="f0a34-181">Vérifiez que le fichier choisi est suffisamment volumineux pour que vous ayez le temps d’annuler la procédure avant qu’elle ne soit terminée.</span><span class="sxs-lookup"><span data-stu-id="f0a34-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="f0a34-182">Cliquez sur le bouton `Start` pour lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="f0a34-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="f0a34-183">Cliquez sur le bouton `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="f0a34-183">Click the `Cancel` button.</span></span> <span data-ttu-id="f0a34-184">L’application devrait cesser le comptage immédiatement.</span><span class="sxs-lookup"><span data-stu-id="f0a34-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f0a34-185">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f0a34-185">Next Steps</span></span>  
 <span data-ttu-id="f0a34-186">Cette application contient une fonctionnalité de base de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f0a34-186">This application contains some basic error handling.</span></span> <span data-ttu-id="f0a34-187">Elle détecte les chaînes de recherche vides.</span><span class="sxs-lookup"><span data-stu-id="f0a34-187">It detects blank search strings.</span></span> <span data-ttu-id="f0a34-188">Vous pouvez rendre ce programme plus robuste en lui permettant de gérer d’autres erreurs, telles que le dépassement du nombre maximal de mots ou de lignes pouvant être comptés.</span><span class="sxs-lookup"><span data-stu-id="f0a34-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a34-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0a34-189">See Also</span></span>  
 [<span data-ttu-id="f0a34-190">Threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0a34-190">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="f0a34-191">Procédure pas à pas : Création d’un composant Simple multithread avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0a34-191">Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic</span></span>](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [<span data-ttu-id="f0a34-192">Guide pratique pour s’abonner et se désabonner d’événements</span><span class="sxs-lookup"><span data-stu-id="f0a34-192">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
