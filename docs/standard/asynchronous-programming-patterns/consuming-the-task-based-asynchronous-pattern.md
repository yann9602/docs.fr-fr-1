---
title: "Consuming the Task-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, and TAP"
  - "asynchronous design patterns, .NET Framework"
  - "TAP, .NET Framework support for"
  - "Task-based Asynchronous Pattern, .NET Framework support for"
  - ".NET Framework, asynchronous design patterns"
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Consuming the Task-based Asynchronous Pattern
Lorsque vous utilisez le Modèle Asynchrone basé sur Tâche \(TAP\) pour travailler avec des opérations asynchrones, vous pouvez utiliser des rappels pour attendre sans se bloquer.  Pour les tâches, cela est accompli via des méthodes telles que <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName>.  La prise en charge asynchrone basé sur un langage masque les rappels en autorisant les opérations asynchrones en attente dans le flux de contrôle normal, et le code généré par le compilateur fournit la prise en charge au même niveau de l'API.  
  
## Suspend l'exécution avec Await  
 En commençant par [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vous pouvez utiliser le mot clé [await](../Topic/await%20\(C%23%20Reference\).md) en C\# et [Await Operator](../Topic/Await%20Operator%20\(Visual%20Basic\).md) en Visual Basic pour attendre de façon asynchrone <xref:System.Threading.Tasks.Task> et les objets <xref:System.Threading.Tasks.Task%601>.  Quand vous attendez <xref:System.Threading.Tasks.Task>, l'expression `await` est de type `void`.  Quand vous attendez <xref:System.Threading.Tasks.Task%601>, l'expression `await` est de type `TResult`.  Une expression `await` doit se produire à l'intérieur du corps d'une méthode asynchrone.  Pour plus d'informations sur la prise en charge du langage C\# et Visual Basic dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consultez les spécifications des langages C\# et Visual Basic.  
  
 De manière transparente, la fonctionnalité d'attente installe un rappel sur la tâche à l'aide d'une tâche asynchrone.  Ce rappel poursuit la méthode asynchrone au point de la sélection.  Lorsque la méthode asynchrone est poursuivie, si l'opération attendue terminée avec succès et était une <xref:System.Threading.Tasks.Task%601>, son `TResult` est retournée.  Si <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> qui était attendu terminait dans l'état d' <xref:System.Threading.Tasks.TaskStatus>, une exception <xref:System.OperationCanceledException> est levée.  Si <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> qui était attendu terminait dans l'état <xref:System.Threading.Tasks.TaskStatus>, l'exception qui l'a causé est levée.  Une `Task` peut être en faute à la suite de plusieurs exceptions, mais une seule de ces exceptions est retournée.  Toutefois, la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=fullName> retourne une exception <xref:System.AggregateException> qui contient toutes les erreurs.  
  
 Si un contexte de synchronisation \(objet<xref:System.Threading.SynchronizationContext>\) est associé au thread qui exécutait la méthode asynchrone au moment de la suspension \(par exemple, si la propriété <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=fullName> n'est pas `null`\), la méthode asynchrone poursuit sur ce même contexte de synchronisation à l'aide de la méthode <xref:System.Threading.SynchronizationContext.Post%2A> du contexte.  Sinon, elle repose sur le planificateur de tâches \(objet<xref:System.Threading.Tasks.TaskScheduler>\) qui était en cours au moment de la sélection.  En général, c'est le planificateur de tâches par défaut \(<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=fullName>\), qui cible le pool de processus.  Ce planificateur de tâches détermine si l'opération asynchrone attendue doit continuer où elle s'est terminée ou si la récupération doit être planifiée.  Le planificateur par défaut permet généralement la suite de s'exécuter sur le thread sur lequel l'opération attendue s'est terminé.  
  
 Lorsqu'elle est appelée, une méthode asynchrone exécute de façon synchrone le corps de la fonction jusqu'à la première expression Await sur une instance permettant l'attente qui n'est pas encore complétée, après quoi l'appel est retourné à l'appelant.  Si la méthode asynchrone ne retourne pas `void`, un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> est retourné pour représenter le calcul actuel.  Dans une méthode asynchrone non void, si une instruction return est produite, ou la fin du corps de la méthode est atteint, la tâche est terminée dans l'état final de <xref:System.Threading.Tasks.TaskStatus>.  Si une exception non gérée fait partir le contrôle du corps de la méthode asynchrone, la tâche s'achève dans l'état <xref:System.Threading.Tasks.TaskStatus>.  Si cette exception est <xref:System.OperationCanceledException>, la tâche se termine à la place dans l'état d' <xref:System.Threading.Tasks.TaskStatus>.  De cette manière, le résultat ou l'exception est finalement publié.  
  
 Il y a plusieurs variations importantes de ce comportement.  Pour des raisons de performances, si une tâche est déjà terminée avant que la tâche est attendue, le contrôle n'est pas cédé, et la fonction continue à s'exécuter.  En outre, retourner au contexte d'origine n'est pas toujours le comportement souhaité et peut être modifié ; cela est décrit plus en détail dans la section suivante.  
  
### Configurer la suspension et la récupération avec Yield et ConfigureAwait  
 Plusieurs méthodes permettent de mieux contrôler l'exécution d'une méthode asynchrone.  Par exemple, vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=fullName> pour introduire un point d'interruption dans la méthode asynchrone :  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
  
```  
  
 Cela équivaut de façon asynchrone à publier ou à planifier au contexte actuel.  
  
```csharp  
Task.Run(async  delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
  
```  
  
 Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=fullName> pour un meilleur contrôle de sélection et un redémarrage dans une méthode asynchrone.  Comme mentionné précédemment, par défaut le contexte actuel, lorsqu'une méthode asynchrone est interrompue, est capturé, et ce contexte capturé est utilisé pour appeler la suite de la méthode asynchrone lors de la modification.  Dans de nombreux cas, il s'agit du comportement exact que vous souhaitez.  Dans d'autres cas, vous ne pouvez pas à vous préoccuper du contexte de suite, et vous pouvez obtenir de meilleures performances en évitant de telles publications sur le contexte d'origine.  Pour activer cela, utilisez la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=fullName> pour informer l'opération d'attente de ne pas capturer et ne pas continuer dans le contexte, mais pour reprendre l'exécution où l'opération asynchrone qui était attendue est terminée :  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
  
```  
  
## Annulation d'une opération asynchrone  
 En commençant par [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les méthodes TAP qui prennent en charge l'annulation fournissent au moins une surcharge qui accepte un jeton d'annulation \(objet<xref:System.Threading.CancellationToken>\).  
  
 Un jeton d'annulation est créé via une source de jeton d'annulation \(objet<xref:System.Threading.CancellationTokenSource>\).  La propriété <xref:System.Threading.CancellationTokenSource.Token%2A> de la source retourne le jeton d'annulation qui sera signalé lorsque la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A> de la source est appelée.  Par exemple, si vous souhaitez télécharger une page Web unique et vous souhaitez pouvoir annuler l'opération, vous créez un objet <xref:System.Threading.CancellationTokenSource>, passez son jeton à la méthode TAP, puis appelez la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A> de la source lorsque vous êtes prêt à annuler l'exécution :  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
  
```  
  
 Pour annuler plusieurs appels asynchrones, vous pouvez passer le même jeton à tous les appels :  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
  
```  
  
 Sinon, vous pouvez passer le même jeton à un sous\-ensemble sélectionné d'opérations :  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
  
```  
  
 Les demandes d'annulation peuvent être initialisées à partir de n'importe quel processus.  
  
 Vous pouvez passer la valeur <xref:System.Threading.CancellationToken.None%2A?displayProperty=fullName> à toute méthode qui accepte un jeton d'annulation pour indiquer que l'annulation ne sera jamais demandée.  Cela retourne la propriété <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=fullName> `false`, et la méthode appelée peut l'optimiser en conséquence.  À des fins de test, vous pouvez également passer dans un jeton d'annulation préannulé qui est instancié à l'aide du constructeur qui accepte une valeur booléenne pour indiquer si le jeton doit commencer dans un état déjà annulé ou non annulable.  
  
 Cette approche à l'annulation présente plusieurs avantages :  
  
-   Vous pouvez passer le même jeton d'annulation à un nombre quelconque de mécanismes asynchrones et synchrones.  
  
-   La même requête d'annulation peut être proliférée à un nombre quelconque d'écouteurs.  
  
-   Le développeur de l'API asynchrone contrôle entièrement si l'annulation peut être demandée et lorsqu'elle peut prendre effet.  
  
-   Le code qui utilise l'API peut sélectivement déterminer les appels asynchrones auxquels il propagera les demandes d'annulation.  
  
## Contrôle de la progression  
 Certaines méthodes asynchrones exposent la progression via une interface de progression passée à la méthode asynchrone.  Par exemple, considérez une fonction qui télécharge de façon asynchrone une chaîne de texte, et tout au long de l'opération lève des mises à jour de progression qui incluent le pourcentage de téléchargement effectué.  Une telle méthode peut être consommée dans une application Windows Presentation Foundation \(WPF\) comme suit :  
  
```csharp  
private async  void btnDownload_Click(object sender, RoutedEventArgs e)    
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,   
            new Progress<int>(p => pbDownloadProgress.Value = p));  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
  
```  
  
<a name="combinators"></a>   
## À l'aide des combinateurs inclus basés sur les tâches  
 L'espace de noms <xref:System.Threading.Tasks> inclut plusieurs méthodes pour utiliser et composer des tâches.  
  
### Task.Run  
 La classe <xref:System.Threading.Tasks.Task> inclut plusieurs méthodes <xref:System.Threading.Tasks.Task.Run%2A> qui vous permettent de facilement décharger le travail en tant que <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> au pool de processus, par exemple :  
  
```csharp  
public async  void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
  
```  
  
 Certaines de ces méthodes <xref:System.Threading.Tasks.Task.Run%2A>, telles que la surcharge <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName>, existent en tant que sténographie de la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName>.  D'autres surcharges, telles que <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName>, vous permettent de l'utiliser l'attente du travail déchargé, par exemple :  
  
```csharp  
public async  void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 De telles surcharges sont logiquement équivalentes à utiliser la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName> avec la méthode d'extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> dans la bibliothèque parallèle de tâches.  
  
### Task.FromResult  
 Utilisez la méthode <xref:System.Threading.Tasks.Task.FromResult%2A> dans les cas où les données sont déjà disponibles et uniquement besoin d'être retournées par une méthode qui retourne une tâche envoyée dans <xref:System.Threading.Tasks.Task%601> :  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async  Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
  
```  
  
### Task.WhenAll  
 Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A> pour attendre de façon asynchrone sur plusieurs opérations asynchrones qui sont représentées en tant que tâches.  La méthode a plusieurs surcharges qui prennent en charge un ensemble de tâches non génériques ou un ensemble de tâches non générique \(par exemple, les attentes asynchrones pour les multiples opérations retournant void, ou les attentes de façon asynchrone pour les multiples méthodes qui retournent des valeurs quand chaque valeur peut avoir un type différent\) et prendre en charge un ensemble uniforme de tâches générique \(telles qu'une attente asynchrone de plusieurs méthodes retournant `TResult`\).  
  
 Supposons que vous souhaitez envoyer des messages électroniques à plusieurs clients.  Vous pouvez superposer l'envoi des messages afin que vous n'attendiez pas qu'un envoi se termine avant d'envoyer le suivant.  Vous pouvez également découvrir lorsque les opérations d'envoi terminées et si des erreurs se sont produites :  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
  
```  
  
 Ce code ne gère pas explicitement les exceptions qui peuvent se produire, mais laisse les exceptions se propager hors de `await` sur la tâche résultant de <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Pour gérer les exceptions, vous pouvez utiliser le code suivant :  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    ...  
}  
  
```  
  
 Dans ce cas, si une opération asynchrone échoue, toutes les exceptions sont consolidées dans une exception <xref:System.AggregateException>, qui est stockée dans <xref:System.Threading.Tasks.Task> qui est retourné par la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Toutefois, une seule de ces exceptions est propagé par le mot clé `await`.  Si vous souhaitez examiner toutes les exceptions, vous pouvez réécrire le code précédent comme suit :  
  
```csharp  
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
  
```  
  
 Prenons de façon asynchrone un exemple de plusieurs fichiers en téléchargement depuis le Web.  Dans ce cas, toutes les opérations asynchrones ont des types de résultat homogènes, et il est facile d'accéder aux résultats :  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Vous pouvez utiliser les mêmes techniques de gestion que nous avons traitées dans le cas précédent des méthodes retournant void :  
  
```csharp  
Task [] asyncOps =   
    (from url in urls select DownloadStringAsync(url)).ToArray();  
try  
{  
    string [] pages = await Task.WhenAll(asyncOps);  
    ...  
}  
catch(Exception exc)  
{  
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
  
```  
  
### Task.WhenAny  
 Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour attendre de façon asynchrone qu'une des différentes opérations asynchrones représentées en tant que tâches soit terminée.  Cette méthode utilise quatre cas d'usage principaux :  
  
-   Redondance : l'exécution d'une opération plusieurs fois et la sélection de celle qui se termine en premier \(par exemple, en contactant plusieurs services Web de cotations boursières qui produisent un résultat unique et en sélectionnant celui qui s'arrête le plus rapidement\).  
  
-   Entrelacement : Activer plusieurs opérations et attendre que toutes se terminent, mais les traiter quand elles se terminent.  
  
-   Étranglement : laisser les opérations supplémentaires démarrer alors que les autres se terminent.  C'est une extension du scénario d'entrelacement.  
  
-   Renflouement : Par exemple, une opération représentée par la tâche t1 peut être regroupée dans une tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> avec une autre tâche t2, et vous pouvez attendre sur la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A>.  La tâche t2 peut représenter une minuterie, ou une annulation, ou un autre signal qui provoque la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> de se terminer avant que le t1 se termine.  
  
#### Redondance  
 Considérez un cas où vous souhaitez prendre une décision concernant l'achat d'actions.  Il existe plusieurs services Web de recommandations boursières auxquels vous faites confiance, mais en fonction du chargement quotidien, chaque service peut au final être lent à différents moments.  Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour recevoir une notification lorsqu'une opération se termine :  
  
```csharp  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol),   
    GetBuyRecommendation2Async(symbol),  
    GetBuyRecommendation3Async(symbol)  
};  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
if (await recommendation) BuyStock(symbol);  
  
```  
  
 Contrairement à <xref:System.Threading.Tasks.Task.WhenAll%2A>, qui retourne les résultats non encapsulés de toutes les tâches que se sont terminées avec succès, <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche qui s'est terminée.  Si une tâche échoue, il est important de savoir qu'elle a échouée, et si une tâche réussit, il est important de savoir avec quelle tâche la valeur de retour est associée.  Par conséquent, vous devez accéder au résultat de la tâche renvoyée, ou en outre l'attendre, comme le montre cet exemple.  
  
 Comme avec <xref:System.Threading.Tasks.Task.WhenAll%2A>, vous devez pouvoir tenir compte des exceptions.  Étant donné que vous recevez en retour la tâche achevée, vous pouvez attendre la tâche retournée pour avoir les erreurs propagées, et les `try/catch` correctement ; par exemple :  
  
```csharp  
Task<bool> [] recommendations = …;  
while(recommendations.Count > 0)  
{   
    Task<bool> recommendation = await Task.WhenAny(recommendations);      
    try  
    {  
        if (await recommendation) BuyStock(symbol);  
        break;  
    }  
    catch(WebException exc)  
    {  
        recommendations.Remove(recommendation);  
    }  
}  
  
```  
  
 En outre, même si une première tâche est terminée avec succès, les tâches suivantes peuvent échouer.  À ce stade, vous disposez de plusieurs options pour le traitement des exceptions : Vous pouvez attendre que toutes les tâches lancées se soient effectuées , dans ce cas vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>, ou vous pouvez décider que toutes les exceptions sont importantes et doivent être signalées.  Pour cela, vous pouvez utiliser des poursuites pour recevoir une notification lorsque les tâches sont exécutées de façon asynchrone :  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
  
```  
  
 ou :  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
  
```  
  
 ou même :  
  
```  
private static async  void LogCompletionIfFailed(IEnumerable<Task> tasks)  
{  
    foreach(var task in tasks)  
    {  
        try { await task; }  
        catch(Exception exc) { Log(exc); }  
    }  
}  
…  
LogCompletionIfFailed(recommendations);  
  
```  
  
 Enfin, vous pouvez annuler toutes les opérations restantes :  
  
```csharp  
var cts = new CancellationTokenSource();  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol, cts.Token),   
    GetBuyRecommendation2Async(symbol, cts.Token),  
    GetBuyRecommendation3Async(symbol, cts.Token)  
};  
  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
