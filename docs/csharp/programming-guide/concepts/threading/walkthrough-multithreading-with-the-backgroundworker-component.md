---
title: "Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="b2b0f-102">Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="b2b0f-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="b2b0f-103">Cette procédure pas à pas montre comment créer une application Windows Forms multithread qui recherche les occurrences d’un mot dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="b2b0f-104">Elle présente les points suivants :</span><span class="sxs-lookup"><span data-stu-id="b2b0f-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="b2b0f-105">Définition d’une classe avec une méthode qui peut être appelée par le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="b2b0f-106">Gestion des événements déclenchés par le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="b2b0f-107">Démarrage d’un composant <xref:System.ComponentModel.BackgroundWorker> pour exécuter une méthode.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="b2b0f-108">Implémentation d’un bouton `Cancel` qui arrête le composant <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="b2b0f-109">Pour créer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="b2b0f-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="b2b0f-110">Ouvrez un nouveau projet d’application Windows Forms C#, puis créez un formulaire nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="b2b0f-111">Ajoutez deux boutons et quatre zones de texte à `Form1`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="b2b0f-112">Nommez les objets de la façon indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b2b0f-113">Objet</span><span class="sxs-lookup"><span data-stu-id="b2b0f-113">Object</span></span>|<span data-ttu-id="b2b0f-114">Propriété</span><span class="sxs-lookup"><span data-stu-id="b2b0f-114">Property</span></span>|<span data-ttu-id="b2b0f-115">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b2b0f-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="b2b0f-116">Premier bouton</span><span class="sxs-lookup"><span data-stu-id="b2b0f-116">First button</span></span>|<span data-ttu-id="b2b0f-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-117">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-118">Start, Start</span><span class="sxs-lookup"><span data-stu-id="b2b0f-118">Start, Start</span></span>|  
    |<span data-ttu-id="b2b0f-119">Deuxième bouton</span><span class="sxs-lookup"><span data-stu-id="b2b0f-119">Second button</span></span>|<span data-ttu-id="b2b0f-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-120">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-121">Cancel, Cancel</span><span class="sxs-lookup"><span data-stu-id="b2b0f-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="b2b0f-122">Première zone de texte</span><span class="sxs-lookup"><span data-stu-id="b2b0f-122">First text box</span></span>|<span data-ttu-id="b2b0f-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-123">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="b2b0f-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="b2b0f-125">Deuxième zone de texte</span><span class="sxs-lookup"><span data-stu-id="b2b0f-125">Second text box</span></span>|<span data-ttu-id="b2b0f-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-126">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="b2b0f-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="b2b0f-128">Troisième zone de texte</span><span class="sxs-lookup"><span data-stu-id="b2b0f-128">Third text box</span></span>|<span data-ttu-id="b2b0f-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-129">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="b2b0f-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="b2b0f-131">Quatrième zone de texte</span><span class="sxs-lookup"><span data-stu-id="b2b0f-131">Fourth text box</span></span>|<span data-ttu-id="b2b0f-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b2b0f-132">`Name`, `Text`</span></span>|<span data-ttu-id="b2b0f-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="b2b0f-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="b2b0f-134">Ajoutez une étiquette à côté de chaque zone de texte.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-134">Add a label next to each text box.</span></span> <span data-ttu-id="b2b0f-135">Définissez la propriété `Text` pour chaque étiquette, comme illustré dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b2b0f-136">Objet</span><span class="sxs-lookup"><span data-stu-id="b2b0f-136">Object</span></span>|<span data-ttu-id="b2b0f-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="b2b0f-137">Property</span></span>|<span data-ttu-id="b2b0f-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b2b0f-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="b2b0f-139">Première étiquette</span><span class="sxs-lookup"><span data-stu-id="b2b0f-139">First label</span></span>|`Text`|<span data-ttu-id="b2b0f-140">Fichier source</span><span class="sxs-lookup"><span data-stu-id="b2b0f-140">Source File</span></span>|  
    |<span data-ttu-id="b2b0f-141">Deuxième étiquette</span><span class="sxs-lookup"><span data-stu-id="b2b0f-141">Second label</span></span>|`Text`|<span data-ttu-id="b2b0f-142">Compare String</span><span class="sxs-lookup"><span data-stu-id="b2b0f-142">Compare String</span></span>|  
    |<span data-ttu-id="b2b0f-143">Troisième étiquette</span><span class="sxs-lookup"><span data-stu-id="b2b0f-143">Third label</span></span>|`Text`|<span data-ttu-id="b2b0f-144">Matching Words</span><span class="sxs-lookup"><span data-stu-id="b2b0f-144">Matching Words</span></span>|  
    |<span data-ttu-id="b2b0f-145">Quatrième étiquette</span><span class="sxs-lookup"><span data-stu-id="b2b0f-145">Fourth label</span></span>|`Text`|<span data-ttu-id="b2b0f-146">Lines Counted</span><span class="sxs-lookup"><span data-stu-id="b2b0f-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="b2b0f-147">Pour créer un composant BackgroundWorker et s’abonner à ses événements</span><span class="sxs-lookup"><span data-stu-id="b2b0f-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="b2b0f-148">Ajoutez au formulaire un composant <xref:System.ComponentModel.BackgroundWorker> de la section **Composants** de la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="b2b0f-149">Il apparaît dans la barre d’état des composants du formulaire.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="b2b0f-150">Définissez les propriétés suivantes de l’objet backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="b2b0f-151">Propriété</span><span class="sxs-lookup"><span data-stu-id="b2b0f-151">Property</span></span>|<span data-ttu-id="b2b0f-152">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b2b0f-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="b2b0f-153">True</span><span class="sxs-lookup"><span data-stu-id="b2b0f-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="b2b0f-154">True</span><span class="sxs-lookup"><span data-stu-id="b2b0f-154">True</span></span>|  
  
