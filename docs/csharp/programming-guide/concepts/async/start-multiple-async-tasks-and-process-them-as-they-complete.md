---
title: "Démarrer plusieurs tâches Async et les traiter une fois terminées (C#) | Microsoft Docs"
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
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ae131d70af5e4f469b99e2544b8de220fbf92a26
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)
En utilisant <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une, une fois terminées, au lieu de les traiter dans l’ordre dans lequel elles ont démarré.  
  
 L’exemple suivant utilise une requête pour créer une collection de tâches. Chaque tâche télécharge le contenu d’un site web spécifié. À chaque itération d’une boucle while, un appel attendu à `WhenAny` retourne la tâche de la collection de tâches dont le téléchargement se termine en premier. Cette tâche est supprimée de la collection et traitée. La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.  
  
> [!NOTE]
>  Pour exécuter les exemples, Visual Studio 2012 ou version ultérieure et .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.  
  
## <a name="downloading-the-example"></a>Téléchargement de l'exemple  
 Vous pouvez télécharger l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046), puis effectuer les opérations suivantes.  
  
1.  Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningCS.  
  
4.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le projet **ProcessTasksAsTheyFinish**, puis choisissez **Définir comme projet de démarrage**.  
  
5.  Appuyez sur la touche F5 pour exécuter le projet.  
  
     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.  
  
6.  Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.  
  
 Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique.  
  
## <a name="building-the-example"></a>Génération de l’exemple  
 Cet exemple ajoute le code développé dans [Annuler les tâches Async restantes lorsque l’une d’elles est terminée (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Annuler les tâches Async restantes lorsque l’une d’elles est terminée](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) et utilise la même interface utilisateur.  
  
 Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section « Téléchargement de l’exemple », mais choisissez **CancelAfterOneTask** comme **Projet de démarrage**. Ajoutez les modifications de cette rubrique à la méthode `AccessTheWebAsync` dans ce projet. Les modifications sont marquées par des astérisques.  
  
 Le projet **CancelAfterOneTask** inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches. Chaque appel à `ProcessURLAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Dans le fichier MainWindow.xaml.cs du projet, apportez les modifications suivantes à la méthode `AccessTheWebAsync`.  
  
-   Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> à la place de <xref:System.Linq.Enumerable.ToArray%2A>.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
-   Ajoutez une boucle while qui effectue les étapes suivantes pour chaque tâche dans la collection.  
  
    1.  Elle attend un appel à `WhenAny` pour identifier la première tâche dans la collection afin de terminer son téléchargement.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
    2.  Elle supprime cette tâche de la collection.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
    3.  Elle attend `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`. La variable `firstFinishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TReturn` est un entier. La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant.  
  
        ```cs  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        VBCopy Code  
        Dim length = Await firstFinishedTask  
        ```  
  
 Vous devez exécuter le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.  
  
> [!CAUTION]
>  Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches. Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter. Pour plus d’informations et d’exemples, consultez l’article relatif au [traitement des tâches une fois terminées](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est le texte complet du fichier MainWindow.xaml.cs de l’exemple. Des astérisques marquent les éléments ajoutés pour cet exemple.  
  
 Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.  
  
 Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
```cs  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
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
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Réglage de votre application Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programmation asynchrone avec Async et Await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)   
 [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046)