cts.Cancel();  
if (await recommendation) BuyStock(symbol);  
  
```  
  
#### Entrelacement  
 Considérez un cas où vous téléchargez des images du Web et traitez chaque image \(par exemple, en ajoutant l'image à un contrôle d'interface utilisateur\).  Vous devez faire traiter séquentiellement sur le processus d'interface utilisateur, mais vous souhaitez télécharger les images le plus simultanément possible.  De plus, vous ne souhaitez pas différer l'ajout d'images à l'interface utilisateur en attendant qu'elles soient toutes téléchargées\- vous souhaitez les ajouter en même temps que d'autres se terminent :  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
  
```  
  
 Vous pouvez également appliquer l'entrelacement à un scénario qui implique le traitement nécessitant de nombreuses ressources de calcul sur <xref:System.Threading.ThreadPool> des images téléchargées ; par exemple :  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)  
         .ContinueWith(t => ConvertImage(t.Result)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
  
```  
  
#### Throttling  
 Prenons l'exemple de l'entrelacement, excepté le fait que l'utilisateur télécharge tellement d'images que les téléchargements sont étranglés ; par exemple, vous souhaitez qu'un nombre spécifique de téléchargements soient générés simultanément.  Pour ce faire, vous pouvez démarrer un sous\-ensemble des opérations asynchrones.  Au fur et à mesure que les opérations terminent, vous pouvez démarrer des opérations supplémentaires pour prendre leur place :  
  
```csharp  
const int CONCURRENCY_LEVEL = 15;  
Uri [] urls = …;  
int nextIndex = 0;  
var imageTasks = new List<Task<Bitmap>>();  
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)  
{  
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
    nextIndex++;  
}  
  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch(Exception exc) { Log(exc); }  
  
    if (nextIndex < urls.Length)  
    {  
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
        nextIndex++;  
    }  
}  
  
