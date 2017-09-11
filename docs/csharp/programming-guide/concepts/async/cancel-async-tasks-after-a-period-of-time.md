---
title: "Annuler des tâches asynchrones après une période spécifique (C#)"
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
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
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
ms.openlocfilehash: 450749c67854dbc0020094fe587c34e50d82b8b8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="97a42-102">Annuler des tâches asynchrones après une période spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="97a42-102">Cancel Async Tasks after a Period of Time (C#)</span></span>
<span data-ttu-id="97a42-103">Si vous ne souhaitez pas attendre la fin d’une opération asynchrone, vous pouvez l’annuler après une période spécifique à l’aide de la méthode <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="97a42-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="97a42-104">Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées au terme de la période indiquée par l’expression `CancelAfter`.</span><span class="sxs-lookup"><span data-stu-id="97a42-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="97a42-105">Cet exemple s’appuie sur le code développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites web et afficher la longueur du contenu de chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="97a42-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97a42-106">Pour exécuter les exemples, Visual Studio 2012 ou ultérieur et le .NET Framework 4.5 ou ultérieur doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="97a42-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="97a42-107">Téléchargement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="97a42-107">Downloading the Example</span></span>  
 <span data-ttu-id="97a42-108">Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046), puis procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="97a42-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="97a42-109">Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97a42-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="97a42-110">Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="97a42-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="97a42-111">Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier solution (.sln) pour AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="97a42-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="97a42-112">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterTime**, puis choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="97a42-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="97a42-113">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="97a42-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="97a42-114">Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.</span><span class="sxs-lookup"><span data-stu-id="97a42-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="97a42-115">Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.</span><span class="sxs-lookup"><span data-stu-id="97a42-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="97a42-116">Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="97a42-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="97a42-117">Génération de l’exemple</span><span class="sxs-lookup"><span data-stu-id="97a42-117">Building the Example</span></span>  
 <span data-ttu-id="97a42-118">L’exemple de cette rubrique s’appuie sur le projet développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches.</span><span class="sxs-lookup"><span data-stu-id="97a42-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="97a42-119">Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.</span><span class="sxs-lookup"><span data-stu-id="97a42-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="97a42-120">Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="97a42-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="97a42-121">Ajoutez les changements de cette rubrique à ce projet.</span><span class="sxs-lookup"><span data-stu-id="97a42-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="97a42-122">Pour spécifier une durée maximale avant que les tâches ne soient marquées comme annulées, ajoutez un appel à `CancelAfter` à `startButton_Click`, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="97a42-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="97a42-123">L’ajout est signalé par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="97a42-123">The addition is marked with asterisks.</span></span>  
  
```csharp  
private async void startButton_Click(object sender, RoutedEventArgs e)  
{  
    // Instantiate the CancellationTokenSource.  
    cts = new CancellationTokenSource();  
  
    resultsTextBox.Clear();  
  
    try  
    {  
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
        // can adjust the time.)  
        cts.CancelAfter(2500);  
  
        await AccessTheWebAsync(cts.Token);  
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
    }  
    catch (OperationCanceledException)  
    {  
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
  
    cts = null;   
}  
```  
  
 <span data-ttu-id="97a42-124">Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.</span><span class="sxs-lookup"><span data-stu-id="97a42-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="97a42-125">La sortie suivante est un exemple.</span><span class="sxs-lookup"><span data-stu-id="97a42-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="97a42-126">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="97a42-126">Complete Example</span></span>  
 <span data-ttu-id="97a42-127">Le code suivant est le texte complet du fichier MainWindow.xaml.cs de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="97a42-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="97a42-128">Des astérisques marquent les éléments ajoutés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="97a42-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="97a42-129">Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="97a42-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="97a42-130">Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="97a42-130">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterTime  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
                // can adjust the time.)  
                cts.CancelAfter(2500);  
  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;   
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // Note that the Cancel button cancels all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
  
    // Sample Output:  
  
    // Length of the downloaded string: 35990.  
  
    // Length of the downloaded string: 407399.  
  
    // Length of the downloaded string: 226091.  
  
    // Downloads canceled.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="97a42-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a42-131">See Also</span></span>  
 <span data-ttu-id="97a42-132">[Programmation asynchrone avec async et await (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="97a42-132">[Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
 <span data-ttu-id="97a42-133">[Procédure pas à pas : accès au web avec async et await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="97a42-133">[Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
 <span data-ttu-id="97a42-134">[Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="97a42-134">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span></span>  
 <span data-ttu-id="97a42-135">[Réglage de votre application asynchrone (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="97a42-135">[Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
 [<span data-ttu-id="97a42-136">Exemple Async : réglage de votre application</span><span class="sxs-lookup"><span data-stu-id="97a42-136">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)

