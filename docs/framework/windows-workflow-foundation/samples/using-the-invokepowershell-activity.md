---
title: "Utilisation de l'activité InvokePowerShell"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ea3106f87dae64204ea0c02a1388ed8893c858b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="5be83-102">Utilisation de l'activité InvokePowerShell</span><span class="sxs-lookup"><span data-stu-id="5be83-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="5be83-103">L'exemple InvokePowerShell montre comment appeler des commandes Windows PowerShell à l'aide de l'activité `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5be83-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="5be83-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="5be83-105">Innovation simple des commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="5be83-106">Récupérer des valeurs du pipeline de sortie Windows PowerShell et les stocker dans des variables de workflow.</span><span class="sxs-lookup"><span data-stu-id="5be83-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="5be83-107">Passer des données dans Windows PowerShell en tant que pipeline d'entrée pour une commande en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5be83-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5be83-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5be83-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5be83-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5be83-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5be83-110">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5be83-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5be83-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5be83-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="5be83-112">Discussion</span><span class="sxs-lookup"><span data-stu-id="5be83-112">Discussion</span></span>  
 <span data-ttu-id="5be83-113">Cet exemple contient les trois projets suivants.</span><span class="sxs-lookup"><span data-stu-id="5be83-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="5be83-114">Nom du projet</span><span class="sxs-lookup"><span data-stu-id="5be83-114">Project Name</span></span>|<span data-ttu-id="5be83-115">Description</span><span class="sxs-lookup"><span data-stu-id="5be83-115">Description</span></span>|<span data-ttu-id="5be83-116">Fichiers principaux</span><span class="sxs-lookup"><span data-stu-id="5be83-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="5be83-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="5be83-117">CodedClient</span></span>|<span data-ttu-id="5be83-118">Exemple d'application cliente qui utilise l'activité PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="5be83-119">-   **Program.cs**: crée par programmation un workflow basé sur une séquence qui appelle l’activité InvokePowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="5be83-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="5be83-120">DesignerClient</span></span>|<span data-ttu-id="5be83-121">Ensemble d'activités personnalisées qui contiennent l'activité personnalisée `InvokePowerShell` et d'autres activités personnalisées diverses, et un workflow qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="5be83-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="5be83-122">Activités :</span><span class="sxs-lookup"><span data-stu-id="5be83-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="5be83-123">**PrintCollection.cs**: activité d’assistance qui imprime tous les éléments d’une collection dans la console.</span><span class="sxs-lookup"><span data-stu-id="5be83-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="5be83-124">**ReadLine.cs**: activité d’assistance pour l’entrée de la lecture à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="5be83-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="5be83-125">Système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="5be83-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="5be83-126">**Copy.XAML**: une activité qui copie un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be83-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="5be83-127">**CreateFile.xaml**: activité qui crée un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be83-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="5be83-128">**DeleteFile.xaml**: une activité qui supprime un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be83-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="5be83-129">**MakeDir.xaml**: activité qui crée un répertoire.</span><span class="sxs-lookup"><span data-stu-id="5be83-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="5be83-130">**Move.XAML**: une activité qui déplace un fichier.</span><span class="sxs-lookup"><span data-stu-id="5be83-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="5be83-131">**ReadFile.xaml**: une activité qui lit un fichier et retourne son contenu.</span><span class="sxs-lookup"><span data-stu-id="5be83-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="5be83-132">**TestPath.xaml**: activité qui teste l’existence d’un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="5be83-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="5be83-133">Processus :</span><span class="sxs-lookup"><span data-stu-id="5be83-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="5be83-134">**GetProcess.xaml**: une activité qui obtient une liste des processus en cours.</span><span class="sxs-lookup"><span data-stu-id="5be83-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="5be83-135">**StopProcess.xaml**: activité qui arrête un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="5be83-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="5be83-136">**Program.cs**: appelle le workflow Sequence1.</span><span class="sxs-lookup"><span data-stu-id="5be83-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="5be83-137">**Sequence1.XAML**: un workflow basé sur la séquence.</span><span class="sxs-lookup"><span data-stu-id="5be83-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="5be83-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5be83-138">PowerShell</span></span>|<span data-ttu-id="5be83-139">Activité `InvokePowerShell` et les concepteurs qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="5be83-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="5be83-140">Fichiers d'activité</span><span class="sxs-lookup"><span data-stu-id="5be83-140">Activity Files</span></span><br /><br /> <span data-ttu-id="5be83-141">-   **ExecutePowerShell.cs**: la logique d’exécution principale de l’activité.</span><span class="sxs-lookup"><span data-stu-id="5be83-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="5be83-142">-   **InvokePowerShell.cs**: wrapper autour de la logique d’exécution principale, qui contient une version générique (valeur de retour) et une version non générique (valeur de retour).</span><span class="sxs-lookup"><span data-stu-id="5be83-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="5be83-143">Il s'agit de l'interface publique pour l'activité.</span><span class="sxs-lookup"><span data-stu-id="5be83-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="5be83-144">-   **NoPersistZone.cs**: cette activité empêche toutes les activités enfants la persistance.</span><span class="sxs-lookup"><span data-stu-id="5be83-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="5be83-145">Cette classe est utilisée dans l'implémentation de l'activité `InvokePowerShell` pour empêcher que l'activité soit rendue persistante au milieu de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="5be83-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="5be83-146">Fichiers de concepteur :</span><span class="sxs-lookup"><span data-stu-id="5be83-146">Designer files:</span></span><br /><br /> <span data-ttu-id="5be83-147">1.  **ArgumentDictionaryEditor.cs**: boîte de dialogue Windows qui permet à l’utilisateur de modifier les arguments de la `InvokePowerShell` activité.</span><span class="sxs-lookup"><span data-stu-id="5be83-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="5be83-148">2.  **GenericInvokePowerShellDesigner.xaml** et **GenericInvokePowerShellDesigner.xaml.cs**: définit l’apparence de l’objet générique `InvokePowerShell` activité dans [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be83-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="5be83-149">3.  **InvokePowerShellDesigner.xaml** et **InvokePowerShellDesigner.cs**: définit l’apparence de la non générique `InvokePowerShell` activité dans [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be83-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="5be83-150">Les projets clients sont traités en premier, car il est plus facile de comprendre les fonctionnalités internes de l'activité PowerShell une fois que son utilisation est comprise.</span><span class="sxs-lookup"><span data-stu-id="5be83-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="5be83-151">Utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5be83-151">Using This Sample</span></span>  
 <span data-ttu-id="5be83-152">Les sections suivantes expliquent comment utiliser les trois projets dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5be83-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="5be83-153">Utilisation du projet client encodé</span><span class="sxs-lookup"><span data-stu-id="5be83-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="5be83-154">L'exemple de client crée par programmation une activité de séquence, laquelle contient des exemples de plusieurs méthodes différentes de l'utilisation de l'activité `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5be83-155">Le premier appel lance le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="5be83-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="5be83-156">Le deuxième appel obtient la liste des processus en cours d'exécution sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5be83-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="5be83-157">`Output` est la variable utilisée pour stocker la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="5be83-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="5be83-158">L'appel suivant montre comment exécuter une étape de post-traitement sur chaque sortie individuelle de l'appel de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="5be83-159">`InitializationAction` a la valeur d'une fonction qui génère une représentation sous forme de chaîne pour chaque processus.</span><span class="sxs-lookup"><span data-stu-id="5be83-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="5be83-160">La collection de ces chaînes est retournée dans la variable `Output` par l'activité `InvokePowerShell<string>`.</span><span class="sxs-lookup"><span data-stu-id="5be83-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="5be83-161">Les appels `InvokePowerShell` suivants montrent le passage de données dans l'activité et l'obtention des sorties et des erreurs.</span><span class="sxs-lookup"><span data-stu-id="5be83-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="5be83-162">Utilisation du projet DesignerClient</span><span class="sxs-lookup"><span data-stu-id="5be83-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="5be83-163">Le projet DesignerClient est composé d'un ensemble d'activités personnalisées, presque toutes étant générées de façon à contenir l'activité `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5be83-164">La plupart des activités appellent la version non générique de l'activité `InvokePowerShell` et n'attendent pas de valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="5be83-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="5be83-165">D'autres activités utilisent la version générique de l'activité `InvokePowerShell` et utilisent l'argument `InitializationAction` pour post-traiter les résultats.</span><span class="sxs-lookup"><span data-stu-id="5be83-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="5be83-166">Utilisation du projet PowerShell</span><span class="sxs-lookup"><span data-stu-id="5be83-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="5be83-167">L'action principale de l'activité se produit dans la classe `ExecutePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="5be83-168">Étant donné que l'exécution des commandes PowerShell ne doit pas bloquer le thread de workflow principal, l'activité est créée de façon à être une activité asynchrone en héritant de la classe <xref:System.Activities.AsyncCodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="5be83-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="5be83-169">La méthode <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> est appelée par le runtime du workflow pour commencer l'exécution de l'activité.</span><span class="sxs-lookup"><span data-stu-id="5be83-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="5be83-170">Il commence par appeler les API PowerShell pour créer un pipeline PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="5be83-171">Il crée ensuite une commande PowerShell et la remplit avec des paramètres et des variables.</span><span class="sxs-lookup"><span data-stu-id="5be83-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="5be83-172">Les entrées redirigées sont également envoyées au pipeline à ce stade.</span><span class="sxs-lookup"><span data-stu-id="5be83-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="5be83-173">Enfin, le pipeline est inclus dans un wrapper dans un objet `PipelineInvokerAsyncResult` et retourné.</span><span class="sxs-lookup"><span data-stu-id="5be83-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="5be83-174">L'objet `PipelineInvokerAsyncResult` enregistre un écouteur et appelle le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5be83-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="5be83-175">Lorsque l'exécution se termine, la sortie et les erreurs sont stockées dans le même objet `PipelineInvokerAsyncResult`, et le contrôle est remis au runtime du workflow en appelant la méthode de rappel initialement passée à <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="5be83-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="5be83-176">À la fin de l'exécution de la méthode, le runtime du workflow appelle la méthode <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de l'activité.</span><span class="sxs-lookup"><span data-stu-id="5be83-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="5be83-177">La classe `InvokePowerShell` inclut dans un wrapper la classe `ExecutePowerShellCommand` et crée deux versions de l'activité : une version générique et une version non générique.</span><span class="sxs-lookup"><span data-stu-id="5be83-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="5be83-178">La version non générique retourne directement la sortie de l'exécution de PowerShell, tandis que la version générique transforme les résultats individuels en type générique.</span><span class="sxs-lookup"><span data-stu-id="5be83-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="5be83-179">La version générique de l'activité est implémentée sous la forme d'un workflow séquentiel qui appelle `ExecutePowerShellCommand` et post-traite ses résultats.</span><span class="sxs-lookup"><span data-stu-id="5be83-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="5be83-180">Pour chaque élément de la collection des résultats, l'étape de post-traitement appelle `InitializationAction` s'il est défini.</span><span class="sxs-lookup"><span data-stu-id="5be83-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="5be83-181">Sinon, elle effectue un cast simple.</span><span class="sxs-lookup"><span data-stu-id="5be83-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="5be83-182">Un concepteur a été créé pour chacune des deux activités `InvokePowerShell` (générique et non générique).</span><span class="sxs-lookup"><span data-stu-id="5be83-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="5be83-183">InvokePowerShellDesigner.xaml et son fichier .cs associé définissent l'apparence de la version non générique de l'activité [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] dans le `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5be83-184">À l'intérieur d'InvokePowerShellDesigner.xaml, un <xref:System.Windows.Controls.DockPanel> est utilisé pour représenter l'interface graphique.</span><span class="sxs-lookup"><span data-stu-id="5be83-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="5be83-185">Notez que la propriété `Text` de la zone de texte est une liaison bidirectionnelle qui vérifie que la valeur de la propriété `CommandText` de l'activité est équivalente à la valeur entrée dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="5be83-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="5be83-186">GenericInvokePowerShellDesigner.xaml et son fichier .cs associé définissent l'interface graphique pour l'activité `InvokePowerShell` générique.</span><span class="sxs-lookup"><span data-stu-id="5be83-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="5be83-187">Le concepteur est légèrement plus compliqué, car il permet aux utilisateurs de définir un `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="5be83-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="5be83-188">L'élément clé est l'utilisation de <xref:System.Activities.Presentation.WorkflowItemPresenter> pour permettre le glisser-déplacer d'activités enfants sur l'aire du concepteur `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="5be83-189">La personnalisation du concepteur ne s'arrête pas aux fichiers .xaml qui définissent l'apparence de l'activité sur la zone de conception.</span><span class="sxs-lookup"><span data-stu-id="5be83-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="5be83-190">Les boîtes de dialogue utilisées pour afficher les paramètres de l'activité peuvent également être personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5be83-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="5be83-191">Ces paramètres et les variables PowerShell affectent le comportement des commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be83-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="5be83-192">L’activité expose en tant que <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span><span class="sxs-lookup"><span data-stu-id="5be83-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="5be83-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml et PropertyEditorResources.cs définissent la boîte de dialogue qui vous permet de modifier ces types.</span><span class="sxs-lookup"><span data-stu-id="5be83-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5be83-194">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5be83-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="5be83-195">Vous devez installer Windows PowerShell pour exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5be83-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="5be83-196">Windows PowerShell peut être installé à partir de cet emplacement : [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="5be83-196">Windows PowerShell can be installed from this location: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="5be83-197">Pour exécuter le client encodé</span><span class="sxs-lookup"><span data-stu-id="5be83-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="5be83-198">Ouvrez PowerShell.sln à l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be83-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5be83-199">Cliquez avec le bouton droit sur la solution, puis générez-la.</span><span class="sxs-lookup"><span data-stu-id="5be83-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="5be83-200">Cliquez sur le **CodedClient** de projet et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="5be83-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="5be83-201">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="5be83-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="5be83-202">Pour exécuter le client du concepteur</span><span class="sxs-lookup"><span data-stu-id="5be83-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="5be83-203">Ouvrez PowerShell.sln à l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be83-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5be83-204">Cliquez avec le bouton droit sur la solution, puis générez-la.</span><span class="sxs-lookup"><span data-stu-id="5be83-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="5be83-205">Cliquez sur le **DesignerClient** de projet et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="5be83-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="5be83-206">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="5be83-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="5be83-207">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="5be83-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="5be83-208">Si le référencement de l'assembly ou du projet de l'activité `InvokePowerShell` à partir d'un autre projet génère une erreur de build, vous devrez peut-être ajouter manuellement l'élément `<SpecificVersion>True</SpecificVersion>` au fichier .csproj du nouveau projet sous la ligne qui référence `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5be83-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="5be83-209">Si Windows PowerShell n’est pas installé, le message d’erreur suivant s’affiche dans Visual Studio dès que vous ajoutez un `InvokePowerShell` activité sur un flux de travail :`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="5be83-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="5be83-210">Dans Windows PowerShell 2.0, l'appel par programmation de `$input.MoveNext()` échoue et les scripts qui utilisent `$input.MoveNext()` produisent des erreurs et des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="5be83-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="5be83-211">Pour remédier à ce problème, envisagez d'utiliser le verbe PowerShell `foreach` au lieu d'appeler `MoveNext()` lors de l'itération au sein d'un tableau.</span><span class="sxs-lookup"><span data-stu-id="5be83-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5be83-212">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5be83-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5be83-213">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5be83-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5be83-214">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5be83-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5be83-215">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5be83-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`