```  
  
#### Renflouement précoce  
 Considérez que vous prévoyez de façon asynchrone qu'une opération se termine en même temps qu'elle répond à cette demande de l'annulation d'un utilisateur \(par exemple, l'utilisateur a cliqué sur un bouton annuler\).  Le code suivant illustre ce comportement :  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async  void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        if (imageDownload.IsCompleted)  
        {  
            Bitmap image = await imageDownload;  
            panel.AddImage(image);  
        }  
        else imageDownload.ContinueWith(t => Log(t));  
    }  
    finally { btnRun.Enabled = true; }  
}  
  
private static async  Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
  
```  
  
 Cette implémentation réactive l'interface utilisateur dès que vous déciderez de renflouer, mais n'annule pas les opérations asynchrones sous\-jacentes.  Une autre solution est d'annuler les opérations en attente lorsque vous décidez de renflouer, mais de ne pas rétablir l'interface utilisateur jusqu'à ce que les opérations se terminent, potentiellement en raison de finir trop tôt en raison de la demande d'annulation :  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async  void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        Bitmap image = await imageDownload;  
        panel.AddImage(image);  
    }  
    catch(OperationCanceledException) {}  
    finally { btnRun.Enabled = true; }  
}  
  
```  
  
 Un autre exemple de renflouement précoce implique l'utilisation de la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> avec la méthode <xref:System.Threading.Tasks.Task.Delay%2A>, comme décrit dans la section suivante.  
  
### Task.Delay  
 Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Delay%2A> pour introduire des pauses dans l'exécution d'une méthode asynchrone.  Ceci est utile pour de nombreux types de fonctionnalités, y compris les boucles d'interrogation de génération et différer la gestion de l'entrée d'utilisateur pendant une période prédéterminée.  La méthode <xref:System.Threading.Tasks.Task.Delay%2A> peut également être utile en association avec <xref:System.Threading.Tasks.Task.WhenAny%2A> pour implémenter des délais d'attente.  
  
 Si une tâche qui fait partie d'une plus grande opération asynchrone \(par exemple, un service Web ASP.NET\) utilise trop de temps pour s'exécuter, l'opération globale peut souffrir, surtout si elle ne se termine pas jamais.  Pour cette raison, il est important de pouvoir chronométrer en attente d'une opération asynchrone.  La <xref:System.Threading.Tasks.Task.Wait%2A>synchrone, <xref:System.Threading.Tasks.Task.%2A> WaitAll?qualifyHint=False&autoUpgrade=True, et les méthodes <xref:System.Threading.Tasks.Task.%2A> WaitAny?qualifyHint=False&autoUpgrade=True acceptent des valeurs du délai d'attente, mais le <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>correspondant\/<xref:System.Threading.Tasks.Task.WhenAny%2A> et les méthodes mentionnées précédemment <xref:System.Threading.Tasks.Task.WhenAll%2A>et<xref:System.Threading.Tasks.Task.WhenAny%2A> ne stockent pas.  À la place, vous pouvez utiliser <xref:System.Threading.Tasks.Task.Delay%2A> et <xref:System.Threading.Tasks.Task.WhenAny%2A> en association pour implémenter une minuterie.  
  
 Par exemple, dans votre application d'interface utilisateur, disons que vous souhaitez télécharger une image et désactiver l'interface utilisateur pendant que l'image se télécharge.  Toutefois, si le téléchargement est trop long, vous voulez réactiver l'interface utilisateur et abandonner le téléchargement :  
  
```csharp  
public async  void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = “Downloaded”;  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = “Timed out”;  
            var ignored = download.ContinueWith(  
                t => Trace(“Task finally completed”));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
  
