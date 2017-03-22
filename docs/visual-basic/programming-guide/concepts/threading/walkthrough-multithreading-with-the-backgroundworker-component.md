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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3686eb230349876f6cfffd2ad94ed1f547779ab1
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>Procédure pas à pas : Multithreading avec le composant BackgroundWorker (Visual Basic)
Cette procédure pas à pas montre comment créer une application Windows Forms multithread qui recherche dans un fichier texte les occurrences d’un mot. Il montre :  
  
-   Définition d’une classe avec une méthode qui peut être appelée par le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Gestion des événements déclenchés par le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Démarrer un <xref:System.ComponentModel.BackgroundWorker>pour exécuter une méthode.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Implémentation d’un `Cancel` bouton qui arrête le <xref:System.ComponentModel.BackgroundWorker>composant.</xref:System.ComponentModel.BackgroundWorker>  
  
### <a name="to-create-the-user-interface"></a>Pour créer l'interface utilisateur  
  
1.  Ouvrez un nouveau projet d’Application Windows Forms Visual Basic et créez un formulaire nommé `Form1`.  
  
2.  Ajoutez deux boutons et quatre zones de texte `Form1`.  
  
3.  Nommez les objets comme indiqué dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |Premier bouton|`Name`, `Text`|Démarrage, démarrer|  
    |Deuxième bouton|`Name`, `Text`|Annuler, annulation|  
    |Première zone de texte|`Name`, `Text`|SourceFile, « »|  
    |Deuxième zone de texte|`Name`, `Text`|CompareString, « »|  
    |Troisième zone de texte|`Name`, `Text`|WordsCounted, « 0 »|  
    |Quatrième zone de texte|`Name`, `Text`|LinesCounted, « 0 »|  
  
4.  Ajoutez une étiquette en regard de chaque zone de texte. Définir le `Text` propriété pour chaque étiquette, comme illustré dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |Première étiquette|`Text`|Fichier source|  
    |Deuxième contrôle label|`Text`|Comparer des chaînes|  
    |Troisième contrôle label|`Text`|Correspondance de mots|  
    |Quatrième contrôle label|`Text`|Lignes comptées|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>Pour créer un composant BackgroundWorker et s’abonner à ses événements  
  
1.  Ajouter un <xref:System.ComponentModel.BackgroundWorker>composant à partir de la **composants** section de la **boîte à outils** au formulaire.</xref:System.ComponentModel.BackgroundWorker> Il apparaît dans la barre d’état des composants du formulaire.  
  
2.  Définissez les propriétés suivantes de l’objet BackgroundWorker1.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Pour définir la méthode qui s’exécutera sur un thread distinct  
  
1.  À partir de la **projet** menu, choisissez **ajouter une classe** pour ajouter une classe au projet. Le **ajouter un nouvel élément** boîte de dialogue s’affiche.  
  
2.  Sélectionnez **classe** à partir de la fenêtre de modèles, puis entrez `Words.vb` dans le champ nom.  
  
3.  Cliquez sur **Ajouter**. La `Words` classe s’affiche.  
  
4.  Ajoutez le code suivant à la classe `Words` :  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>Pour gérer les événements à partir du thread  
  
-   Ajoutez les gestionnaires d’événements suivant à votre formulaire principal :  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Pour démarrer et appeler un nouveau thread qui exécute la méthode WordCount  
  
1.  Ajoutez les procédures suivantes pour votre programme :  
  
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
  
2.  Appelez le `StartThread` méthode à partir de la `Start` bouton sur votre formulaire :  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Pour implémenter un bouton Cancel qui arrête le thread  
  
-   Appelez le `StopThread` procédure à partir de la `Click` Gestionnaire d’événements pour le `Cancel` bouton.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>Test  
 Vous pouvez maintenant tester l’application pour vérifier qu’il fonctionne correctement.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Lorsque le formulaire s’affiche, entrez le chemin d’accès du fichier que vous souhaitez tester dans la `sourceFile` boîte. Par exemple, en supposant que votre fichier de test se nomme Test.txt, entrez C:\Test.txt.  
  
3.  Dans la deuxième zone de texte, entrez un mot ou expression à rechercher dans le fichier texte de l’application.  
  
4.  Cliquez sur le bouton `Start`. Le `LinesCounted` bouton doit commencer immédiatement. L’application affiche le message « Finished Counting » lorsqu’il est terminé.  
  
#### <a name="to-test-the-cancel-button"></a>Pour tester le bouton Annuler  
  
1.  Appuyez sur F5 pour démarrer l’application, entrez le mot fichier recherche et le nom comme décrit dans la procédure précédente. Assurez-vous que le fichier choisi est suffisamment volumineux pour que vous ayez le temps d’annuler la procédure avant la fin.  
  
2.  Cliquez sur le `Start` bouton pour démarrer l’application.  
  
3.  Cliquez sur le bouton `Cancel`. L’application devrait cesser le décompte immédiatement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application contient une gestion des erreurs de base. Il détecte les chaînes de recherche vides. Vous pouvez rendre ce programme plus robuste en gérant les autres erreurs, telles que le dépassement du nombre maximal de mots ou de lignes qui peuvent être comptées.  
  
## <a name="see-also"></a>Voir aussi  
 [Threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [Procédure pas à pas : Création d’un composant Simple multithread avec Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)   
 [Comment : s’abonner et annuler l’abonnement à des événements](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
