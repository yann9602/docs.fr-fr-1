---
title: "Gestion de la réentrance dans Async Apps (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07157057d7ae94d3c6017544ff654ca0ed7b7cf2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="39eae-102">Gestion de la réentrance dans Async Apps (C#)</span><span class="sxs-lookup"><span data-stu-id="39eae-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="39eae-103">Quand vous incluez du code asynchrone dans votre application, vous devez prendre en compte et éventuellement empêcher la réentrance, qui fait référence à une nouvelle entrée d'une opération asynchrone avant qu'elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="39eae-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="39eae-104">Si vous n'identifiez pas et ne gérez pas les possibilités de réentrance, les résultats peuvent être inattendus.</span><span class="sxs-lookup"><span data-stu-id="39eae-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="39eae-105">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="39eae-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="39eae-106">Identification de la réentrance</span><span class="sxs-lookup"><span data-stu-id="39eae-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="39eae-107">Gestion de la réentrance</span><span class="sxs-lookup"><span data-stu-id="39eae-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="39eae-108">Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="39eae-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="39eae-109">Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="39eae-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="39eae-110">Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="39eae-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="39eae-111">Examen et exécution de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="39eae-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="39eae-112">Pour exécuter l’exemple, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="39eae-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="39eae-113">Identification de la réentrance</span><span class="sxs-lookup"><span data-stu-id="39eae-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="39eae-114">Dans l’exemple de cette rubrique, les utilisateurs choisissent un bouton **Démarrer** pour lancer une application asynchrone qui télécharge une série de sites web et calcule le nombre total d’octets téléchargés.</span><span class="sxs-lookup"><span data-stu-id="39eae-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="39eae-115">Une version synchrone de l’exemple répondrait de la même façon quel que soit le nombre de fois où un utilisateur clique sur le bouton car, après la première fois, le thread d’interface utilisateur ignore ces événements jusqu’à ce que l’application arrête de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="39eae-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="39eae-116">Dans une application asynchrone, en revanche, le thread d'interface utilisateur continue de répondre et vous pouvez entrer à nouveau l'opération asynchrone avant qu'elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="39eae-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="39eae-117">L’exemple suivant illustre la sortie attendue si l’utilisateur choisit le bouton **Démarrer** une seule fois.</span><span class="sxs-lookup"><span data-stu-id="39eae-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="39eae-118">La liste des sites web téléchargés apparaît avec la taille, en octets, de chaque site.</span><span class="sxs-lookup"><span data-stu-id="39eae-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="39eae-119">Le nombre total d'octets apparaît à la fin.</span><span class="sxs-lookup"><span data-stu-id="39eae-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="39eae-120">Toutefois, si l'utilisateur choisit le bouton plusieurs fois, le gestionnaire d'événements est appelé à plusieurs reprises et le processus de téléchargement est à nouveau entré à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="39eae-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="39eae-121">Ainsi, plusieurs opérations asynchrones s'exécutent en même temps, la sortie entrelace les résultats et le nombre total d'octets est source de confusion.</span><span class="sxs-lookup"><span data-stu-id="39eae-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
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
  
 <span data-ttu-id="39eae-122">Vous pouvez passer en revue le code qui produit cette sortie en accédant à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="39eae-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="39eae-123">Vous pouvez faire des essais avec le code en téléchargeant la solution sur votre ordinateur local, puis en exécutant le projet WebsiteDownload ou en utilisant le code donné à la fin de cette rubrique pour créer votre propre projet. Pour plus d’informations et d’instructions, consultez [Examen et exécution de l’exemple d’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="39eae-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="39eae-124">Gestion de la réentrance</span><span class="sxs-lookup"><span data-stu-id="39eae-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="39eae-125">Vous pouvez gérer la réentrance de différentes façons, selon ce que vous voulez que votre application fasse.</span><span class="sxs-lookup"><span data-stu-id="39eae-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="39eae-126">Cette rubrique présente les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="39eae-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="39eae-127">Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="39eae-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="39eae-128">Désactivez le bouton **Démarrer** pendant que l’opération est en cours d’exécution afin que l’utilisateur ne puisse pas l’interrompre.</span><span class="sxs-lookup"><span data-stu-id="39eae-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="39eae-129">Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="39eae-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="39eae-130">Annulez toute opération encore en cours d’exécution quand l’utilisateur choisit le bouton **Démarrer** à nouveau, puis laissez l’opération demandée le plus récemment continuer.</span><span class="sxs-lookup"><span data-stu-id="39eae-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="39eae-131">Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="39eae-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="39eae-132">Autorisez toutes les opérations demandées à s'exécuter de façon asynchrone, mais coordonnez l'affichage de la sortie de sorte que les résultats de chaque opération apparaissent ensemble et dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="39eae-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="39eae-133">Désactiver le bouton Démarrer</span><span class="sxs-lookup"><span data-stu-id="39eae-133">Disable the Start Button</span></span>  
 <span data-ttu-id="39eae-134">Vous pouvez bloquer le bouton **Démarrer** pendant l’exécution d’une opération en désactivant le bouton en haut du gestionnaire d’événements `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="39eae-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="39eae-135">Ensuite, vous pouvez réactiver le bouton depuis un bloc `finally` quand l'opération se termine pour que les utilisateurs puissent exécuter à nouveau l'application.</span><span class="sxs-lookup"><span data-stu-id="39eae-135">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="39eae-136">Le code suivant illustre ces modifications, marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="39eae-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="39eae-137">Vous pouvez ajouter les modifications apportées au code à la fin de cette rubrique, ou vous pouvez télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="39eae-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="39eae-138">Le nom du projet est DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="39eae-138">The project name is DisableStartButton.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 <span data-ttu-id="39eae-139">Suite aux modifications, le bouton ne répond pas pendant que `AccessTheWebAsync` télécharge les sites Web, donc le processus ne peut pas être entré de nouveau.</span><span class="sxs-lookup"><span data-stu-id="39eae-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="39eae-140">Annuler et redémarrer l’opération</span><span class="sxs-lookup"><span data-stu-id="39eae-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="39eae-141">Au lieu de désactiver le bouton **Démarrer**, vous pouvez garder le bouton actif. Toutefois, si l’utilisateur choisit de nouveau ce bouton, annulez l’opération qui est déjà en cours d’exécution et laissez continuer l’opération le plus récemment démarrée.</span><span class="sxs-lookup"><span data-stu-id="39eae-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="39eae-142">Pour plus d’informations sur l’annulation, consultez [Réglage de votre application Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="39eae-142">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="39eae-143">Pour configurer ce scénario, apportez les modifications suivantes au code de base fourni dans [Examen et exécution de l’exemple d’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="39eae-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="39eae-144">Vous pouvez également télécharger l’application finalisée dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="39eae-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="39eae-145">Le nom de ce projet est CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="39eae-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="39eae-146">Déclarez une variable <xref:System.Threading.CancellationTokenSource>, `cts`, qui est dans la portée de toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="39eae-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="39eae-147">Dans `StartButton_Click`, déterminez si une opération est déjà en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="39eae-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="39eae-148">Si la valeur de `cts` est Null, aucune opération n’est active.</span><span class="sxs-lookup"><span data-stu-id="39eae-148">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="39eae-149">Si la valeur n'est pas null, l'opération qui est déjà en cours d'exécution est annulée.</span><span class="sxs-lookup"><span data-stu-id="39eae-149">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="39eae-150">Définissez `cts` sur une autre valeur qui représente le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="39eae-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="39eae-151">À la fin de `StartButton_Click`, le processus en cours est terminé, donc redéfinissez la valeur `cts` sur null.</span><span class="sxs-lookup"><span data-stu-id="39eae-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="39eae-152">Le code suivant illustre toutes les modifications dans `StartButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="39eae-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="39eae-153">Les ajouts sont marqués par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="39eae-153">The additions are marked with asterisks.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 <span data-ttu-id="39eae-154">Dans `AccessTheWebAsync`, apportez les modifications suivantes.</span><span class="sxs-lookup"><span data-stu-id="39eae-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="39eae-155">Ajoutez un paramètre pour accepter le jeton d'annulation en provenance de `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="39eae-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="39eae-156">Utilisez la méthode <xref:System.Net.Http.HttpClient.GetAsync%2A> pour télécharger les sites Web car `GetAsync` accepte un argument <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="39eae-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="39eae-157">Avant d'appeler `DisplayResults` pour afficher les résultats de chaque site Web téléchargé, vérifiez `ct` pour vous assurer que l'opération en cours n'a pas été annulée.</span><span class="sxs-lookup"><span data-stu-id="39eae-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="39eae-158">Le code suivant illustre ces modifications, marquées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="39eae-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 <span data-ttu-id="39eae-159">Si vous choisissez le bouton **Démarrer** plusieurs fois pendant l’exécution de cette application, les résultats produits doivent ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="39eae-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="39eae-160">Pour éliminer les listes partielles, supprimez les commentaires de la première ligne de code dans `StartButton_Click` pour effacer la zone de texte chaque fois que l'utilisateur redémarre l'opération.</span><span class="sxs-lookup"><span data-stu-id="39eae-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="39eae-161">Exécuter plusieurs opérations et mettre la sortie en file d’attente</span><span class="sxs-lookup"><span data-stu-id="39eae-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="39eae-162">Ce troisième exemple est le plus compliqué, car l’application démarre une autre opération asynchrone chaque fois que l’utilisateur choisit le bouton **Démarrer**, et toutes les opérations s’exécutent jusqu’à leur achèvement.</span><span class="sxs-lookup"><span data-stu-id="39eae-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="39eae-163">Toutes les opérations demandées téléchargent des sites web de la liste de façon asynchrone, mais la sortie des opérations est présentée séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="39eae-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="39eae-164">Autrement dit, l’activité de téléchargement réelle est entrelacée, comme le montre la sortie dans [Identification de la réentrance](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), mais la liste des résultats de chaque groupe est présentée séparément.</span><span class="sxs-lookup"><span data-stu-id="39eae-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="39eae-165">Les opérations partagent un <xref:System.Threading.Tasks.Task> global, `pendingWork`, qui sert d'opérateur de contrôle d'appels pour le processus d'affichage.</span><span class="sxs-lookup"><span data-stu-id="39eae-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="39eae-166">Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour télécharger l’exemple, puis exécuter le projet QueueResults.</span><span class="sxs-lookup"><span data-stu-id="39eae-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="39eae-167">La sortie suivante montre le résultat obtenu si l’utilisateur choisit le bouton **Démarrer** une seule fois.</span><span class="sxs-lookup"><span data-stu-id="39eae-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="39eae-168">L’étiquette A indique que le résultat part de la première fois que le bouton **Démarrer** est choisi.</span><span class="sxs-lookup"><span data-stu-id="39eae-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="39eae-169">Les numéros indiquent l'ordre des URL dans la liste des cibles de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="39eae-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="39eae-170">Si l’utilisateur choisit le bouton **Démarrer** trois fois, l’application produit une sortie semblable aux lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="39eae-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="39eae-171">Les lignes d'information qui commencent par un signe dièse (#) suivent la progression de l'application.</span><span class="sxs-lookup"><span data-stu-id="39eae-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="39eae-172">Les groupes B et C démarrent avant que le groupe A ait terminé, mais la sortie de chaque groupe apparaît séparément.</span><span class="sxs-lookup"><span data-stu-id="39eae-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="39eae-173">Toute la sortie du groupe A apparaît en premier, suivie de toute la sortie du groupe B, puis de toute la sortie du groupe C. L’application affiche toujours les groupes dans l’ordre et, pour chaque groupe, elle affiche toujours les informations sur les sites web, dans l’ordre où les URL apparaissent dans la liste des URL.</span><span class="sxs-lookup"><span data-stu-id="39eae-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="39eae-174">Toutefois, vous ne pouvez pas prévoir l'ordre dans lequel les téléchargements se produisent réellement.</span><span class="sxs-lookup"><span data-stu-id="39eae-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="39eae-175">Après le démarrage de plusieurs groupes, les tâches de téléchargement qu'ils génèrent sont toutes actives.</span><span class="sxs-lookup"><span data-stu-id="39eae-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="39eae-176">Vous ne pouvez pas supposer que A-1 sera téléchargé avant B-1 ni que A-1 sera téléchargé avant A-2.</span><span class="sxs-lookup"><span data-stu-id="39eae-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="39eae-177">Définitions globales</span><span class="sxs-lookup"><span data-stu-id="39eae-177">Global Definitions</span></span>  
 <span data-ttu-id="39eae-178">L'exemple de code contient les deux déclarations globales suivantes qui sont visibles à partir de toutes les méthodes.</span><span class="sxs-lookup"><span data-stu-id="39eae-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="39eae-179">La variable `Task`, `pendingWork`, supervise le processus d'affichage et empêche tout groupe d'interrompre l'opération d'affichage d'un autre groupe.</span><span class="sxs-lookup"><span data-stu-id="39eae-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="39eae-180">La variable de caractère `group`, étiquette la sortie de différents groupes pour vérifier que les résultats apparaissent dans l'ordre attendu.</span><span class="sxs-lookup"><span data-stu-id="39eae-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="39eae-181">Gestionnaire d'événements Click</span><span class="sxs-lookup"><span data-stu-id="39eae-181">The Click Event Handler</span></span>  
 <span data-ttu-id="39eae-182">Le gestionnaire d’événements, `StartButton_Click`, incrémente la lettre du groupe chaque fois que l’utilisateur choisit le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="39eae-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="39eae-183">Ensuite, le gestionnaire appelle `AccessTheWebAsync` pour exécuter l'opération de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="39eae-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="39eae-184">Méthode AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="39eae-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="39eae-185">Cet exemple fractionne `AccessTheWebAsync` en deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="39eae-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="39eae-186">La première méthode, `AccessTheWebAsync`, démarre toutes les tâches de téléchargement d'un groupe et configure `pendingWork` pour contrôler le processus d'affichage.</span><span class="sxs-lookup"><span data-stu-id="39eae-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="39eae-187">La méthode utilise une requête LINQ (Language Integrated Query) et <xref:System.Linq.Enumerable.ToArray%2A> pour démarrer toutes les tâches de téléchargement en même temps.</span><span class="sxs-lookup"><span data-stu-id="39eae-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="39eae-188">`AccessTheWebAsync` appelle ensuite `FinishOneGroupAsync` pour attendre la fin de chaque téléchargement et en afficher la longueur.</span><span class="sxs-lookup"><span data-stu-id="39eae-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="39eae-189">`FinishOneGroupAsync` retourne une tâche assignée à `pendingWork` dans `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="39eae-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="39eae-190">Cette valeur empêche toute interruption par une autre opération avant que la tâche ne soit terminée.</span><span class="sxs-lookup"><span data-stu-id="39eae-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="39eae-191">Méthode FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="39eae-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="39eae-192">Cette méthode parcourt les tâches de téléchargement dans un groupe, en attendant chacune d’elles, en affichant la longueur du site web téléchargé et en ajoutant la longueur au total.</span><span class="sxs-lookup"><span data-stu-id="39eae-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="39eae-193">La première instruction dans `FinishOneGroupAsync` utilise `pendingWork` pour vérifier que l’entrée de la méthode n’interfère pas avec une opération qui est déjà dans le processus d’affichage ou qui est déjà en train d’attendre.</span><span class="sxs-lookup"><span data-stu-id="39eae-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="39eae-194">Si une telle opération est en cours, l'opération d'entrée doit attendre son tour.</span><span class="sxs-lookup"><span data-stu-id="39eae-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
 <span data-ttu-id="39eae-195">Vous pouvez exécuter cet exemple en collant les modifications dans le code indiqué dans [Génération de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou vous pouvez suivre les instructions données dans [Téléchargement de l’application](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour télécharger l’exemple, puis exécuter le projet QueueResults.</span><span class="sxs-lookup"><span data-stu-id="39eae-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="39eae-196">Points d'intérêt</span><span class="sxs-lookup"><span data-stu-id="39eae-196">Points of Interest</span></span>  
 <span data-ttu-id="39eae-197">Les lignes d'information qui commencent par un signe dièse (#) dans la sortie clarifient le fonctionnement de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="39eae-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="39eae-198">La sortie affiche les modèles suivants.</span><span class="sxs-lookup"><span data-stu-id="39eae-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="39eae-199">Un groupe peut être démarré pendant qu'un groupe précédent affiche sa sortie, mais l'affichage de la sortie du groupe précédent n'est pas interrompu.</span><span class="sxs-lookup"><span data-stu-id="39eae-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="39eae-200">La tâche `pendingWork` est Null au début de `FinishOneGroupAsync` uniquement pour le groupe A, qui a démarré en premier.</span><span class="sxs-lookup"><span data-stu-id="39eae-200">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="39eae-201">Le groupe A n'a pas encore terminé une expression await quand il atteint `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="39eae-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="39eae-202">Par conséquent, le contrôle n'a pas retourné à `AccessTheWebAsync`, et la première assignation à `pendingWork` ne s'est pas produite.</span><span class="sxs-lookup"><span data-stu-id="39eae-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="39eae-203">Les deux lignes suivantes apparaissent toujours ensemble dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="39eae-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="39eae-204">Le code n'est jamais interrompu entre le démarrage d'une opération de groupe dans `StartButton_Click` et l'affectation d'une tâche pour le groupe à `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="39eae-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="39eae-205">Une fois qu'un groupe entre `StartButton_Click`, l'opération ne termine pas une expression await tant que l'opération n'entre pas `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="39eae-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="39eae-206">Par conséquent, aucune autre opération ne peut obtenir le contrôle au cours de ce segment de code.</span><span class="sxs-lookup"><span data-stu-id="39eae-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="39eae-207">Examen et exécution de l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="39eae-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="39eae-208">Pour mieux comprendre l’exemple d’application, vous pouvez le télécharger, le créer vous-même ou passer en revue le code à la fin de cette rubrique sans implémenter l’application.</span><span class="sxs-lookup"><span data-stu-id="39eae-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39eae-209">Pour exécuter l’exemple comme une application de bureau WPF, Visual Studio version 2012, ou une version ultérieure, et .NET Framework version 4.5, ou une version ultérieure, doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="39eae-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="39eae-210">Téléchargement de l’application</span><span class="sxs-lookup"><span data-stu-id="39eae-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="39eae-211">Téléchargez le fichier compressé dans la rubrique [Exemples Async : la réentrance dans les applications de bureau .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="39eae-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="39eae-212">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39eae-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="39eae-213">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="39eae-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="39eae-214">Accédez au dossier qui contient l’exemple de code décompressé, puis ouvrez le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="39eae-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="39eae-215">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet à modifier, puis choisissez **Définir comme StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="39eae-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="39eae-216">Appuyez sur les touches CTRL+F5 pour générer et exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="39eae-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="39eae-217">Génération de l’application</span><span class="sxs-lookup"><span data-stu-id="39eae-217">Building the App</span></span>  
 <span data-ttu-id="39eae-218">La section suivante fournit le code pour générer l’exemple comme une application WPF.</span><span class="sxs-lookup"><span data-stu-id="39eae-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="39eae-219">Pour générer une application WPF</span><span class="sxs-lookup"><span data-stu-id="39eae-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="39eae-220">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39eae-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="39eae-221">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="39eae-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="39eae-222">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="39eae-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="39eae-223">Dans le volet **Modèles installés**, développez **Visual C#**, puis développez **Windows**.</span><span class="sxs-lookup"><span data-stu-id="39eae-223">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="39eae-224">Dans la liste des types de projets, choisissez **Application WPF**.</span><span class="sxs-lookup"><span data-stu-id="39eae-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="39eae-225">Nommez le projet `WebsiteDownloadWPF`, puis cliquez sur le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="39eae-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="39eae-226">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="39eae-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="39eae-227">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="39eae-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="39eae-228">Si l’onglet n’est pas visible, ouvrez le menu contextuel de MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="39eae-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="39eae-229">Dans la vue **XAML** de MainWindow.xaml, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39eae-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
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
  
     <span data-ttu-id="39eae-230">Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la vue **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="39eae-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="39eae-231">Ajoutez une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="39eae-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="39eae-232">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="39eae-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="39eae-233">Dans MainWindow.xaml.cs, remplacez le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39eae-233">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    // Add the following using directives, and add a reference for System.Net.Http.  
    using System.Net.Http;  
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="39eae-234">Appuyez sur les touches CTRL+F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="39eae-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="39eae-235">Apportez les modifications indiquées dans [Désactiver le bouton Démarrer](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Annuler et redémarrer l’opération](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ou [Exécuter plusieurs opérations et mettre la sortie en file d’attente](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pour gérer la réentrance.</span><span class="sxs-lookup"><span data-stu-id="39eae-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39eae-236">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39eae-236">See Also</span></span>  
 [<span data-ttu-id="39eae-237">Procédure pas à pas : accès au web avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="39eae-237">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="39eae-238">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="39eae-238">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