```  
  
 Le même s'applique à plusieurs téléchargements, car <xref:System.Threading.Tasks.Task.WhenAll%2A> retourne une tâche :  
  
```csharp  
public async  void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = “Downloaded”;  
        }  
        else  
        {  
            status.Text = “Timed out”;  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
  
```  
  
## Générer des combinateurs basés sur une tâche  
 Étant donné qu'une tâche peut représenter complètement une opération asynchrone et fournir des fonctions synchrones et asynchrones pour s'attacher à une exécution, la récupération de ses résultats, etc., vous pouvez générer des bibliothèques de combinateurs utiles qui composent des tâches qui génèrent de plus grands modèles.  Comme décrit dans la section précédente, le .NET Framework inclut plusieurs combinateurs prédéfinis, mais vous pouvez également créer vos propres combinateurs.  Les sections suivantes fournissent plusieurs exemples de méthodes et de types potentiels de combinateur.  
  
### RetryOnFault  
 Dans de nombreux cas, vous pouvez redémarrer une opération si la précédente tentative échoue.  Pour le code synchrone, vous pouvez générer une méthode d'assistance telle que `RetryOnFault` dans l'exemple suivant :  
  
```csharp  
public static T RetryOnFault<T>(  
    Func<T> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return function(); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
  
```  
  
 Vous pouvez générer une méthode d'assistance presque identique pour les opérations asynchrones qui sont implémentées avec TAP et ainsi retourner les tâches :  
  
```csharp  
public static async  Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 Vous pouvez ensuite utiliser ce combinateur pour encoder des relances dans la logique de l'application ; par exemple :  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
  
```  
  
 Vous pouvez étendre la fonction `RetryOnFault` davantage.  Par exemple, la fonction peut recevoir un autre `Func<Task>` qui sera appelé entre les relances pour déterminer quand réessayer l'exécution ; par exemple :  
  
```csharp  
public static async  Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
        await retryWhen().ConfigureAwait(false);  
    }  
    return default(T);  
}  
```  
  
 Vous pouvez ensuite utiliser la fonction comme suit pour attendre une seconde avant de réessayer l'opération :  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
  
```  
  
