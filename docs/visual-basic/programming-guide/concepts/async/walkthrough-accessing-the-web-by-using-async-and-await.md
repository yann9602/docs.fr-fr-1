---
title: "Accès Web avec Async et Await (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
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
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="90d91-102">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90d91-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="90d91-103">Vous pouvez écrire des programmes asynchrones plus facilement et intuitivement en utilisant les fonctionnalités qui ont été introduites dans [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span><span class="sxs-lookup"><span data-stu-id="90d91-103">You can write asynchronous programs more easily and intuitively by using features that were introduced in [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span></span> <span data-ttu-id="90d91-104">Vous pouvez écrire du code asynchrone qui ressemble au code synchrone et laisser le compilateur gérer les difficiles fonctions de rappel et continuations qu’implique généralement le code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="90d91-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="90d91-105">Pour plus d’informations sur la fonctionnalité Async, consultez [programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="90d91-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="90d91-106">Cette procédure pas à pas commence avec une application Windows Presentation Foundation (WPF) synchrone qui additionne le nombre d’octets figurant dans une liste de sites web.</span><span class="sxs-lookup"><span data-stu-id="90d91-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="90d91-107">La procédure pas à pas convertit ensuite l’application en solution asynchrone en utilisant les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="90d91-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="90d91-108">Si vous ne souhaitez pas générer les applications vous-même, vous pouvez télécharger « exemple Async : accès à la procédure Web (c# et Visual Basic) » à partir de [exemples de Code développeur](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="90d91-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="90d91-109">Dans cette procédure pas à pas, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="90d91-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="90d91-110">Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="90d91-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="90d91-111">Pour concevoir un MainWindow WPF simple</span><span class="sxs-lookup"><span data-stu-id="90d91-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="90d91-112">Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="90d91-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="90d91-113">Pour ajouter les instructions Imports nécessaires</span><span class="sxs-lookup"><span data-stu-id="90d91-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="90d91-114">Pour créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="90d91-115">Pour tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="90d91-116">Pour convertir une méthode asynchrone GetURLContents</span><span class="sxs-lookup"><span data-stu-id="90d91-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="90d91-117">Pour convertir une méthode asynchrone SumPageSizes</span><span class="sxs-lookup"><span data-stu-id="90d91-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="90d91-118">Pour convertir une méthode asynchrone startButton_Click</span><span class="sxs-lookup"><span data-stu-id="90d91-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="90d91-119">Pour tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="90d91-120">Pour remplacer la méthode GetURLContentsAsync avec une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90d91-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="90d91-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="90d91-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="90d91-122">Prérequis</span><span class="sxs-lookup"><span data-stu-id="90d91-122">Prerequisites</span></span>  
 <span data-ttu-id="90d91-123">Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="90d91-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="90d91-124">Pour plus d’informations, consultez la [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="90d91-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="90d91-125"><a name="CreateWPFApp"></a>Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="90d91-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="90d91-126">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90d91-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="90d91-127">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="90d91-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="90d91-128">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="90d91-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="90d91-129">Dans le **modèles installés** volet, choisissez Visual Basic, puis **Application WPF** dans la liste des types de projet.</span><span class="sxs-lookup"><span data-stu-id="90d91-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="90d91-130">Dans le **nom** texte, entrez `AsyncExampleWPF`, puis choisissez le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="90d91-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="90d91-131">Le nouveau projet s’affiche dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="90d91-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="90d91-132"><a name="MainWindow"></a>Pour concevoir un MainWindow WPF simple</span><span class="sxs-lookup"><span data-stu-id="90d91-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="90d91-133">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="90d91-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="90d91-134">Si le **boîte à outils** fenêtre n’est pas visible, ouvrez le **affichage** menu, puis choisissez **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="90d91-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="90d91-135">Ajouter un **bouton** contrôle et un **zone de texte** le contrôle à la **MainWindow** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="90d91-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="90d91-136">Mettez en surbrillance le **zone de texte** contrôle et, dans le **propriétés** fenêtre, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="90d91-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="90d91-137">Définir le **nom** propriété `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="90d91-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="90d91-138">Définir le **hauteur** propriété à 250.</span><span class="sxs-lookup"><span data-stu-id="90d91-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="90d91-139">Définir le **largeur** propriété à 500.</span><span class="sxs-lookup"><span data-stu-id="90d91-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="90d91-140">Sur le **texte** , spécifiez une police à espacement fixe, telles que Lucida Console ou Global à espacement fixe.</span><span class="sxs-lookup"><span data-stu-id="90d91-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="90d91-141">Mettez en surbrillance le **bouton** contrôle et, dans le **propriétés** fenêtre, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="90d91-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="90d91-142">Définir le **nom** propriété `startButton`.</span><span class="sxs-lookup"><span data-stu-id="90d91-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="90d91-143">Modifiez la valeur de la **contenu** propriété **bouton** à **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="90d91-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="90d91-144">Placez la zone de texte et le bouton afin que les deux s’affichent dans le **MainWindow** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="90d91-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="90d91-145">Pour plus d’informations sur le concepteur XAML WPF, consultez [création d’une interface utilisateur à l’aide du concepteur XAML](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="90d91-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="90d91-146"><a name="AddRef"></a>Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="90d91-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="90d91-147">Dans **l’Explorateur de solutions**, mettez en surbrillance le nom de votre projet.</span><span class="sxs-lookup"><span data-stu-id="90d91-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="90d91-148">Dans la barre de menus, choisissez **projet**, **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="90d91-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="90d91-149">Le **Gestionnaire de références** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="90d91-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="90d91-150">En haut de la boîte de dialogue, vérifiez que votre projet cible le .NET Framework 4.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="90d91-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="90d91-151">Dans le **assemblys** zone, choisissez **Framework** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="90d91-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="90d91-152">Dans la liste des noms, sélectionnez le **System.Net.Http** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="90d91-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="90d91-153">Choisissez le **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="90d91-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="90d91-154"><a name="ImportsState"></a>Pour ajouter les instructions Imports nécessaires</span><span class="sxs-lookup"><span data-stu-id="90d91-154"><a name="ImportsState"></a> To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="90d91-155">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.vb, puis choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="90d91-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="90d91-156">Ajoutez le code suivant `Imports` au début du fichier de code s’ils ne sont pas déjà présents.</span><span class="sxs-lookup"><span data-stu-id="90d91-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="90d91-157"><a name="synchronous"></a>Pour créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="90d91-158">Dans la fenêtre de conception, MainWindow.xaml, double-cliquez sur le **Démarrer** pour créer le `startButton_Click` MainWindow.xaml.vb Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="90d91-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="90d91-159">Dans MainWindow.xaml.vb, copiez le code suivant dans le corps de `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="90d91-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="90d91-160">Le code appelle la méthode qui pilote l'application, `SumPageSizes`, et affiche un message quand le contrôle redevient `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="90d91-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="90d91-161">Le code de la solution synchrone contient les quatre méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="90d91-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="90d91-162">`SumPageSizes`, qui obtient la liste des URL des pages web à partir de `SetUpURLList`, puis qui appelle `GetURLContents` et `DisplayResults` pour traiter chaque URL.</span><span class="sxs-lookup"><span data-stu-id="90d91-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="90d91-163">`SetUpURLList`, qui dresse et retourne la liste des adresses web.</span><span class="sxs-lookup"><span data-stu-id="90d91-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="90d91-164">`GetURLContents`, qui télécharge le contenu de chaque site web et retourne le contenu sous la forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="90d91-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="90d91-165">`DisplayResults`, qui affiche le nombre d'octets dans le tableau d'octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="90d91-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="90d91-166">Copiez les quatre méthodes suivantes et collez-les dans le `startButton_Click` MainWindow.xaml.vb Gestionnaire d’événements :</span><span class="sxs-lookup"><span data-stu-id="90d91-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="90d91-167"><a name="testSynch"></a>Pour tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="90d91-168">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="90d91-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="90d91-169">Une sortie semblable à la liste suivante doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="90d91-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="90d91-170">Notez que quelques secondes suffisent pour afficher les nombres.</span><span class="sxs-lookup"><span data-stu-id="90d91-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="90d91-171">Pendant ce temps, le thread d'interface utilisateur est bloqué alors qu'il attend que les ressources demandées se téléchargent.</span><span class="sxs-lookup"><span data-stu-id="90d91-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="90d91-172">Par conséquent, vous ne pouvez pas déplacer, agrandir, réduire ou même de fermer la fenêtre d’affichage après avoir choisi le **Démarrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="90d91-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="90d91-173">Ces efforts échouent jusqu'à ce que les nombres d'octets commencent à apparaître.</span><span class="sxs-lookup"><span data-stu-id="90d91-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="90d91-174">Si un site web ne répond pas, vous n'avez aucune indication précise sur le site en question qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="90d91-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="90d91-175">Il est même difficile d'arrêter l'attente et de fermer le programme.</span><span class="sxs-lookup"><span data-stu-id="90d91-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="90d91-176"><a name="GetURLContents"></a>Pour convertir une méthode asynchrone GetURLContents</span><span class="sxs-lookup"><span data-stu-id="90d91-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="90d91-177">Pour convertir la solution synchrone en une solution asynchrone, le meilleur endroit pour démarrer est dans `GetURLContents` , car les appels à la <xref:System.Net.HttpWebRequest>(méthode) <xref:System.Net.HttpWebRequest.GetResponse%2A>et le <xref:System.IO.Stream>(méthode) <xref:System.IO.Stream.CopyTo%2A>sont où l’application accède au web.</xref:System.IO.Stream.CopyTo%2A> </xref:System.IO.Stream> </xref:System.Net.HttpWebRequest.GetResponse%2A> </xref:System.Net.HttpWebRequest></span><span class="sxs-lookup"><span data-stu-id="90d91-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="90d91-178">Le .NET Framework facilite la conversion en fournissant des versions asynchrones des deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="90d91-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="90d91-179">Pour plus d’informations sur les méthodes qui sont utilisées dans `GetURLContents`, consultez la page <xref:System.Net.WebRequest>.</xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="90d91-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90d91-180">Quand vous suivez les étapes décrites dans cette procédure pas à pas, plusieurs erreurs de compilation apparaissent.</span><span class="sxs-lookup"><span data-stu-id="90d91-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="90d91-181">Vous pouvez les ignorer et poursuivre la procédure.</span><span class="sxs-lookup"><span data-stu-id="90d91-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="90d91-182">Modifiez la méthode qui est appelée dans la troisième ligne de `GetURLContents` de `GetResponse` asynchrone, basée sur les tâches <xref:System.Net.WebRequest.GetResponseAsync%2A>méthode.</xref:System.Net.WebRequest.GetResponseAsync%2A></span><span class="sxs-lookup"><span data-stu-id="90d91-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="90d91-183">`GetResponseAsync`Retourne un <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="90d91-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="90d91-184">Dans ce cas, le *variable de retour de tâches*, `TResult`, a un type <xref:System.Net.WebResponse>.</xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="90d91-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="90d91-185">La tâche est une promesse de produire un objet `WebResponse` réel une fois que les données demandées ont été téléchargées et que la tâche s'est exécutée entièrement.</span><span class="sxs-lookup"><span data-stu-id="90d91-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="90d91-186">Pour récupérer le `WebResponse` à partir de la tâche, appliquez une [Await](../../../../visual-basic/language-reference/operators/await-operator.md) opérateur à l’appel à `GetResponseAsync`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="90d91-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="90d91-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="90d91-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="90d91-188">Le `Await` opérateur suspend l’exécution de la méthode actuelle, `GetURLContents`, jusqu'à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="90d91-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="90d91-189">Entre-temps, le contrôle retourne à l'appelant de la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="90d91-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="90d91-190">Dans cet exemple, la méthode actuelle est `GetURLContents` et l'appelant est `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="90d91-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="90d91-191">Quand la tâche est terminée, l'objet `WebResponse` promis est produit sous forme de valeur de la tâche attendue et assigné à la variable `response`.</span><span class="sxs-lookup"><span data-stu-id="90d91-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<span data-ttu-id="90d91-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="90d91-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="90d91-193">L'appel à `webReq.GetResponseAsync` retourne un `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="90d91-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="90d91-194">Une `Await` opérateur est appliqué à la tâche pour récupérer le `WebResponse` valeur.</span><span class="sxs-lookup"><span data-stu-id="90d91-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  <span data-ttu-id="90d91-195">Étant donné que vous avez ajouté le `Await` opérateur à l’étape précédente, une erreur de compilation apparaît.</span><span class="sxs-lookup"><span data-stu-id="90d91-195">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="90d91-196">L’opérateur peut être utilisé uniquement dans les méthodes marquées avec le [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="90d91-196">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="90d91-197">Ignorez l'erreur quand que vous répétez les étapes de conversion pour remplacer l'appel à `CopyTo` par un appel à `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-197">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="90d91-198">Modifier le nom de la méthode est appelée pour <xref:System.IO.Stream.CopyToAsync%2A>.</xref:System.IO.Stream.CopyToAsync%2A></span><span class="sxs-lookup"><span data-stu-id="90d91-198">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="90d91-199">La méthode `CopyTo` ou `CopyToAsync` copie les octets dans son argument, `content`, et ne retourne pas de valeur significative.</span><span class="sxs-lookup"><span data-stu-id="90d91-199">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="90d91-200">Dans la version synchrone, l'appel à `CopyTo` est une simple instruction qui ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="90d91-200">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="90d91-201">La version asynchrone, `CopyToAsync`, renvoie une <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="90d91-201">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="90d91-202">La tâche fonctionne comme Task(void) et permet à la méthode d’être attendue.</span><span class="sxs-lookup"><span data-stu-id="90d91-202">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="90d91-203">Appliquez `Await` ou `await` à l'appel à `CopyToAsync`, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="90d91-203">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="90d91-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="90d91-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
         <span data-ttu-id="90d91-205">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="90d91-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
<span data-ttu-id="90d91-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="90d91-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="90d91-207">Tout ce qui reste à faire dans `GetURLContents` consiste à adapter la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="90d91-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="90d91-208">Vous pouvez utiliser la `Await` opérateur uniquement dans les méthodes marquées avec le [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="90d91-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="90d91-209">Ajoutez le modificateur pour marquer la méthode comme un *méthode async*, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="90d91-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
<span data-ttu-id="90d91-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="90d91-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
5.  <span data-ttu-id="90d91-211">Le type de retour d’une méthode asynchrone peut être uniquement <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="90d91-211">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="90d91-212">En Visual Basic, la méthode doit être un `Function` qui retourne un `Task` ou `Task(Of T)`, ou la méthode doit être un `Sub`.</span><span class="sxs-lookup"><span data-stu-id="90d91-212">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="90d91-213">En règle générale, un `Sub` méthode est utilisée uniquement dans un gestionnaire d’événements asynchrones, où `Sub` est requis.</span><span class="sxs-lookup"><span data-stu-id="90d91-213">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="90d91-214">Dans d’autres cas, vous utilisez `Task(T)` si la méthode terminée a un [retourner](../../../../visual-basic/language-reference/statements/return-statement.md) instruction qui retourne une valeur de type T, et vous utilisez `Task` si la méthode terminée ne retourne aucune valeur explicite.</span><span class="sxs-lookup"><span data-stu-id="90d91-214">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="90d91-215">Pour plus d’informations, consultez [les Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="90d91-215">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="90d91-216">La méthode `GetURLContents` comporte une instruction return et l'instruction retourne un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="90d91-216">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="90d91-217">Ainsi, le type de retour de la version asynchrone est Task(T), où T est un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="90d91-217">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="90d91-218">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="90d91-218">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="90d91-219">Modifier le type de retour pour `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="90d91-219">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="90d91-220">Par convention, les méthodes asynchrones portent des noms qui se terminent par « Async ». Renommez alors la méthode `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-220">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="90d91-221">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="90d91-221">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="90d91-222">Avec ces quelques modifications, la conversion de `GetURLContents` en méthode asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="90d91-222">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="90d91-223"><a name="SumPageSizes"></a>Pour convertir une méthode asynchrone SumPageSizes</span><span class="sxs-lookup"><span data-stu-id="90d91-223"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="90d91-224">Répétez les étapes de la procédure précédente pour `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="90d91-224">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="90d91-225">Tout d'abord, modifiez l'appel à `GetURLContents` en appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="90d91-225">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="90d91-226">Remplacez le nom de la méthode appelée `GetURLContents` par `GetURLContentsAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="90d91-226">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="90d91-227">Appliquer `Await` à la tâche qui `GetURLContentsAsync` retourne pour obtenir de l’octet de valeur de tableau.</span><span class="sxs-lookup"><span data-stu-id="90d91-227">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="90d91-228">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="90d91-228">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="90d91-229">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="90d91-229">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  <span data-ttu-id="90d91-230">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="90d91-230">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="90d91-231">Marquez la méthode avec la `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="90d91-231">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="90d91-232">Ajoutez « Async » au nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="90d91-232">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="90d91-233">Il n'existe aucune variable de retour de tâche, T, cette fois, car `SumPageSizesAsync` ne retourne pas de valeur pour T. (La méthode n’a aucun `Return` instruction.) Toutefois, la méthode doit retourner un `Task` pour pouvoir être attendue.</span><span class="sxs-lookup"><span data-stu-id="90d91-233">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="90d91-234">Par conséquent, changez le type de méthode de `Sub` à `Function`.</span><span class="sxs-lookup"><span data-stu-id="90d91-234">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="90d91-235">Le type de retour de la fonction est `Task`.</span><span class="sxs-lookup"><span data-stu-id="90d91-235">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="90d91-236">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="90d91-236">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="90d91-237">La conversion de `SumPageSizes` en `SumPageSizesAsync` est terminée.</span><span class="sxs-lookup"><span data-stu-id="90d91-237">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="90d91-238"><a name="startButton"></a>Pour convertir une méthode asynchrone startButton_Click</span><span class="sxs-lookup"><span data-stu-id="90d91-238"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="90d91-239">Dans le gestionnaire d'événements, remplacez le nom de la méthode appelée `SumPageSizes` par `SumPageSizesAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="90d91-239">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="90d91-240">Étant donné que `SumPageSizesAsync` est une méthode async, modifiez le code dans le gestionnaire d'événements de sorte à attendre le résultat.</span><span class="sxs-lookup"><span data-stu-id="90d91-240">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="90d91-241">L'appel à `SumPageSizesAsync` reflète l'appel à `CopyToAsync` dans `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-241">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="90d91-242">L'appel retourne un `Task`, et non un `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="90d91-242">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="90d91-243">Comme dans les procédures précédentes, vous pouvez convertir l'appel à l'aide d'une ou deux instructions.</span><span class="sxs-lookup"><span data-stu-id="90d91-243">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="90d91-244">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="90d91-244">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="90d91-245">Pour empêcher les ressaisir accidentellement l’opération, ajoutez l’instruction suivante en haut de `startButton_Click` pour désactiver la **Démarrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="90d91-245">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="90d91-246">Vous pouvez réactiver le bouton à la fin du gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="90d91-246">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="90d91-247">Pour plus d’informations sur la réentrance, consultez [gère la réentrance dans Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="90d91-247">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="90d91-248">Enfin, ajoutez le `Async` modificateur à la déclaration afin que le Gestionnaire d’événements peut attendre `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-248">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="90d91-249">En règle générale, les noms des gestionnaires d'événements ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="90d91-249">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="90d91-250">Le type de retour n’est pas modifié pour `Task` , car les gestionnaires d’événements doivent être `Sub` procédures dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90d91-250">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="90d91-251">La conversion du projet depuis un traitement synchrone vers un traitement asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="90d91-251">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="90d91-252"><a name="testAsynch"></a>Pour tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="90d91-252"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="90d91-253">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="90d91-253">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="90d91-254">Une sortie semblable à la sortie de la solution synchrone doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="90d91-254">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="90d91-255">En revanche, observez les différences ci-après.</span><span class="sxs-lookup"><span data-stu-id="90d91-255">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="90d91-256">Les résultats ne se produisent pas tous en même temps, une fois le traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="90d91-256">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="90d91-257">Par exemple, les deux programmes contiennent une ligne dans `startButton_Click` qui efface la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="90d91-257">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="90d91-258">L’objectif est d’effacer la zone de texte entre les exécutions, si vous choisissez la **Démarrer** bouton une seconde fois, une fois un jeu de résultats est apparu.</span><span class="sxs-lookup"><span data-stu-id="90d91-258">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="90d91-259">Dans la version synchrone, la zone de texte s’efface juste avant que les nombres n’apparaissent pour la deuxième fois, quand les téléchargements sont terminés et que le thread d’interface utilisateur est libre d’effectuer autre chose.</span><span class="sxs-lookup"><span data-stu-id="90d91-259">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="90d91-260">Dans la version asynchrone, la zone de texte efface immédiatement après avoir choisi le **Démarrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="90d91-260">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="90d91-261">Plus important encore, le thread d'interface utilisateur n'est pas bloqué pendant les téléchargements.</span><span class="sxs-lookup"><span data-stu-id="90d91-261">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="90d91-262">Vous pouvez déplacer ou redimensionner la fenêtre pendant le téléchargement, la comptabilisation et l'affichage des ressources web.</span><span class="sxs-lookup"><span data-stu-id="90d91-262">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="90d91-263">Si un des sites Web est lent ou ne répond ne pas, vous pouvez annuler l’opération en choisissant le **fermer** bouton (x dans le champ rouge dans le coin supérieur droit).</span><span class="sxs-lookup"><span data-stu-id="90d91-263">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="90d91-264"><a name="GetURLContentsAsync"></a>Pour remplacer la méthode GetURLContentsAsync avec une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90d91-264"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="90d91-265">Le .NET Framework 4.5 propose de nombreuses méthodes async que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="90d91-265">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="90d91-266">Un d’eux, le <xref:System.Net.Http.HttpClient>méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, est exactement ce que vous avez besoin pour cette procédure pas à pas.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="90d91-266">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="90d91-267">Vous pouvez l'utiliser à la place de la méthode `GetURLContentsAsync` que vous avez créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="90d91-267">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="90d91-268">La première étape consiste à créer un objet `HttpClient` dans la méthode `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-268">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="90d91-269">Ajoutez la déclaration suivante au début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="90d91-269">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="90d91-270">Dans `SumPageSizesAsync,`, remplacez l'appel à votre méthode `GetURLContentsAsync` par un appel à la méthode `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="90d91-270">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="90d91-271">Supprimez ou commentez la méthode `GetURLContentsAsync` que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="90d91-271">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="90d91-272">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="90d91-272">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="90d91-273">Le comportement de cette version du projet doit correspondre à celui décrit par la procédure « Pour tester la solution asynchrone » mais avec encore moins d'efforts de votre part.</span><span class="sxs-lookup"><span data-stu-id="90d91-273">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="90d91-274"><a name="BKMK_CompleteCodeExamples"></a>Exemple</span><span class="sxs-lookup"><span data-stu-id="90d91-274"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="90d91-275">Le code suivant inclut l'exemple complet de la conversion d'une solution synchrone en solution asynchrone à l'aide de la méthode `GetURLContentsAsync` asynchrone que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="90d91-275">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="90d91-276">Remarquez qu’il ressemble fortement à la solution synchrone d’origine.</span><span class="sxs-lookup"><span data-stu-id="90d91-276">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="90d91-277">Le code suivant inclut l'exemple complet de la solution qui utilise la méthode `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="90d91-277">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="90d91-278">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90d91-278">See Also</span></span>  
 <span data-ttu-id="90d91-279">[Exemple Async : Accès à la procédure Web (c# et Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span><span class="sxs-lookup"><span data-stu-id="90d91-279">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span></span>  
<span data-ttu-id="90d91-280"> [Await (opérateur)](../../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="90d91-280"> [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="90d91-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span><span class="sxs-lookup"><span data-stu-id="90d91-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span></span>  
<span data-ttu-id="90d91-282"> [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="90d91-282"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="90d91-283"> [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="90d91-283"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="90d91-284"> [Programmation asynchrone basée sur les tâches (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span><span class="sxs-lookup"><span data-stu-id="90d91-284"> [Task-based Asynchronous Programming (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span></span>  
<span data-ttu-id="90d91-285"> [Comment : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span><span class="sxs-lookup"><span data-stu-id="90d91-285"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span></span>  
<span data-ttu-id="90d91-286"> [Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="90d91-286"> [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span></span>
