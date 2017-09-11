---
title: "Multithreading à l’aide du composant BackgroundWorker (Visual Basic) | Documents Microsoft"
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
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
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
ms.openlocfilehash: 88d0711c8e417ae5c95b0e109504b69882015241
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="57676-102">Procédure pas à pas : Multithreading avec le composant BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57676-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="57676-103">Cette procédure pas à pas montre comment créer une application Windows Forms multithread qui recherche dans un fichier texte les occurrences d’un mot.</span><span class="sxs-lookup"><span data-stu-id="57676-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="57676-104">Il montre :</span><span class="sxs-lookup"><span data-stu-id="57676-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="57676-105">Définition d’une classe avec une méthode qui peut être appelée par le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="57676-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="57676-106">Gestion des événements déclenchés par le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="57676-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="57676-107">Démarrer un <xref:System.ComponentModel.BackgroundWorker>pour exécuter une méthode.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="57676-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="57676-108">Implémentation d’un `Cancel` bouton qui arrête le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="57676-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="57676-109">Pour créer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="57676-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="57676-110">Ouvrez un nouveau projet d’Application Windows Forms Visual Basic et créez un formulaire nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="57676-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="57676-111">Ajoutez deux boutons et quatre zones de texte `Form1`.</span><span class="sxs-lookup"><span data-stu-id="57676-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="57676-112">Nommez les objets comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="57676-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="57676-113">Objet</span><span class="sxs-lookup"><span data-stu-id="57676-113">Object</span></span>|<span data-ttu-id="57676-114">Propriété</span><span class="sxs-lookup"><span data-stu-id="57676-114">Property</span></span>|<span data-ttu-id="57676-115">Paramètre</span><span class="sxs-lookup"><span data-stu-id="57676-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="57676-116">Premier bouton</span><span class="sxs-lookup"><span data-stu-id="57676-116">First button</span></span>|<span data-ttu-id="57676-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-117">`Name`, `Text`</span></span>|<span data-ttu-id="57676-118">Démarrage, démarrer</span><span class="sxs-lookup"><span data-stu-id="57676-118">Start, Start</span></span>|  
    |<span data-ttu-id="57676-119">Deuxième bouton</span><span class="sxs-lookup"><span data-stu-id="57676-119">Second button</span></span>|<span data-ttu-id="57676-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-120">`Name`, `Text`</span></span>|<span data-ttu-id="57676-121">Annuler, annulation</span><span class="sxs-lookup"><span data-stu-id="57676-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="57676-122">Première zone de texte</span><span class="sxs-lookup"><span data-stu-id="57676-122">First text box</span></span>|<span data-ttu-id="57676-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-123">`Name`, `Text`</span></span>|<span data-ttu-id="57676-124">SourceFile, « »</span><span class="sxs-lookup"><span data-stu-id="57676-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="57676-125">Deuxième zone de texte</span><span class="sxs-lookup"><span data-stu-id="57676-125">Second text box</span></span>|<span data-ttu-id="57676-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-126">`Name`, `Text`</span></span>|<span data-ttu-id="57676-127">CompareString, « »</span><span class="sxs-lookup"><span data-stu-id="57676-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="57676-128">Troisième zone de texte</span><span class="sxs-lookup"><span data-stu-id="57676-128">Third text box</span></span>|<span data-ttu-id="57676-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-129">`Name`, `Text`</span></span>|<span data-ttu-id="57676-130">WordsCounted, « 0 »</span><span class="sxs-lookup"><span data-stu-id="57676-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="57676-131">Quatrième zone de texte</span><span class="sxs-lookup"><span data-stu-id="57676-131">Fourth text box</span></span>|<span data-ttu-id="57676-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="57676-132">`Name`, `Text`</span></span>|<span data-ttu-id="57676-133">LinesCounted, « 0 »</span><span class="sxs-lookup"><span data-stu-id="57676-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="57676-134">Ajoutez une étiquette en regard de chaque zone de texte.</span><span class="sxs-lookup"><span data-stu-id="57676-134">Add a label next to each text box.</span></span> <span data-ttu-id="57676-135">Définir le `Text` propriété pour chaque étiquette, comme illustré dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="57676-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="57676-136">Objet</span><span class="sxs-lookup"><span data-stu-id="57676-136">Object</span></span>|<span data-ttu-id="57676-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="57676-137">Property</span></span>|<span data-ttu-id="57676-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="57676-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="57676-139">Première étiquette</span><span class="sxs-lookup"><span data-stu-id="57676-139">First label</span></span>|`Text`|<span data-ttu-id="57676-140">Fichier source</span><span class="sxs-lookup"><span data-stu-id="57676-140">Source File</span></span>|  
    |<span data-ttu-id="57676-141">Deuxième contrôle label</span><span class="sxs-lookup"><span data-stu-id="57676-141">Second label</span></span>|`Text`|<span data-ttu-id="57676-142">Comparer des chaînes</span><span class="sxs-lookup"><span data-stu-id="57676-142">Compare String</span></span>|  
    |<span data-ttu-id="57676-143">Troisième contrôle label</span><span class="sxs-lookup"><span data-stu-id="57676-143">Third label</span></span>|`Text`|<span data-ttu-id="57676-144">Correspondance de mots</span><span class="sxs-lookup"><span data-stu-id="57676-144">Matching Words</span></span>|  
    |<span data-ttu-id="57676-145">Quatrième contrôle label</span><span class="sxs-lookup"><span data-stu-id="57676-145">Fourth label</span></span>|`Text`|<span data-ttu-id="57676-146">Lignes comptées</span><span class="sxs-lookup"><span data-stu-id="57676-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="57676-147">Pour créer un composant BackgroundWorker et s’abonner à ses événements</span><span class="sxs-lookup"><span data-stu-id="57676-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="57676-148">Ajouter un <xref:System.ComponentModel.BackgroundWorker>composant à partir de la **composants** section de la **boîte à outils** au formulaire.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="57676-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="57676-149">Il apparaît dans la barre d’état des composants du formulaire.</span><span class="sxs-lookup"><span data-stu-id="57676-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="57676-150">Définissez les propriétés suivantes de l’objet BackgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="57676-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="57676-151">Propriété</span><span class="sxs-lookup"><span data-stu-id="57676-151">Property</span></span>|<span data-ttu-id="57676-152">Paramètre</span><span class="sxs-lookup"><span data-stu-id="57676-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="57676-153">True</span><span class="sxs-lookup"><span data-stu-id="57676-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="57676-154">True</span><span class="sxs-lookup"><span data-stu-id="57676-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="57676-155">Pour définir la méthode qui s’exécutera sur un thread distinct</span><span class="sxs-lookup"><span data-stu-id="57676-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="57676-156">À partir de la **projet** menu, choisissez **ajouter une classe** pour ajouter une classe au projet.</span><span class="sxs-lookup"><span data-stu-id="57676-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="57676-157">Le **ajouter un nouvel élément** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="57676-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="57676-158">Sélectionnez **classe** à partir de la fenêtre de modèles, puis entrez `Words.vb` dans le champ nom.</span><span class="sxs-lookup"><span data-stu-id="57676-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="57676-159">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="57676-159">Click **Add**.</span></span> <span data-ttu-id="57676-160">La `Words` classe s’affiche.</span><span class="sxs-lookup"><span data-stu-id="57676-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="57676-161">Ajoutez le code suivant à la classe `Words` :</span><span class="sxs-lookup"><span data-stu-id="57676-161">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="57676-162">Pour gérer les événements à partir du thread</span><span class="sxs-lookup"><span data-stu-id="57676-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="57676-163">Ajoutez les gestionnaires d’événements suivant à votre formulaire principal :</span><span class="sxs-lookup"><span data-stu-id="57676-163">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="57676-164">Pour démarrer et appeler un nouveau thread qui exécute la méthode WordCount</span><span class="sxs-lookup"><span data-stu-id="57676-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="57676-165">Ajoutez les procédures suivantes pour votre programme :</span><span class="sxs-lookup"><span data-stu-id="57676-165">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="57676-166">Appelez le `StartThread` méthode à partir de la `Start` bouton sur votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="57676-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="57676-167">Pour implémenter un bouton Cancel qui arrête le thread</span><span class="sxs-lookup"><span data-stu-id="57676-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="57676-168">Appelez le `StopThread` procédure à partir de la `Click` Gestionnaire d’événements pour le `Cancel` bouton.</span><span class="sxs-lookup"><span data-stu-id="57676-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="57676-169">Test</span><span class="sxs-lookup"><span data-stu-id="57676-169">Testing</span></span>  
 <span data-ttu-id="57676-170">Vous pouvez maintenant tester l’application pour vérifier qu’il fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="57676-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="57676-171">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="57676-171">To test the application</span></span>  
  