### NeedOnlyOne  
 Parfois, vous pouvez tirer parti de la redondance pour améliorer la latence et les chances de réussir une opération.  Considérez plusieurs services Web qui fournissent des cotations boursières, mais à différents moments du jour, chaque service peut fournir des niveaux de qualité et de temps de réponse différents.  Pour traiter ces fluctuations, vous pouvez fournir des demandes à tous les services Web, et dès que vous obtiendrez une réponse d'une, supprimez les demandes restantes.  Vous pouvez implémenter une fonction d'assistance pour simplifier l'implémentation de ce modèle commun d'activer plusieurs opérations, puis d'attente, puis d'annuler le reste.  La fonction `NeedOnlyOne` dans l'exemple suivant illustre ce scénario :  
  
```csharp  
public static async  Task<T> NeedOnlyOne(  
    params Func<CancellationToken,Task<T>> [] functions)  
{  
    var cts = new CancellationTokenSource();  
    var tasks = (from function in functions  
                 select function(cts.Token)).ToArray();  
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);  
    cts.Cancel();  
    foreach(var task in tasks)   
    {  
        var ignored = task.ContinueWith(  
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);  
    }  
    return completed;  
}  
```  
  
 Vous pouvez ensuite utiliser cette fonction comme suit :  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async(“msft”, ct),  
    ct => GetCurrentPriceFromServer2Async(“msft”, ct),  
    ct => GetCurrentPriceFromServer3Async(“msft”, ct));  
