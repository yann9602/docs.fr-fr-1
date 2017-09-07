---
title: "Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 541a1ec788c337eea9965b8a46155e5c6606ea2f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)
Cette procédure pas à pas montre comment créer une application Windows Forms multithread qui recherche les occurrences d’un mot dans un fichier texte. Elle présente les points suivants :  
  
-   Définition d’une classe avec une méthode qui peut être appelée par le composant <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Gestion des événements déclenchés par le composant <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Démarrage d’un composant <xref:System.ComponentModel.BackgroundWorker> pour exécuter une méthode.  
  
-   Implémentation d’un bouton `Cancel` qui arrête le composant <xref:System.ComponentModel.BackgroundWorker>.  
  
### <a name="to-create-the-user-interface"></a>Pour créer l'interface utilisateur  
  
1.  Ouvrez un nouveau projet d’application Windows Forms C#, puis créez un formulaire nommé `Form1`.  
  
2.  Ajoutez deux boutons et quatre zones de texte à `Form1`.  
  
3.  Nommez les objets de la façon indiquée dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |Premier bouton|`Name`, `Text`|Start, Start|  
    |Deuxième bouton|`Name`, `Text`|Cancel, Cancel|  
    |Première zone de texte|`Name`, `Text`|SourceFile, ""|  
    |Deuxième zone de texte|`Name`, `Text`|CompareString, ""|  
    |Troisième zone de texte|`Name`, `Text`|WordsCounted, "0"|  
    |Quatrième zone de texte|`Name`, `Text`|LinesCounted, "0"|  
  
4.  Ajoutez une étiquette à côté de chaque zone de texte. Définissez la propriété `Text` pour chaque étiquette, comme illustré dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |Première étiquette|`Text`|Fichier source|  
    |Deuxième étiquette|`Text`|Compare String|  
    |Troisième étiquette|`Text`|Matching Words|  
    |Quatrième étiquette|`Text`|Lines Counted|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>Pour créer un composant BackgroundWorker et s’abonner à ses événements  
  
1.  Ajoutez au formulaire un composant <xref:System.ComponentModel.BackgroundWorker> de la section **Composants** de la **boîte à outils**. Il apparaît dans la barre d’état des composants du formulaire.  
  
2.  Définissez les propriétés suivantes de l’objet backgroundWorker1.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
3.  Abonnez-vous aux événements de l’objet backgroundWorker1. En haut de la fenêtre **Propriétés**, cliquez sur l’icône **Événements**. Double-cliquez sur l’événement `RunWorkerCompleted` pour créer une méthode de gestionnaire d’événements. Effectuez la même opération pour les événements `ProgressChanged` et `DoWork`.  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Pour définir la méthode qui s’exécutera sur un thread distinct  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter une classe** pour ajouter une classe au projet. La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
2.  Sélectionnez **Classe** dans la fenêtre de modèles, puis entrez `Words.cs` dans le champ Nom.  
  
3.  Cliquez sur **Ajouter**. La classe `Words` s’affiche.  
  
4.  Ajoutez le code suivant à la classe `Words` :  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>Pour gérer les événements à partir du thread  
  
-   Ajoutez les gestionnaires d’événements suivants au formulaire principal :  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Pour démarrer et appeler un nouveau thread qui exécute la méthode WordCount  
  
1.  Ajoutez les procédures suivantes à votre programme :  
  
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
  
2.  Appelez la méthode `StartThread` à partir du bouton `Start` sur le formulaire :  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Pour implémenter un bouton Cancel qui arrête le thread  
  
    -   Appelez la procédure `StopThread` à partir du gestionnaire d’événements `Click` pour le bouton `Cancel`.  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a>Test  
 Vous pouvez à présent tester l’application afin de vérifier qu’elle fonctionne correctement.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Quand le formulaire s’affiche, entrez le chemin du fichier que vous souhaitez tester dans la zone `sourceFile`. Par exemple, en supposant que le fichier de test se nomme Test.txt, entrez C:\Test.txt.  
  
3.  Dans la deuxième zone de texte, entrez un mot ou une expression que l’application va devoir rechercher dans le fichier texte.  
  
4.  Cliquez sur le bouton `Start`. Sur le bouton `LinesCounted`, la valeur affichée devrait commencer immédiatement à être incrémentée. L’application affiche le message « Finished Counting » (Comptage terminé) une fois l’opération terminée.  
  
#### <a name="to-test-the-cancel-button"></a>Pour tester le bouton Cancel  
  
1.  Appuyez sur F5 pour démarrer l’application, puis entrez le nom de fichier et le mot à rechercher comme décrit dans la procédure précédente. Vérifiez que le fichier choisi est suffisamment volumineux pour que vous ayez le temps d’annuler la procédure avant qu’elle ne soit terminée.  
  
2.  Cliquez sur le bouton `Start` pour lancer l’application.  
  
3.  Cliquez sur le bouton `Cancel`. L’application devrait cesser le comptage immédiatement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application contient une fonctionnalité de base de gestion des erreurs. Elle détecte les chaînes de recherche vides. Vous pouvez rendre ce programme plus robuste en lui permettant de gérer d’autres erreurs, telles que le dépassement du nombre maximal de mots ou de lignes pouvant être comptés.  
  
## <a name="see-also"></a>Voir aussi  
 [Threads (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 [Guide pratique pour s’abonner et se désabonner d’événements](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

