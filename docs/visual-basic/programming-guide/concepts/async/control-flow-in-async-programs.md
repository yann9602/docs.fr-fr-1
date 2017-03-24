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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a>Flux de contrôle dans les programmes Async (Visual Basic)
Vous pouvez écrire et maintenir plus facilement des programmes asynchrones à l’aide de la `Async` et `Await` mots clés. Toutefois, les résultats peuvent vous surprendre si vous ne comprenez pas le fonctionnement de votre programme. Traces de cette rubrique le flux de contrôle via un programme asynchrone simple pour vous montrer lorsque le contrôle passe à partir d’une méthode à un autre et les informations est transféré à chaque fois.  
  
> [!NOTE]
>  Les mots clés `Async` et `Await` ont été introduites dans Visual Studio 2012.  
  
 En général, vous marquez les méthodes qui contiennent du code asynchrone avec le [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificateur. Dans une méthode qui est marquée avec un modificateur async, vous pouvez utiliser un [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) (opérateur) pour spécifier où la méthode Pause pour attendre un processus asynchrone appelé terminer. Pour plus d’informations, consultez [programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 L’exemple suivant utilise les méthodes async pour télécharger le contenu d’un site Web spécifié sous forme de chaîne et afficher la longueur de la chaîne. L’exemple contient deux méthodes suivantes.  
  
-   `startButton_Click`, qui appelle la méthode `AccessTheWebAsync` et affiche le résultat.  
  
-   `AccessTheWebAsync`, qui télécharge le contenu d’un site Web sous forme de chaîne et retourne la longueur de la chaîne. `AccessTheWebAsync`utilise asynchrone <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>permet de télécharger le contenu.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient>  
  
 Numérotées affichage lignes apparaissent aux points stratégiques tout au long du programme pour vous aider à comprendre comment le programme s’exécute et d’expliquer ce qui se produit à chaque point est marqué. Les lignes d’affichage sont étiquetés « Un » à « 6. » Les étiquettes représentent l’ordre dans lequel le programme atteint ces lignes de code.  
  
 Le code suivant montre un plan du programme.  
  
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
  
 Chaque emplacement étiqueté, « Un » à « 6, » affiche des informations sur l’état actuel du programme. La sortie suivante est produite.  
  
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
  
## <a name="set-up-the-program"></a>Configurer le programme  
 Vous pouvez télécharger le code qui utilise cette rubrique à partir de MSDN, ou vous pouvez la créer vous-même.  
  
> [!NOTE]
>  Pour exécuter l’exemple, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.  
  
### <a name="download-the-program"></a>Téléchargez le programme  
 Vous pouvez télécharger l’application de cette rubrique à partir de [exemple Async : flux de contrôle dans les programmes Async](http://go.microsoft.com/fwlink/?LinkId=255285). Les étapes suivantes, ouvrent et exécutez le programme.  
  
1.  Décompressez le fichier téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Accédez au dossier qui contient le code exemple décompressé, ouvrez le fichier solution (.sln), puis appuyez sur F5 pour générer et exécuter le projet.  
  
### <a name="build-the-program-yourself"></a>Générer le programme vous-même  
 Le projet Windows Presentation Foundation (WPF) suivant contient l’exemple de code de cette rubrique.  
  
 Pour exécuter le projet, procédez comme suit :  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le **modèles installés** volet, choisissez **Visual Basic**, puis choisissez **Application WPF** dans la liste des types de projet.  
  
4.  Entrez `AsyncTracer` comme nom du projet, puis choisissez le **OK** bouton.  
  
     Le nouveau projet s’affiche dans **l’Explorateur de solutions**.  
  
5.  Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .  
  
     Si l’onglet n’est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans **l’Explorateur de solutions**, puis choisissez **afficher le Code**.  
  
6.  Dans le **XAML** du MainWindow.xaml, remplacez le code par le code suivant.  
  
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
  
     Une fenêtre simple contenant une zone de texte et un bouton s’affiche dans le **conception** vue de MainWindow.xaml.  
  
7.  Ajoutez une référence pour <xref:System.Net.Http>.</xref:System.Net.Http>  
  
8.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.vb, puis choisissez **afficher le Code**.  
  
9. Dans MainWindow.xaml.vb, remplacez le code par le code suivant.  
  
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
  
10. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .  
  
     La sortie suivante doit s’afficher.  
  
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
  
## <a name="trace-the-program"></a>Le programme de trace  
  
### <a name="steps-one-and-two"></a>Étapes UNE et DEUX  
 Les deux premières afficher des lignes de suivre le chemin d’accès en tant que `startButton_Click` appelle `AccessTheWebAsync`, et `AccessTheWebAsync` appelle la <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient> de asynchrone L’image suivante présente les appels de méthode en méthode.  
  
 ![Étapes un et deux](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")  
  
 Le type de retour de `AccessTheWebAsync` et `client.GetStringAsync` est <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> Pour `AccessTheWebAsync`, TResult est un entier. Pour `GetStringAsync`, TResult est une chaîne. Pour plus d’informations sur les types de retour de méthode asynchrone, consultez [les Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Une méthode async retournant des tâches renvoie une instance de tâche lorsque le contrôle passe à l’appelant. Le contrôle retourne d’une méthode async à son appelant soit lorsque un `Await` opérateur est rencontrée dans la méthode appelée ou lorsque la méthode appelée se termine. Les lignes d’affichage portant le nom « Trois » à « 6 » de cette partie du processus de suivi.  
  
### <a name="step-three"></a>Étape TROIS  
 Dans `AccessTheWebAsync`, la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>est appelée pour télécharger le contenu de la page Web cible.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> Le contrôle retourne de `client.GetStringAsync` à `AccessTheWebAsync` lorsque `client.GetStringAsync` renvoie.  
  
 Le `client.GetStringAsync` méthode retourne une tâche de la chaîne est assignée à la `getStringTask` variable `AccessTheWebAsync`. La ligne suivante dans l’exemple de programme illustre l’appel à `client.GetStringAsync` et l’affectation.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Vous pouvez considérer la tâche en tant qu’une promesse par `client.GetStringAsync` pour produire une chaîne réelle par la suite. En attendant, si `AccessTheWebAsync` a du travail à faire qui ne dépend de la chaîne de promis `client.GetStringAsync`, que le travail peut continuer pendant que `client.GetStringAsync` attend. Dans l’exemple, les lignes suivantes de sortie, qui sont étiquetés « Trois », représentent l’opportunité d’effectuer un travail indépendant  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 L’instruction suivante interrompt la progression dans `AccessTheWebAsync` lorsque `getStringTask` est attendue.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 L’illustration suivante montre le flux de contrôle à partir de `client.GetStringAsync` pour l’assignation à `getStringTask` et de la création de `getStringTask` à l’application d’un opérateur Await.  
  
 ![Étape&3;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-3")  
  
 L’expression await suspend `AccessTheWebAsync` jusqu'à ce que `client.GetStringAsync` retourne. Entre-temps, le contrôle retourne à l’appelant de `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  En règle générale, vous attendez immédiatement l’appel à une méthode asynchrone. Par exemple, l’assignation suivante pourrait remplacer le code précédent qui crée et puis attend `getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  Dans cette rubrique, l’opérateur await est appliqué ultérieurement pour prendre en compte les lignes de sortie qui marquent le flux de contrôle via le programme.  
  
### <a name="step-four"></a>Étape QUATRE  
 Type de retour le déclaré `AccessTheWebAsync` est `Task(Of Integer)`. Par conséquent, lorsque `AccessTheWebAsync` est suspendue, elle retourne une tâche d’entier `startButton_Click`. Vous devez comprendre que la tâche retournée n’est pas `getStringTask`. La tâche retournée est une tâche d’entier qui représente ce qui reste à faire dans la méthode suspendue, `AccessTheWebAsync`. La tâche est une promesse de `AccessTheWebAsync` pour produire un entier lorsque la tâche est terminée.  
  
 L’instruction suivante assigne cette tâche à la `getLengthTask` variable.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Comme dans `AccessTheWebAsync`, `startButton_Click` peut poursuivre une tâche qui ne dépende pas des résultats de la tâche asynchrone (`getLengthTask`) jusqu'à ce que la tâche est attendue. Les lignes de sortie suivantes représentent ce travail.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Progresser dans `startButton_Click` est suspendue lorsque `getLengthTask` est attendue. L’instruction d’assignation suivante interrompt `startButton_Click` jusqu'à ce que `AccessTheWebAsync` est terminée.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 Dans l’illustration suivante, les flèches indiquent le flux de contrôle de l’expression await dans `AccessTheWebAsync` à l’affectation d’une valeur à `getLengthTask`, suivi par le traitement normal de `startButton_Click` jusqu'à ce que `getLengthTask` est attendue.  
  
 ![Étape&4;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-quatre")  
  
### <a name="step-five"></a>Étape CINQ  
 Lors de la `client.GetStringAsync` signale qu’elle est terminée, le traitement de `AccessTheWebAsync` est libéré de la suspension et pouvez passer à l’instruction await. Les lignes de sortie suivantes représentent la reprise du traitement.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 L’opérande de l’instruction return, `urlContents.Length`, est stocké dans la tâche qui `AccessTheWebAsync` retourne. L’expression await récupère cette valeur à partir de `getLengthTask` dans `startButton_Click`.  
  
 L’illustration suivante montre le transfert du contrôle après `client.GetStringAsync` (et `getStringTask`) sont terminées.  
  
 ![Étape&5;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-cinq")  
  
 `AccessTheWebAsync`s’exécute jusqu'à achèvement et le contrôle retourne à `startButton_Click`, qui est en attente de l’achèvement.  
  
### <a name="step-six"></a>Étape SIX  
 Lors de la `AccessTheWebAsync` signale qu’il est terminé, le traitement peut continuer après l’instruction await dans `startButton_Async`. En fait, le programme n’a plus rien à faire.  
  
 Les lignes de sortie suivantes représentent la reprise du traitement `startButton_Async`:  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 L’extrait de l’expression await `getLengthTask` la valeur entière qui est l’opérande de l’instruction return dans `AccessTheWebAsync`. L’instruction suivante assigne la valeur à la `contentLength` variable.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 L’illustration suivante montre le retour du contrôle à partir de `AccessTheWebAsync` à `startButton_Click`.  
  
 ![Étape&6;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [Procédure pas à pas : Accès Web en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Exemple Async : Contrôle de flux dans les programmes Async (c# et Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)