```  
  
### Opérations entrelacées  
 Il y a un problème potentiel de performances avec l'utilisation de la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour prendre en charge un scénario entrelacé lorsque vous utilisez des groupes de tâches très volumineux.  Chaque appel à <xref:System.Threading.Tasks.Task.WhenAny%2A> trouve une continuation enregistrée avec chaque tâche.  Pour un nombre N de tâches, cela provoque des poursuites O \(N2\) créées pendant toute la durée de vie de l'opération entrelacée.  Si vous travaillez avec de grands ensembles de tâches, vous pouvez utiliser un combinateur \(`Interleaved` dans l'exemple suivant\) pour résoudre le problème de performances :  
  
```csharp  
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputTasks = tasks.ToList();  
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)   
                   select new TaskCompletionSource<T>()).ToList();  
    int nextTaskIndex = -1;  
    foreach (var inputTask in inputTasks)  
    {  
        inputTask.ContinueWith(completed =>  
        {  
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];  
            if (completed.IsFaulted)   
                source.TrySetException(completed.Exception.InnerExceptions);  
            else if (completed.IsCanceled)   
                source.TrySetCanceled();  
            else   
                source.TrySetResult(completed.Result);  
        }, CancellationToken.None,   
           TaskContinuationOptions.ExecuteSynchronously,   
           TaskScheduler.Default);  
    }  
    return from source in sources   
           select source.Task;  
}  
  