1.  <span data-ttu-id="57676-172">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="57676-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="57676-173">Lorsque le formulaire s’affiche, entrez le chemin d’accès du fichier que vous souhaitez tester dans la `sourceFile` boîte.</span><span class="sxs-lookup"><span data-stu-id="57676-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="57676-174">Par exemple, en supposant que votre fichier de test se nomme Test.txt, entrez C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="57676-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="57676-175">Dans la deuxième zone de texte, entrez un mot ou expression à rechercher dans le fichier texte de l’application.</span><span class="sxs-lookup"><span data-stu-id="57676-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="57676-176">Cliquez sur le bouton `Start`.</span><span class="sxs-lookup"><span data-stu-id="57676-176">Click the `Start` button.</span></span> <span data-ttu-id="57676-177">Le `LinesCounted` bouton doit commencer immédiatement.</span><span class="sxs-lookup"><span data-stu-id="57676-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="57676-178">L’application affiche le message « Finished Counting » lorsqu’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="57676-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="57676-179">Pour tester le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="57676-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="57676-180">Appuyez sur F5 pour démarrer l’application, entrez le mot fichier recherche et le nom comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="57676-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="57676-181">Assurez-vous que le fichier choisi est suffisamment volumineux pour que vous ayez le temps d’annuler la procédure avant la fin.</span><span class="sxs-lookup"><span data-stu-id="57676-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="57676-182">Cliquez sur le `Start` bouton pour démarrer l’application.</span><span class="sxs-lookup"><span data-stu-id="57676-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="57676-183">Cliquez sur le bouton `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="57676-183">Click the `Cancel` button.</span></span> <span data-ttu-id="57676-184">L’application devrait cesser le décompte immédiatement.</span><span class="sxs-lookup"><span data-stu-id="57676-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="57676-185">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="57676-185">Next Steps</span></span>  
 <span data-ttu-id="57676-186">Cette application contient une gestion des erreurs de base.</span><span class="sxs-lookup"><span data-stu-id="57676-186">This application contains some basic error handling.</span></span> <span data-ttu-id="57676-187">Il détecte les chaînes de recherche vides.</span><span class="sxs-lookup"><span data-stu-id="57676-187">It detects blank search strings.</span></span> <span data-ttu-id="57676-188">Vous pouvez rendre ce programme plus robuste en gérant les autres erreurs, telles que le dépassement du nombre maximal de mots ou de lignes qui peuvent être comptées.</span><span class="sxs-lookup"><span data-stu-id="57676-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57676-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57676-189">See Also</span></span>  
 <span data-ttu-id="57676-190">[Threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="57676-190">[Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="57676-191"> [Procédure pas à pas : Création d’un composant Simple multithread avec Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span><span class="sxs-lookup"><span data-stu-id="57676-191"> [Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span></span>  
<span data-ttu-id="57676-192"> [Comment : s’abonner et annuler l’abonnement à des événements](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="57676-192"> [How to: Subscribe to and Unsubscribe from Events](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span></span>
