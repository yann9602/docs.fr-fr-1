---
title: "Scénario StateMachine à l'aide d'une combinaison de FlowChart et de Pick"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0fb0364310c8780dd41c5369e6b1851dee668d15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="34216-102">Scénario StateMachine à l'aide d'une combinaison de FlowChart et de Pick</span><span class="sxs-lookup"><span data-stu-id="34216-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="34216-103">Cet exemple montre comment implémenter un scénario de chronomètre simple à l'aide d'une combinaison des activités <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="34216-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="34216-104">Il utilise Receive et Send dans l'activité Pick pour écouter des événements de chronomètre.</span><span class="sxs-lookup"><span data-stu-id="34216-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34216-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="34216-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34216-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="34216-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="34216-107">Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34216-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34216-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="34216-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="34216-109">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="34216-109">Sample Details</span></span>  
 <span data-ttu-id="34216-110">Le tableau suivant répertorie les projets compris dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="34216-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="34216-111">Nom du projet</span><span class="sxs-lookup"><span data-stu-id="34216-111">Project Name</span></span>|<span data-ttu-id="34216-112">Description</span><span class="sxs-lookup"><span data-stu-id="34216-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="34216-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="34216-113">StopWatchService</span></span>|<span data-ttu-id="34216-114">Ce projet contient l'implémentation d'une machine à états pour l'exemple de chronomètre à l'aide d'une combinaison des activités <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="34216-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="34216-115">L'activité <xref:System.Activities.Statements.Pick> a 3 instructions <xref:System.Activities.Statements.PickBranch> dans la propriété <xref:System.Activities.Statements.Pick.Branches%2A> qui écoutent les événements `GetStart`, `GetStop` et `GetOff`.</span><span class="sxs-lookup"><span data-stu-id="34216-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="34216-116">En fonction de l'événement entrant, les déclencheurs pour l'une des branches s'activent et la propriété <xref:System.Activities.Statements.PickBranch.Action%2A> correspondante est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="34216-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="34216-117">Dans la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>, il y a une instruction <xref:System.Activities.Statements.Switch%601> qui évalue si la transition est une transition légitime, et si tel est le cas, la propriété `currentState` est mise à jour avec l'état de transition et envoyée au client.</span><span class="sxs-lookup"><span data-stu-id="34216-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="34216-118">L'activité <xref:System.Activities.Statements.FlowDecision> à la fin de <xref:System.Activities.Statements.Flowchart> évalue la propriété `currentState` pour déterminer si l'état est terminal.</span><span class="sxs-lookup"><span data-stu-id="34216-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="34216-119">Si tel est le cas, le workflow se termine ; sinon, le contrôle revient au début de l'activité <xref:System.Activities.Statements.Pick> où le workflow attend des événements de chronomètre supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="34216-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="34216-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="34216-120">StopWatchClient</span></span>|<span data-ttu-id="34216-121">Il s'agit d'une application console de workflow séquentiel simple qui envoie différents événements de chronomètre avec des combinaisons de Send ou de Receive simples.</span><span class="sxs-lookup"><span data-stu-id="34216-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="34216-122">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="34216-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="34216-123">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution StateMachineWithPick.sln.</span><span class="sxs-lookup"><span data-stu-id="34216-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="34216-124">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="34216-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="34216-125">Démarrez StopWatchService.exe de [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] en tant qu’administrateur en cliquant avec le bouton droit sur le fichier .exe et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="34216-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="34216-126">Accédez au dossier StateMachineWithPick\CS\StopWatchService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="34216-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="34216-127">Cliquez sur le fichier StopWatchService.exe, puis sélectionnez **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="34216-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="34216-128">Démarrez l'application cliente StopWatchClient à partir de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34216-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="34216-129">Dans **l’Explorateur de solutions**, sélectionnez le **StopWatchClient** de projet et avec le bouton droit **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="34216-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="34216-130">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="34216-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="34216-131">Revenez à la fenêtre de console de StopWatchService.exe pour voir les transitions d'état.</span><span class="sxs-lookup"><span data-stu-id="34216-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34216-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="34216-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34216-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="34216-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="34216-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34216-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34216-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="34216-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="see-also"></a><span data-ttu-id="34216-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34216-136">See Also</span></span>
