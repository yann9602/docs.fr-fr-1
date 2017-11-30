---
title: "Procédure pas à pas : accès au web avec Async et Await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="ce923-102">Procédure pas à pas : accès au web avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ce923-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="ce923-103">Vous pouvez écrire des programmes asynchrones plus facilement et intuitivement en utilisant les fonctionnalités async/await.</span><span class="sxs-lookup"><span data-stu-id="ce923-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="ce923-104">Vous pouvez écrire du code asynchrone qui ressemble au code synchrone et laisser le compilateur gérer les difficiles fonctions de rappel et continuations qu’implique généralement le code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ce923-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="ce923-105">Pour plus d’informations sur la fonctionnalité Async, consultez [Programmation asynchrone avec Async et Await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="ce923-106">Cette procédure pas à pas commence avec une application Windows Presentation Foundation (WPF) synchrone qui additionne le nombre d’octets figurant dans une liste de sites web.</span><span class="sxs-lookup"><span data-stu-id="ce923-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="ce923-107">La procédure pas à pas convertit ensuite l’application en solution asynchrone en utilisant les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ce923-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="ce923-108">Si vous ne souhaitez pas générer les applications vous-même, vous pouvez télécharger « Exemple Async : Accès à la procédure web (C# et Visual Basic) » à partir des [exemples de code de développeur](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="ce923-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="ce923-109">Dans cette procédure pas à pas, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce923-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="ce923-110">Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="ce923-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="ce923-111">Pour concevoir une simple fenêtre MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="ce923-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="ce923-112">Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="ce923-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="ce923-113">Pour ajouter les directives using nécessaires</span><span class="sxs-lookup"><span data-stu-id="ce923-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="ce923-114">Pour créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="ce923-115">Pour tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="ce923-116">Pour convertir GetURLContents en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="ce923-117">Pour convertir SumPageSizes en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="ce923-118">Pour convertir startButton_Click en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="ce923-119">Pour tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="ce923-120">Pour remplacer la méthode GetURLContentsAsync par une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce923-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="ce923-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce923-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="ce923-122">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ce923-122">Prerequisites</span></span>  
 <span data-ttu-id="ce923-123">Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ce923-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="ce923-124">Pour plus d’informations, consultez le [site web de Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="ce923-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="ce923-125"><a name="CreateWPFApp"></a> Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="ce923-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="ce923-126">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce923-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ce923-127">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="ce923-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="ce923-128">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ce923-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ce923-129">Dans le volet **Modèles installés**, choisissez Visual C#, puis **Application WPF** dans la liste des types de projets.</span><span class="sxs-lookup"><span data-stu-id="ce923-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="ce923-130">Dans la zone de texte **Nom**, entrez `AsyncExampleWPF`, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce923-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="ce923-131">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="ce923-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="ce923-132"><a name="MainWindow"></a> Pour concevoir une simple fenêtre MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="ce923-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="ce923-133">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="ce923-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="ce923-134">Si la fenêtre **Boîte à outils** n’est pas visible, ouvrez le menu **Affichage**, puis choisissez **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="ce923-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="ce923-135">Ajoutez un contrôle **Button** et un contrôle **TextBox** à la fenêtre **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="ce923-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="ce923-136">Mettez en surbrillance le contrôle **TextBox** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce923-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="ce923-137">Affectez la valeur `resultsTextBox` à la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="ce923-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="ce923-138">Affectez la valeur 250 à la propriété **Height**.</span><span class="sxs-lookup"><span data-stu-id="ce923-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="ce923-139">Affectez la valeur 500 à la propriété **Width**.</span><span class="sxs-lookup"><span data-stu-id="ce923-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="ce923-140">Sous l’onglet **Texte**, spécifiez une police à espacement fixe, comme Lucida Console ou Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="ce923-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="ce923-141">Mettez en surbrillance le contrôle **Button** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce923-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="ce923-142">Affectez la valeur `startButton` à la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="ce923-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="ce923-143">Remplacez la valeur **Button** de la propriété **Content** par **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce923-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="ce923-144">Placez la zone de texte et le bouton de manière à ce qu’ils apparaissent tous les deux dans la fenêtre **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="ce923-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="ce923-145">Pour plus d’informations sur le concepteur XAML WPF, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ce923-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="ce923-146"><a name="AddRef"></a> Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="ce923-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="ce923-147">Dans l’**Explorateur de solutions**, mettez en surbrillance le nom de votre projet.</span><span class="sxs-lookup"><span data-stu-id="ce923-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="ce923-148">Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="ce923-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="ce923-149">La boîte de dialogue **Gestionnaire de références** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ce923-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="ce923-150">En haut de la boîte de dialogue, vérifiez que votre projet cible .NET Framework 4.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ce923-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="ce923-151">Dans la zone **Assemblys**, choisissez **Framework** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ce923-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="ce923-152">Dans la liste de noms, cochez la case **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="ce923-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="ce923-153">Choisissez le bouton **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ce923-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="ce923-154"><a name="usingDir"></a> Pour ajouter les directives using nécessaires</span><span class="sxs-lookup"><span data-stu-id="ce923-154"><a name="usingDir"></a> To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="ce923-155">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="ce923-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="ce923-156">Ajoutez les directives `using` suivantes en haut du fichier de code, si elles ne sont pas déjà présentes.</span><span class="sxs-lookup"><span data-stu-id="ce923-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="ce923-157"><a name="synchronous"></a> Pour créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="ce923-158">Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le bouton **Démarrer** pour créer le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="ce923-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="ce923-159">Dans MainWindow.xaml.cs, copiez le code suivant dans le corps de `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="ce923-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="ce923-160">Le code appelle la méthode qui pilote l'application, `SumPageSizes`, et affiche un message quand le contrôle redevient `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ce923-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="ce923-161">Le code de la solution synchrone contient les quatre méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce923-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="ce923-162">`SumPageSizes`, qui obtient la liste des URL des pages web à partir de `SetUpURLList`, puis qui appelle `GetURLContents` et `DisplayResults` pour traiter chaque URL.</span><span class="sxs-lookup"><span data-stu-id="ce923-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="ce923-163">`SetUpURLList`, qui dresse et retourne la liste des adresses web.</span><span class="sxs-lookup"><span data-stu-id="ce923-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="ce923-164">`GetURLContents`, qui télécharge le contenu de chaque site web et retourne le contenu sous la forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="ce923-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="ce923-165">`DisplayResults`, qui affiche le nombre d'octets dans le tableau d'octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="ce923-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="ce923-166">Copiez les quatre méthodes suivantes, puis collez-les sous le gestionnaire d’événements `startButton_Click` dans MainWindow.xaml.cs :</span><span class="sxs-lookup"><span data-stu-id="ce923-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290136.aspx",  
            "http://msdn.microsoft.com/library/ee256749.aspx",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="ce923-167"><a name="testSynch"></a> Pour tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="ce923-168">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="ce923-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ce923-169">Une sortie semblable à la liste suivante doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="ce923-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     <span data-ttu-id="ce923-170">Notez que quelques secondes suffisent pour afficher les nombres.</span><span class="sxs-lookup"><span data-stu-id="ce923-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="ce923-171">Pendant ce temps, le thread d'interface utilisateur est bloqué alors qu'il attend que les ressources demandées se téléchargent.</span><span class="sxs-lookup"><span data-stu-id="ce923-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="ce923-172">Par conséquent, vous ne pouvez pas déplacer, agrandir, réduire ni même fermer la fenêtre d’affichage une fois que vous avez choisi le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce923-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="ce923-173">Ces efforts échouent jusqu'à ce que les nombres d'octets commencent à apparaître.</span><span class="sxs-lookup"><span data-stu-id="ce923-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="ce923-174">Si un site web ne répond pas, vous n'avez aucune indication précise sur le site en question qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="ce923-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="ce923-175">Il est même difficile d'arrêter l'attente et de fermer le programme.</span><span class="sxs-lookup"><span data-stu-id="ce923-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="ce923-176"><a name="GetURLContents"></a> Pour convertir GetURLContents en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="ce923-177">Pour convertir la solution synchrone en solution asynchrone, `GetURLContents` est le meilleur point de départ, car les appels à la méthode <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> et à la méthode <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> se trouvent là où l’application accède au web.</span><span class="sxs-lookup"><span data-stu-id="ce923-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="ce923-178">Le .NET Framework facilite la conversion en fournissant des versions asynchrones des deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="ce923-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="ce923-179">Pour plus d'informations sur les méthodes utilisées dans `GetURLContents`, consultez <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="ce923-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce923-180">Quand vous suivez les étapes décrites dans cette procédure pas à pas, plusieurs erreurs de compilation apparaissent.</span><span class="sxs-lookup"><span data-stu-id="ce923-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="ce923-181">Vous pouvez les ignorer et poursuivre la procédure.</span><span class="sxs-lookup"><span data-stu-id="ce923-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="ce923-182">Remplacez la méthode appelée à la troisième ligne de `GetURLContents` dont la valeur est `GetResponse` par la méthode <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchrone basée sur les tâches.</span><span class="sxs-lookup"><span data-stu-id="ce923-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="ce923-183">`GetResponseAsync` retourne un <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ce923-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ce923-184">Dans ce cas, la *variable de retour de tâche*, `TResult`, est de type <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="ce923-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ce923-185">La tâche est une promesse de produire un objet `WebResponse` réel une fois que les données demandées ont été téléchargées et que la tâche s'est exécutée entièrement.</span><span class="sxs-lookup"><span data-stu-id="ce923-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="ce923-186">Pour récupérer la valeur `WebResponse` de la tâche, appliquez un opérateur [await](../../../../csharp/language-reference/keywords/await.md) à l’appel à `GetResponseAsync`, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ce923-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="ce923-187">L’opérateur `await` suspend l’exécution de la méthode actuelle, `GetURLContents`, jusqu’à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="ce923-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="ce923-188">Entre-temps, le contrôle retourne à l'appelant de la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="ce923-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="ce923-189">Dans cet exemple, la méthode actuelle est `GetURLContents` et l'appelant est `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="ce923-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="ce923-190">Quand la tâche est terminée, l'objet `WebResponse` promis est produit sous forme de valeur de la tâche attendue et assigné à la variable `response`.</span><span class="sxs-lookup"><span data-stu-id="ce923-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="ce923-191">L'instruction précédente peut être divisée en deux instructions suivantes pour clarifier ce qui se passe.</span><span class="sxs-lookup"><span data-stu-id="ce923-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="ce923-192">L'appel à `webReq.GetResponseAsync` retourne un `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="ce923-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="ce923-193">Un opérateur await est alors appliqué à la tâche pour récupérer la valeur `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="ce923-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="ce923-194">Si votre méthode async a un travail à effectuer qui ne dépend pas de la complétion de la tâche, elle peut poursuivre ce travail entre ces deux instructions, après l’appel à la méthode async et avant l’application de l’opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="ce923-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="ce923-195">Pour obtenir des exemples, consultez [Guide pratique pour effectuer plusieurs requêtes web en parallèle en utilisant async et await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) et [Guide pratique pour étendre la procédure pas à pas Async à l’aide de Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="ce923-196">Comme vous avez ajouté l’opérateur `await` à l’étape précédente, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="ce923-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="ce923-197">L’opérateur peut être utilisé uniquement dans les méthodes marquées avec le modificateur [async](../../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ce923-198">Ignorez l'erreur quand que vous répétez les étapes de conversion pour remplacer l'appel à `CopyTo` par un appel à `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="ce923-199">Remplacez le nom de la méthode appelée par <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce923-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="ce923-200">La méthode `CopyTo` ou `CopyToAsync` copie les octets dans son argument, `content`, et ne retourne pas de valeur significative.</span><span class="sxs-lookup"><span data-stu-id="ce923-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="ce923-201">Dans la version synchrone, l'appel à `CopyTo` est une simple instruction qui ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="ce923-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="ce923-202">La version asynchrone, `CopyToAsync`, retourne un <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="ce923-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="ce923-203">La tâche fonctionne comme Task(void) et permet à la méthode d'être attendue.</span><span class="sxs-lookup"><span data-stu-id="ce923-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="ce923-204">Appliquez `Await` ou `await` à l'appel à `CopyToAsync`, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ce923-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="ce923-205">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce923-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="ce923-206">Tout ce qui reste à faire dans `GetURLContents` consiste à adapter la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ce923-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="ce923-207">L’opérateur `await` peut être utilisé uniquement dans les méthodes marquées avec le modificateur [async](../../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ce923-208">Ajoutez le modificateur pour marquer la méthode en tant que *méthode async*, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ce923-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="ce923-209">Le type de retour d'une méthode async peut uniquement être <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `void` en C#.</span><span class="sxs-lookup"><span data-stu-id="ce923-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="ce923-210">En règle générale, le type de retour `void` est utilisé uniquement dans un gestionnaire d’événements asynchrones, où `void` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ce923-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="ce923-211">Dans d’autres cas, vous utilisez `Task(T)` si la méthode exécutée comporte une instruction [return](../../../../csharp/language-reference/keywords/return.md) qui retourne une valeur de type T et vous utilisez `Task` si la méthode exécutée ne retourne aucune valeur significative.</span><span class="sxs-lookup"><span data-stu-id="ce923-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="ce923-212">Vous pouvez considérer que le type de retour `Task` signifie Task(void).</span><span class="sxs-lookup"><span data-stu-id="ce923-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="ce923-213">Pour plus d’informations, consultez [Types de retour Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="ce923-214">La méthode `GetURLContents` comporte une instruction return et l'instruction retourne un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="ce923-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="ce923-215">Ainsi, le type de retour de la version asynchrone est Task(T), où T est un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="ce923-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="ce923-216">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="ce923-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="ce923-217">Remplacez le type de retour par `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="ce923-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="ce923-218">Par convention, les méthodes asynchrones portent des noms qui se terminent par « Async ». Renommez alors la méthode `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="ce923-219">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="ce923-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="ce923-220">Avec ces quelques modifications, la conversion de `GetURLContents` en méthode asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="ce923-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="ce923-221"><a name="SumPageSizes"></a> Pour convertir SumPageSizes en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-221"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="ce923-222">Répétez les étapes de la procédure précédente pour `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="ce923-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="ce923-223">Tout d'abord, modifiez l'appel à `GetURLContents` en appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ce923-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="ce923-224">Remplacez le nom de la méthode appelée `GetURLContents` par `GetURLContentsAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="ce923-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="ce923-225">Appliquez `await` à la tâche que `GetURLContentsAsync` retourne pour obtenir la valeur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="ce923-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="ce923-226">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="ce923-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="ce923-227">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce923-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="ce923-228">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="ce923-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="ce923-229">Marquez la méthode avec le modificateur `async`.</span><span class="sxs-lookup"><span data-stu-id="ce923-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="ce923-230">Ajoutez « Async » au nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ce923-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="ce923-231">Il n'existe aucune variable de retour de tâche, T, cette fois, car `SumPageSizesAsync` ne retourne pas de valeur pour T. (La méthode ne comporte pas d’instruction `return`.) Toutefois, la méthode doit retourner un `Task` pour pouvoir être attendue.</span><span class="sxs-lookup"><span data-stu-id="ce923-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="ce923-232">Par conséquent, remplacez le type de retour de la méthode `void` par `Task`.</span><span class="sxs-lookup"><span data-stu-id="ce923-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="ce923-233">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="ce923-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="ce923-234">La conversion de `SumPageSizes` en `SumPageSizesAsync` est terminée.</span><span class="sxs-lookup"><span data-stu-id="ce923-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="ce923-235"><a name="startButton"></a> Pour convertir startButton_Click en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-235"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="ce923-236">Dans le gestionnaire d'événements, remplacez le nom de la méthode appelée `SumPageSizes` par `SumPageSizesAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="ce923-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="ce923-237">Étant donné que `SumPageSizesAsync` est une méthode async, modifiez le code dans le gestionnaire d'événements de sorte à attendre le résultat.</span><span class="sxs-lookup"><span data-stu-id="ce923-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="ce923-238">L'appel à `SumPageSizesAsync` reflète l'appel à `CopyToAsync` dans `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="ce923-239">L'appel retourne un `Task`, et non un `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="ce923-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="ce923-240">Comme dans les procédures précédentes, vous pouvez convertir l'appel à l'aide d'une ou deux instructions.</span><span class="sxs-lookup"><span data-stu-id="ce923-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="ce923-241">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="ce923-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="ce923-242">Pour empêcher une nouvelle entrée accidentelle de l’opération, ajoutez l’instruction suivante en haut de `startButton_Click` pour désactiver le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce923-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="ce923-243">Vous pouvez réactiver le bouton à la fin du gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="ce923-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="ce923-244">Pour plus d’informations sur la réentrance, consultez [Gestion de la réentrance dans les applications asynchrones (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ce923-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="ce923-245">Enfin, ajoutez le modificateur `async` à la déclaration pour que le gestionnaire d’événements puisse attendre `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="ce923-246">En règle générale, les noms des gestionnaires d'événements ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="ce923-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="ce923-247">Le type de retour n’est pas remplacé par `Task`, car les gestionnaires d’événements doivent retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="ce923-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="ce923-248">La conversion du projet depuis un traitement synchrone vers un traitement asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="ce923-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="ce923-249"><a name="testAsynch"></a> Pour tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="ce923-249"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="ce923-250">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="ce923-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="ce923-251">Une sortie semblable à la sortie de la solution synchrone doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="ce923-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="ce923-252">En revanche, observez les différences ci-après.</span><span class="sxs-lookup"><span data-stu-id="ce923-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="ce923-253">Les résultats ne se produisent pas tous en même temps, une fois le traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="ce923-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="ce923-254">Par exemple, les deux programmes contiennent une ligne dans `startButton_Click` qui efface la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="ce923-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="ce923-255">L’objectif est d’effacer la zone de texte entre les exécutions si vous choisissez le bouton **Démarrer** une deuxième fois, une fois qu’un jeu de résultats est apparu.</span><span class="sxs-lookup"><span data-stu-id="ce923-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="ce923-256">Dans la version synchrone, la zone de texte s’efface juste avant que les nombres n’apparaissent pour la deuxième fois, quand les téléchargements sont terminés et que le thread d’interface utilisateur est libre d’effectuer autre chose.</span><span class="sxs-lookup"><span data-stu-id="ce923-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="ce923-257">Dans la version asynchrone, la zone de texte s’efface immédiatement après avoir choisi le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce923-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="ce923-258">Plus important encore, le thread d'interface utilisateur n'est pas bloqué pendant les téléchargements.</span><span class="sxs-lookup"><span data-stu-id="ce923-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="ce923-259">Vous pouvez déplacer ou redimensionner la fenêtre pendant le téléchargement, la comptabilisation et l'affichage des ressources web.</span><span class="sxs-lookup"><span data-stu-id="ce923-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="ce923-260">Si l’un des sites web est lent ou ne répond pas, vous pouvez annuler l’opération en choisissant le bouton **Fermer** (le x dans le champ rouge situé dans le coin supérieur droit).</span><span class="sxs-lookup"><span data-stu-id="ce923-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="ce923-261"><a name="GetURLContentsAsync"></a> Pour remplacer la méthode GetURLContentsAsync par une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce923-261"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="ce923-262">Le .NET Framework 4.5 propose de nombreuses méthodes async que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="ce923-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="ce923-263">L'une d'entre elles, la méthode <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, convient parfaitement à cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ce923-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="ce923-264">Vous pouvez l'utiliser à la place de la méthode `GetURLContentsAsync` que vous avez créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="ce923-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="ce923-265">La première étape consiste à créer un objet `HttpClient` dans la méthode `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="ce923-266">Ajoutez la déclaration suivante au début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ce923-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="ce923-267">Dans `SumPageSizesAsync,`, remplacez l'appel à votre méthode `GetURLContentsAsync` par un appel à la méthode `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="ce923-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="ce923-268">Supprimez ou commentez la méthode `GetURLContentsAsync` que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="ce923-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="ce923-269">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="ce923-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ce923-270">Le comportement de cette version du projet doit correspondre à celui décrit par la procédure « Pour tester la solution asynchrone » mais avec encore moins d'efforts de votre part.</span><span class="sxs-lookup"><span data-stu-id="ce923-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="ce923-271"><a name="BKMK_CompleteCodeExamples"></a> Exemple</span><span class="sxs-lookup"><span data-stu-id="ce923-271"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="ce923-272">Le code suivant inclut l'exemple complet de la conversion d'une solution synchrone en solution asynchrone à l'aide de la méthode `GetURLContentsAsync` asynchrone que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="ce923-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="ce923-273">Remarquez qu’il ressemble fortement à la solution synchrone d’origine.</span><span class="sxs-lookup"><span data-stu-id="ce923-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ce923-274">Le code suivant inclut l'exemple complet de la solution qui utilise la méthode `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="ce923-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce923-275">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce923-275">See Also</span></span>  
 [<span data-ttu-id="ce923-276">Exemple Async : L’accès à la procédure Web (c# et Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce923-276">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="ce923-277">async</span><span class="sxs-lookup"><span data-stu-id="ce923-277">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="ce923-278">await</span><span class="sxs-lookup"><span data-stu-id="ce923-278">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="ce923-279">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ce923-279">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="ce923-280">Types de retour async (C#)</span><span class="sxs-lookup"><span data-stu-id="ce923-280">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="ce923-281">Programmation asynchrone basé sur des tâches (TAP)</span><span class="sxs-lookup"><span data-stu-id="ce923-281">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="ce923-282">Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="ce923-282">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="ce923-283">Guide pratique : effectuer plusieurs requêtes web en parallèle avec async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="ce923-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