```  
  
 Vous pouvez ensuite utiliser le combinateur pour traiter les résultats des tâches qui se terminent ; par exemple :  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### WhenAllOrFirstException  
 Dans certains scénarios de dispersion\/rassemblement, vous souhaitez vouloir attendre toutes les tâches d'un ensemble, à moins que l'une d'entre elles soient en faute, auquel cas vous souhaitez cesser d'attendre dès que l'exception se produira.  Vous pouvez accomplir cela avec une méthode de combinateur telle que `WhenAllOrFirstException` dans l'exemple suivant :  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
  
```  
  
## Générer des structures de données basées sur une tâche  
 Outre la possibilité de générer des combinateurs basés sur des tâches personnalisés, avoir une structure de données dans <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui représente les résultats d'une opération asynchrone et la synchronisation nécessaire pour les attacher produit en fait un type très puissant sur lequel on peut générer des structures de données personnalisées à utiliser dans les scénarios asynchrones.  
  
### AsyncCache  
 Un aspect important d'une tâche est qu'elle peut être distribuée à plusieurs consommateurs, qui peuvent tous se mettre en attente, s'abonner à sa poursuite, obtenir son résultat \(dans le cas de <xref:System.Threading.Tasks.Task%601>\) ou ses exceptions, et ainsi de suite.  Les <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> sont parfaitement adaptés pour être utilisé dans une infrastructure asynchrone de mise en cache.  Voici un exemple d'un petit mais puissant cache asynchrone généré sur <xref:System.Threading.Tasks.Task%601> :  
  
