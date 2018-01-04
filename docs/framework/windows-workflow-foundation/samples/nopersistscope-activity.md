---
title: "Activité NoPersistScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc651403988fa7558f79a4c99e42fb776efec4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="631b0-102">Activité NoPersistScope</span><span class="sxs-lookup"><span data-stu-id="631b0-102">NoPersistScope Activity</span></span>
<span data-ttu-id="631b0-103">Cet exemple montre comment manipuler un état non sérialisable et supprimable dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="631b0-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="631b0-104">Il est important que les workflows n'essaient pas de rendre l'état non sérialisable persistant et il est également important de nettoyer les objets supprimables après qu'ils ont été utilisés dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="631b0-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="631b0-105">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="631b0-105">Demonstrates</span></span>  
 <span data-ttu-id="631b0-106">Concepteur et activité personnalisée `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="631b0-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="631b0-107">Utilisation de l'activité NoPersistZone</span><span class="sxs-lookup"><span data-stu-id="631b0-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="631b0-108">Lors de l'exécution de l'exemple de workflow, une activité personnalisée appelée `CreateTextWriter` crée un objet de type <xref:System.IO.TextWriter> et l'enregistre dans une variable de workflow.</span><span class="sxs-lookup"><span data-stu-id="631b0-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="631b0-109"><xref:System.IO.TextWriter> est un objet <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="631b0-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="631b0-110">Ce <xref:System.IO.TextWriter>, configuré pour écrire dans un fichier nommé « out.txt » dans le répertoire dans lequel l'exemple s'exécute, est utilisé par une activité <xref:System.Activities.Statements.WriteLine> lors de l'écho de tout texte que vous entrez au niveau de la console.</span><span class="sxs-lookup"><span data-stu-id="631b0-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="631b0-111">La logique d'écho est exécutée dans une activité `NoPersistScope` (le code associé fait également partie de cet exemple), qui empêche de rendre le workflow persistant.</span><span class="sxs-lookup"><span data-stu-id="631b0-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="631b0-112">Si vous tapez dans `unload` à la console, l’hôte tente de conserver l’instance de workflow, mais cette opération arrive à expiration, car le flux de travail reste dans un `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="631b0-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="631b0-113">Le workflow utilise également une activité personnalisée appelée `Dispose` pour supprimer l'objet <xref:System.IO.TextWriter> lorsque le workflow a fini de l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="631b0-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="631b0-114">L'activité `Dispose` est placée dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A> de l'activité <xref:System.Activities.Statements.TryCatch> où la variable <xref:System.IO.TextWriter> est déclarée pour garantir son exécution même si une exception devait se produire pendant l'exécution du bloc Try.</span><span class="sxs-lookup"><span data-stu-id="631b0-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="631b0-115">Vous pouvez taper dans `exit` pour terminer l’instance de workflow et de quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="631b0-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="631b0-116">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="631b0-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="631b0-117">Ouvrez la solution NoPersistZone.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="631b0-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="631b0-118">Pour générer la solution, appuyez sur CTRL + MAJ + B ou sélectionnez **générer la Solution** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="631b0-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="631b0-119">Une fois la génération a réussi, appuyez sur F5 ou sélectionnez **démarrer le débogage** à partir de la **déboguer** menu ou bien, vous pouvez appuyer sur CTRL + F5 ou sélectionnez **démarrer sans débogage** à partir de la **Déboguer** menu pour exécuter sans débogage.</span><span class="sxs-lookup"><span data-stu-id="631b0-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="631b0-120">Pour effectuer un nettoyage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="631b0-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="631b0-121">Pour supprimer le magasin d'instances SQL, exécutez Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="631b0-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="631b0-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="631b0-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="631b0-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="631b0-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="631b0-124">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="631b0-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="631b0-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="631b0-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`