3.  <span data-ttu-id="b2b0f-155">Abonnez-vous aux événements de l’objet backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="b2b0f-156">En haut de la fenêtre **Propriétés**, cliquez sur l’icône **Événements**.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="b2b0f-157">Double-cliquez sur l’événement `RunWorkerCompleted` pour créer une méthode de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="b2b0f-158">Effectuez la même opération pour les événements `ProgressChanged` et `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="b2b0f-159">Pour définir la méthode qui s’exécutera sur un thread distinct</span><span class="sxs-lookup"><span data-stu-id="b2b0f-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="b2b0f-160">Dans le menu **Projet**, sélectionnez **Ajouter une classe** pour ajouter une classe au projet.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="b2b0f-161">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="b2b0f-162">Sélectionnez **Classe** dans la fenêtre de modèles, puis entrez `Words.cs` dans le champ Nom.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="b2b0f-163">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-163">Click **Add**.</span></span> <span data-ttu-id="b2b0f-164">La classe `Words` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="b2b0f-165">Ajoutez le code suivant à la classe `Words` :</span><span class="sxs-lookup"><span data-stu-id="b2b0f-165">Add the following code to the `Words` class:</span></span>  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="b2b0f-166">Pour gérer les événements à partir du thread</span><span class="sxs-lookup"><span data-stu-id="b2b0f-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="b2b0f-167">Ajoutez les gestionnaires d’événements suivants au formulaire principal :</span><span class="sxs-lookup"><span data-stu-id="b2b0f-167">Add the following event handlers to your main form:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="b2b0f-168">Pour démarrer et appeler un nouveau thread qui exécute la méthode WordCount</span><span class="sxs-lookup"><span data-stu-id="b2b0f-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="b2b0f-169">Ajoutez les procédures suivantes à votre programme :</span><span class="sxs-lookup"><span data-stu-id="b2b0f-169">Add the following procedures to your program:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  <span data-ttu-id="b2b0f-170">Appelez la méthode `StartThread` à partir du bouton `Start` sur le formulaire :</span><span class="sxs-lookup"><span data-stu-id="b2b0f-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="b2b0f-171">Pour implémenter un bouton Cancel qui arrête le thread</span><span class="sxs-lookup"><span data-stu-id="b2b0f-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="b2b0f-172">Appelez la procédure `StopThread` à partir du gestionnaire d’événements `Click` pour le bouton `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="b2b0f-173">Test</span><span class="sxs-lookup"><span data-stu-id="b2b0f-173">Testing</span></span>  
 <span data-ttu-id="b2b0f-174">Vous pouvez à présent tester l’application afin de vérifier qu’elle fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="b2b0f-175">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="b2b0f-175">To test the application</span></span>  
  
1.  <span data-ttu-id="b2b0f-176">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="b2b0f-177">Quand le formulaire s’affiche, entrez le chemin du fichier que vous souhaitez tester dans la zone `sourceFile`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="b2b0f-178">Par exemple, en supposant que le fichier de test se nomme Test.txt, entrez C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="b2b0f-179">Dans la deuxième zone de texte, entrez un mot ou une expression que l’application va devoir rechercher dans le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="b2b0f-180">Cliquez sur le bouton `Start`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-180">Click the `Start` button.</span></span> <span data-ttu-id="b2b0f-181">Sur le bouton `LinesCounted`, la valeur affichée devrait commencer immédiatement à être incrémentée.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="b2b0f-182">L’application affiche le message « Finished Counting » (Comptage terminé) une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="b2b0f-183">Pour tester le bouton Cancel</span><span class="sxs-lookup"><span data-stu-id="b2b0f-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="b2b0f-184">Appuyez sur F5 pour démarrer l’application, puis entrez le nom de fichier et le mot à rechercher comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="b2b0f-185">Vérifiez que le fichier choisi est suffisamment volumineux pour que vous ayez le temps d’annuler la procédure avant qu’elle ne soit terminée.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="b2b0f-186">Cliquez sur le bouton `Start` pour lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="b2b0f-187">Cliquez sur le bouton `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-187">Click the `Cancel` button.</span></span> <span data-ttu-id="b2b0f-188">L’application devrait cesser le comptage immédiatement.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b2b0f-189">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b2b0f-189">Next Steps</span></span>  
 <span data-ttu-id="b2b0f-190">Cette application contient une fonctionnalité de base de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-190">This application contains some basic error handling.</span></span> <span data-ttu-id="b2b0f-191">Elle détecte les chaînes de recherche vides.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-191">It detects blank search strings.</span></span> <span data-ttu-id="b2b0f-192">Vous pouvez rendre ce programme plus robuste en lui permettant de gérer d’autres erreurs, telles que le dépassement du nombre maximal de mots ou de lignes pouvant être comptés.</span><span class="sxs-lookup"><span data-stu-id="b2b0f-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b0f-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2b0f-193">See Also</span></span>  
 [<span data-ttu-id="b2b0f-194">Threading (C#)</span><span class="sxs-lookup"><span data-stu-id="b2b0f-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="b2b0f-195">Guide pratique pour s’abonner et se désabonner d’événements</span><span class="sxs-lookup"><span data-stu-id="b2b0f-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
