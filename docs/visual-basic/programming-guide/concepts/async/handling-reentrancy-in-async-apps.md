---
title: "Gestion de la réentrance dans Async Apps (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45dfc4dd4ab42c3ce8edd7e41b7b0401bb0db672
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="da138-102">Gestion de la réentrance dans Async Apps (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da138-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="da138-103">Quand vous incluez du code asynchrone dans votre application, vous devez prendre en compte et éventuellement empêcher la réentrance, qui fait référence à une nouvelle entrée d'une opération asynchrone avant qu'elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="da138-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="da138-104">Si vous n'identifiez pas et ne gérez pas les possibilités de réentrance, les résultats peuvent être inattendus.</span><span class="sxs-lookup"><span data-stu-id="da138-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="da138-105">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="da138-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="da138-106">Identification de la réentrance</span><span class="sxs-lookup"><span data-stu-id="da138-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="da138-107">Gestion de la réentrance</span><span class="sxs-lookup"><span data-stu-id="da138-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="da138-108">Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="da138-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="da138-109">Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="da138-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="da138-110">Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="da138-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="da138-111">Examen et exécution de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="da138-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="da138-112">Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da138-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="da138-113"><a name="BKMK_RecognizingReentrancy"></a> Identification de la réentrance</span><span class="sxs-lookup"><span data-stu-id="da138-113"><a name="BKMK_RecognizingReentrancy"></a> Recognizing Reentrancy</span></span>  
 <span data-ttu-id="da138-114">Dans l’exemple de cette rubrique, les utilisateurs choisissent un bouton **Démarrer** pour lancer une application asynchrone qui télécharge une série de sites web et calcule le nombre total d’octets téléchargés.</span><span class="sxs-lookup"><span data-stu-id="da138-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="da138-115">Une version synchrone de l’exemple répondrait de la même façon quel que soit le nombre de fois où un utilisateur clique sur le bouton car, après la première fois, le thread d’interface utilisateur ignore ces événements jusqu’à ce que l’application arrête de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="da138-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="da138-116">Dans une application asynchrone, en revanche, le thread d'interface utilisateur continue de répondre et vous pouvez entrer à nouveau l'opération asynchrone avant qu'elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="da138-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="da138-117">L’exemple suivant illustre la sortie attendue si l’utilisateur choisit le bouton **Démarrer** une seule fois.</span><span class="sxs-lookup"><span data-stu-id="da138-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="da138-118">La liste des sites web téléchargés apparaît avec la taille, en octets, de chaque site.</span><span class="sxs-lookup"><span data-stu-id="da138-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="da138-119">Le nombre total d'octets apparaît à la fin.</span><span class="sxs-lookup"><span data-stu-id="da138-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="da138-120">Toutefois, si l'utilisateur choisit le bouton plusieurs fois, le gestionnaire d'événements est appelé à plusieurs reprises et le processus de téléchargement est à nouveau entré à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="da138-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="da138-121">Ainsi, plusieurs opérations asynchrones s'exécutent en même temps, la sortie entrelace les résultats et le nombre total d'octets est source de confusion.</span><span class="sxs-lookup"><span data-stu-id="da138-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="da138-122">Vous pouvez passer en revue le code qui produit cette sortie en accédant à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="da138-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="da138-123">Vous pouvez faire des essais avec le code en téléchargeant la solution sur votre ordinateur local, puis en exécutant le projet WebsiteDownload ou en utilisant le code donné à la fin de cette rubrique pour créer votre propre projet. Pour plus d’informations et d’instructions, consultez [Examen et exécution de l’exemple d’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="da138-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <span data-ttu-id="da138-124"><a name="BKMK_HandlingReentrancy"></a> Gestion de la réentrance</span><span class="sxs-lookup"><span data-stu-id="da138-124"><a name="BKMK_HandlingReentrancy"></a> Handling Reentrancy</span></span>  
 <span data-ttu-id="da138-125">Vous pouvez gérer la réentrance de différentes façons, selon ce que vous voulez que votre application fasse.</span><span class="sxs-lookup"><span data-stu-id="da138-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="da138-126">Cette rubrique présente les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="da138-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="da138-127">Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="da138-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="da138-128">Désactivez le bouton **Démarrer** pendant que l’opération est en cours d’exécution afin que l’utilisateur ne puisse pas l’interrompre.</span><span class="sxs-lookup"><span data-stu-id="da138-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="da138-129">Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="da138-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="da138-130">Annulez toute opération encore en cours d’exécution quand l’utilisateur choisit le bouton **Démarrer** à nouveau, puis laissez l’opération demandée le plus récemment continuer.</span><span class="sxs-lookup"><span data-stu-id="da138-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="da138-131">Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="da138-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="da138-132">Autorisez toutes les opérations demandées à s'exécuter de façon asynchrone, mais coordonnez l'affichage de la sortie de sorte que les résultats de chaque opération apparaissent ensemble et dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="da138-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <span data-ttu-id="da138-133"><a name="BKMK_DisableTheStartButton"></a> Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="da138-133"><a name="BKMK_DisableTheStartButton"></a> Disable the Start Button</span></span>  
 <span data-ttu-id="da138-134">Vous pouvez bloquer le bouton **Démarrer** pendant l’exécution d’une opération en désactivant le bouton en haut du gestionnaire d’événements `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="da138-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="da138-135">Ensuite, vous pouvez réactiver le bouton depuis un bloc `Finally` quand l'opération se termine pour que les utilisateurs puissent exécuter à nouveau l'application.</span><span class="sxs-lookup"><span data-stu-id="da138-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="da138-136">Le code suivant illustre ces modifications, marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="da138-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="da138-137">Vous pouvez ajouter les modifications apportées au code à la fin de cette rubrique, ou vous pouvez télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="da138-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="da138-138">Le nom du projet est DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="da138-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="da138-139">Suite aux modifications, le bouton ne répond pas pendant que `AccessTheWebAsync` télécharge les sites Web, donc le processus ne peut pas être entré de nouveau.</span><span class="sxs-lookup"><span data-stu-id="da138-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <span data-ttu-id="da138-140"><a name="BKMK_CancelAndRestart"></a> Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="da138-140"><a name="BKMK_CancelAndRestart"></a> Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="da138-141">Au lieu de désactiver le bouton **Démarrer**, vous pouvez garder le bouton actif. Toutefois, si l’utilisateur choisit de nouveau ce bouton, annulez l’opération qui est déjà en cours d’exécution et laissez continuer l’opération le plus récemment démarrée.</span><span class="sxs-lookup"><span data-stu-id="da138-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="da138-142">Pour plus d’informations sur l’annulation, consultez [réglage (Visual Basic) de votre Application Async](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="da138-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="da138-143">Pour configurer ce scénario, apportez les modifications suivantes au code de base fourni dans [Examen et exécution de l’exemple d’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="da138-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="da138-144">Vous pouvez également télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="da138-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="da138-145">Le nom de ce projet est CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="da138-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="da138-146">Déclarez une variable <xref:System.Threading.CancellationTokenSource>, `cts`, qui est dans la portée de toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="da138-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="da138-147">Dans `StartButton_Click`, déterminez si une opération est déjà en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="da138-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="da138-148">Si la valeur de `cts` est `Nothing`, aucune opération n’est déjà active.</span><span class="sxs-lookup"><span data-stu-id="da138-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="da138-149">Si la valeur n’est pas `Nothing`, l’opération est déjà en cours d’exécution est annulée.</span><span class="sxs-lookup"><span data-stu-id="da138-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="da138-150">Définissez `cts` sur une autre valeur qui représente le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="da138-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="da138-151">À la fin de `StartButton_Click`, le processus en cours est terminé, par conséquent, définissez la valeur de `cts` à `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="da138-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="da138-152">Le code suivant illustre toutes les modifications dans `StartButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="da138-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="da138-153">Les ajouts sont marqués par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="da138-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="da138-154">Dans `AccessTheWebAsync`, apportez les modifications suivantes.</span><span class="sxs-lookup"><span data-stu-id="da138-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="da138-155">Ajoutez un paramètre pour accepter le jeton d'annulation en provenance de `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="da138-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="da138-156">Utilisez la méthode <xref:System.Net.Http.HttpClient.GetAsync%2A> pour télécharger les sites Web car `GetAsync` accepte un argument <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="da138-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="da138-157">Avant d'appeler `DisplayResults` pour afficher les résultats de chaque site Web téléchargé, vérifiez `ct` pour vous assurer que l'opération en cours n'a pas été annulée.</span><span class="sxs-lookup"><span data-stu-id="da138-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="da138-158">Le code suivant illustre ces modifications, marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="da138-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="da138-159">Si vous choisissez le bouton **Démarrer** plusieurs fois pendant l’exécution de cette application, les résultats produits doivent ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="da138-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="da138-160">Pour éliminer les listes partielles, supprimez les commentaires de la première ligne de code dans `StartButton_Click` pour effacer la zone de texte chaque fois que l'utilisateur redémarre l'opération.</span><span class="sxs-lookup"><span data-stu-id="da138-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <span data-ttu-id="da138-161"><a name="BKMK_RunMultipleOperations"></a> Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="da138-161"><a name="BKMK_RunMultipleOperations"></a> Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="da138-162">Ce troisième exemple est le plus compliqué, car l’application démarre une autre opération asynchrone chaque fois que l’utilisateur choisit le bouton **Démarrer**, et toutes les opérations s’exécutent jusqu’à leur achèvement.</span><span class="sxs-lookup"><span data-stu-id="da138-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="da138-163">Toutes les opérations demandées téléchargent des sites web de la liste de façon asynchrone, mais la sortie des opérations est présentée séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="da138-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="da138-164">Autrement dit, l’activité de téléchargement réelle est entrelacée, comme le montre la sortie dans [Identification de la réentrance](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), mais la liste des résultats de chaque groupe est présentée séparément.</span><span class="sxs-lookup"><span data-stu-id="da138-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="da138-165">Les opérations partagent un <xref:System.Threading.Tasks.Task> global, `pendingWork`, qui sert d'opérateur de contrôle d'appels pour le processus d'affichage.</span><span class="sxs-lookup"><span data-stu-id="da138-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="da138-166">Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour télécharger l’exemple, puis exécuter le projet QueueResults.</span><span class="sxs-lookup"><span data-stu-id="da138-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="da138-167">La sortie suivante montre le résultat obtenu si l’utilisateur choisit le bouton **Démarrer** une seule fois.</span><span class="sxs-lookup"><span data-stu-id="da138-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="da138-168">L’étiquette A indique que le résultat part de la première fois que le bouton **Démarrer** est choisi.</span><span class="sxs-lookup"><span data-stu-id="da138-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="da138-169">Les numéros indiquent l'ordre des URL dans la liste des cibles de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="da138-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="da138-170">Si l’utilisateur choisit le bouton **Démarrer** trois fois, l’application produit une sortie semblable aux lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="da138-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="da138-171">Les lignes d'information qui commencent par un signe dièse (#) suivent la progression de l'application.</span><span class="sxs-lookup"><span data-stu-id="da138-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="da138-172">Les groupes B et C démarrent avant que le groupe A ait terminé, mais la sortie de chaque groupe apparaît séparément.</span><span class="sxs-lookup"><span data-stu-id="da138-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="da138-173">Toute la sortie du groupe A apparaît en premier, suivie de toute la sortie du groupe B, puis de toute la sortie du groupe C. L’application affiche toujours les groupes dans l’ordre et, pour chaque groupe, elle affiche toujours les informations sur les sites web, dans l’ordre où les URL apparaissent dans la liste des URL.</span><span class="sxs-lookup"><span data-stu-id="da138-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="da138-174">Toutefois, vous ne pouvez pas prévoir l'ordre dans lequel les téléchargements se produisent réellement.</span><span class="sxs-lookup"><span data-stu-id="da138-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="da138-175">Après le démarrage de plusieurs groupes, les tâches de téléchargement qu'ils génèrent sont toutes actives.</span><span class="sxs-lookup"><span data-stu-id="da138-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="da138-176">Vous ne pouvez pas supposer que A-1 sera téléchargé avant B-1 ni que A-1 sera téléchargé avant A-2.</span><span class="sxs-lookup"><span data-stu-id="da138-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="da138-177">Définitions globales</span><span class="sxs-lookup"><span data-stu-id="da138-177">Global Definitions</span></span>  
 <span data-ttu-id="da138-178">L'exemple de code contient les deux déclarations globales suivantes qui sont visibles à partir de toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="da138-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="da138-179">La variable `Task`, `pendingWork`, supervise le processus d'affichage et empêche tout groupe d'interrompre l'opération d'affichage d'un autre groupe.</span><span class="sxs-lookup"><span data-stu-id="da138-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="da138-180">La variable de caractère `group`, étiquette la sortie de différents groupes pour vérifier que les résultats apparaissent dans l'ordre attendu.</span><span class="sxs-lookup"><span data-stu-id="da138-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="da138-181">Gestionnaire d'événements Click</span><span class="sxs-lookup"><span data-stu-id="da138-181">The Click Event Handler</span></span>  
 <span data-ttu-id="da138-182">Le gestionnaire d’événements, `StartButton_Click`, incrémente la lettre du groupe chaque fois que l’utilisateur choisit le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="da138-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="da138-183">Ensuite, le gestionnaire appelle `AccessTheWebAsync` pour exécuter l'opération de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="da138-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="da138-184">Méthode AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="da138-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="da138-185">Cet exemple fractionne `AccessTheWebAsync` en deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="da138-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="da138-186">La première méthode, `AccessTheWebAsync`, démarre toutes les tâches de téléchargement d'un groupe et configure `pendingWork` pour contrôler le processus d'affichage.</span><span class="sxs-lookup"><span data-stu-id="da138-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="da138-187">La méthode utilise une requête LINQ (Language Integrated Query) et <xref:System.Linq.Enumerable.ToArray%2A> pour démarrer toutes les tâches de téléchargement en même temps.</span><span class="sxs-lookup"><span data-stu-id="da138-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="da138-188">`AccessTheWebAsync` appelle ensuite `FinishOneGroupAsync` pour attendre la fin de chaque téléchargement et en afficher la longueur.</span><span class="sxs-lookup"><span data-stu-id="da138-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="da138-189">`FinishOneGroupAsync` retourne une tâche assignée à `pendingWork` dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="da138-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="da138-190">Cette valeur empêche toute interruption par une autre opération avant que la tâche ne soit terminée.</span><span class="sxs-lookup"><span data-stu-id="da138-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="da138-191">Méthode FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="da138-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="da138-192">Cette méthode parcourt les tâches de téléchargement dans un groupe, en attendant chacune d’elles, en affichant la longueur du site web téléchargé et en ajoutant la longueur au total.</span><span class="sxs-lookup"><span data-stu-id="da138-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="da138-193">La première instruction dans `FinishOneGroupAsync` utilise `pendingWork` pour vérifier que l’entrée de la méthode n’interfère pas avec une opération qui est déjà dans le processus d’affichage ou qui est déjà en train d’attendre.</span><span class="sxs-lookup"><span data-stu-id="da138-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="da138-194">Si une telle opération est en cours, l'opération d'entrée doit attendre son tour.</span><span class="sxs-lookup"><span data-stu-id="da138-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="da138-195">Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour télécharger l’exemple, puis exécuter le projet QueueResults.</span><span class="sxs-lookup"><span data-stu-id="da138-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="da138-196">Points d'intérêt</span><span class="sxs-lookup"><span data-stu-id="da138-196">Points of Interest</span></span>  
 <span data-ttu-id="da138-197">Les lignes d'information qui commencent par un signe dièse (#) dans la sortie clarifient le fonctionnement de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="da138-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="da138-198">La sortie affiche les modèles suivants.</span><span class="sxs-lookup"><span data-stu-id="da138-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="da138-199">Un groupe peut être démarré pendant qu'un groupe précédent affiche sa sortie, mais l'affichage de la sortie du groupe précédent n'est pas interrompu.</span><span class="sxs-lookup"><span data-stu-id="da138-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="da138-200">Le `pendingWork` tâche est `Nothing` au début de `FinishOneGroupAsync` uniquement pour le groupe A, ce qui a démarré en premier.</span><span class="sxs-lookup"><span data-stu-id="da138-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="da138-201">Le groupe A n'a pas encore terminé une expression await quand il atteint `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="da138-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="da138-202">Par conséquent, le contrôle n'a pas retourné à `AccessTheWebAsync`, et la première assignation à `pendingWork` ne s'est pas produite.</span><span class="sxs-lookup"><span data-stu-id="da138-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="da138-203">Les deux lignes suivantes apparaissent toujours ensemble dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="da138-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="da138-204">Le code n'est jamais interrompu entre le démarrage d'une opération de groupe dans `StartButton_Click` et l'affectation d'une tâche pour le groupe à `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="da138-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="da138-205">Une fois qu'un groupe entre `StartButton_Click`, l'opération ne termine pas une expression await tant que l'opération n'entre pas `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="da138-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="da138-206">Par conséquent, aucune autre opération ne peut obtenir le contrôle au cours de ce segment de code.</span><span class="sxs-lookup"><span data-stu-id="da138-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <span data-ttu-id="da138-207"><a name="BKMD_SettingUpTheExample"></a> Examen et exécution de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="da138-207"><a name="BKMD_SettingUpTheExample"></a> Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="da138-208">Pour mieux comprendre l’exemple d’application, vous pouvez le télécharger, le créer vous-même ou passer en revue le code à la fin de cette rubrique sans implémenter l’application.</span><span class="sxs-lookup"><span data-stu-id="da138-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da138-209">Pour exécuter l’exemple comme une application de bureau WPF, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da138-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <span data-ttu-id="da138-210"><a name="BKMK_DownloadingTheApp"></a> Téléchargement de l’application</span><span class="sxs-lookup"><span data-stu-id="da138-210"><a name="BKMK_DownloadingTheApp"></a> Downloading the App</span></span>  
  
1.  <span data-ttu-id="da138-211">Téléchargez le fichier compressé dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="da138-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="da138-212">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da138-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="da138-213">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="da138-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="da138-214">Accédez au dossier qui contient l’exemple de code décompressé, puis ouvrez le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="da138-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="da138-215">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet à modifier, puis choisissez **Définir comme StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="da138-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="da138-216">Appuyez sur les touches CTRL+F5 pour générer et exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="da138-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <span data-ttu-id="da138-217"><a name="BKMK_BuildingTheApp"></a> Génération de l’application</span><span class="sxs-lookup"><span data-stu-id="da138-217"><a name="BKMK_BuildingTheApp"></a> Building the App</span></span>  
 <span data-ttu-id="da138-218">La section suivante fournit le code pour générer l’exemple comme une application WPF.</span><span class="sxs-lookup"><span data-stu-id="da138-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="da138-219">Pour générer une application WPF</span><span class="sxs-lookup"><span data-stu-id="da138-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="da138-220">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da138-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="da138-221">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="da138-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="da138-222">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="da138-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="da138-223">Dans le **modèles installés** volet, développez **Visual Basic**, puis développez **Windows**.</span><span class="sxs-lookup"><span data-stu-id="da138-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="da138-224">Dans la liste des types de projets, choisissez **Application WPF**.</span><span class="sxs-lookup"><span data-stu-id="da138-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="da138-225">Nommez le projet `WebsiteDownloadWPF`, puis cliquez sur le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="da138-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="da138-226">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="da138-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="da138-227">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="da138-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="da138-228">Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="da138-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="da138-229">Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da138-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="da138-230">Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="da138-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="da138-231">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="da138-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="da138-232">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.XAML, puis choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="da138-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="da138-233">Dans MainWindow.xaml.vb, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da138-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="da138-234">Appuyez sur les touches CTRL+F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="da138-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="da138-235">Apportez les modifications indiquées dans [Désactiver le bouton Démarrer](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Annuler et redémarrer l’opération](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ou [Exécuter plusieurs opérations et mettre la sortie en file d’attente](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour gérer la réentrance.</span><span class="sxs-lookup"><span data-stu-id="da138-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da138-236">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da138-236">See Also</span></span>  
 [<span data-ttu-id="da138-237">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da138-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="da138-238">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da138-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