```csharp  
public class AsyncCache<TKey, TValue>  
{  
    private readonly Func<TKey, Task<TValue>> _valueFactory;  
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;  
  
    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)  
    {  
        if (valueFactory == null) throw new ArgumentNullException("loader");  
        _valueFactory = valueFactory;  
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();  
    }  
  
    public Task<TValue> this[TKey key]  
    {  
        get  
        {  
            if (key == null) throw new ArgumentNullException("key");  
            return _map.GetOrAdd(key, toAdd =>   
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;  
        }  
    }  
}  
  
```  
  
 La classe [AsyncCache\<TKey, TValue\>](http://go.microsoft.com/fwlink/p/?LinkId=251941) accepte comme délégué à son constructeur une fonction qui prend `TKey` et renvoie <xref:System.Threading.Tasks.Task%601>.  Toutes les valeurs précédemment accessibles à partir du cache sont stockées dans le dictionnaire interne, et `AsyncCache` garantit qu'une tâche est générée par clé, même si le cache est accessible simultanément.  
  
 Par exemple, vous pouvez générer un cache des pages Web téléchargées :  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
  
```  
  
 Vous pouvez ensuite utiliser ce cache dans les méthodes asynchrones lorsque vous avez besoin du contenu d'une page Web.  La classe `AsyncCache` garantit que vous téléchargez le moins de pages possible, et met en cache les résultats.  
  
```csharp  
private async  void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
  
```  
  
### AsyncProducerConsumerCollection  
 Vous pouvez également utiliser des tâches pour générer des structures de données pour coordonner les activités asynchrones.  Considérez un des modèles de design parallèles commun : producteur et consommateur.  Dans ce modèle, les producteurs génèrent des données qui sont consommées par les consommateurs, et les producteurs et consommateurs peuvent s'exécuter en parallèle.  Par exemple, le consommateur traite le point 1, qui a été précédemment généré par un producteur qui produit maintenant le point 2. Pour le modèle de producteur et consommateur, vous avez besoin invariablement d'une certaine structure de données pour stocker le travail créé par des producteurs de sorte que les consommateurs puissent être avisés de nouvelles données et rechercher si disponibles.  
  
 Voici une structure de données simple générée à partir de tâches qui permet aux méthodes asynchrones d'être utilisée comme producteurs et consommateurs :  
  
```csharp  
public class AsyncProducerConsumerCollection<T>  
{  
    private readonly Queue<T> m_collection = new Queue<T>();  
    private readonly Queue<TaskCompletionSource<T>> m_waiting =   
        new Queue<TaskCompletionSource<T>>();  
  
    public void Add(T item)  
    {  
        TaskCompletionSource<T> tcs = null;  
        lock (m_collection)  
        {  
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();  
            else m_collection.Enqueue(item);  
        }  
        if (tcs != null) tcs.TrySetResult(item);  
    }  
  
    public Task<T> Take()  
    {  
        lock (m_collection)  
        {  
            if (m_collection.Count > 0)   
            {  
                return Task.FromResult(m_collection.Dequeue());   
            }  
            else   
            {  
                var tcs = new TaskCompletionSource<T>();  
                m_waiting.Enqueue(tcs);  
                return tcs.Task;  
            }  
        }  
    }  
}  
  
```  
  
 Avec cette structure de données en place, vous pouvez écrire le code suivant :  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async  Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.Take();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Add(data);  
}  
```  
  
 L'espace de noms <xref:System.Threading.Tasks.Dataflow> inclut le type <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, que vous pouvez utiliser de façon semblable, mais sans devoir générer un type de collection personnalisé :  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async  Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.ReceiveAsync();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Post(data);  
}  
  
```  
  
> [!NOTE]
>  L'espace de noms <xref:System.Threading.Tasks.Dataflow> est disponible dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] via **NuGet**.  Pour installer l'assembly qui contient l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package Microsoft.Tpl.Dataflow.  
  
## Voir aussi  
 [Task\-based Asynchronous Pattern \(TAP\)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)   
 [Implementing the Task\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)   
 [Interop with Other Asynchronous Patterns and Types](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)