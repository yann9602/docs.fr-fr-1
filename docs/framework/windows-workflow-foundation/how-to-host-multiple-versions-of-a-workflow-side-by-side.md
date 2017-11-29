---
title: "Procédure : héberger plusieurs versions d'un workflow côte à côte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 713417131338dd683906eb2de56e615d4aa13c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="85986-102">Procédure : héberger plusieurs versions d'un workflow côte à côte</span><span class="sxs-lookup"><span data-stu-id="85986-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="85986-103">`WorkflowIdentity` permet aux développeurs d'applications de workflow d'associer un nom et une version à une définition de workflow, et d'associer ces informations à une instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="85986-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="85986-104">Ces informations d'identité peuvent être utilisées par les développeurs d'applications de workflow pour activer des scénarios tels que l'exécution côte à côte de plusieurs versions d'une définition de workflow, et fournir la base d'autres fonctionnalités telles que la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="85986-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="85986-105">Cette étape du didacticiel explique comment utiliser `WorkflowIdentity` pour héberger plusieurs versions de workflow en même temps.</span><span class="sxs-lookup"><span data-stu-id="85986-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85986-106">Pour télécharger une version complète ou consulter une procédure pas à pas vidéo du didacticiel, consultez [Windows Workflow Foundation (WF45) - didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="85986-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="85986-107">Dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="85986-107">In this topic</span></span>  
 <span data-ttu-id="85986-108">Dans cette étape du didacticiel, les activités `WriteLine` dans le workflow sont modifiées pour fournir des informations supplémentaires, et une nouvelle activité `WriteLine` est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="85986-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="85986-109">Une copie de l'assembly de workflow d'origine est enregistrée, et l'application hôte est mise à jour afin qu'elle puisse exécuter simultanément les workflows d'origine et mis à jour.</span><span class="sxs-lookup"><span data-stu-id="85986-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="85986-110">Pour effectuer une copie du projet NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="85986-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="85986-111">Pour mettre à jour les flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-111">To update the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="85986-112">Pour mettre à jour le flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-112">To update the StateMachine workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="85986-113">Pour mettre à jour le workflow d’organigramme</span><span class="sxs-lookup"><span data-stu-id="85986-113">To update the Flowchart workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="85986-114">Pour mettre à jour le flux de travail séquentiel</span><span class="sxs-lookup"><span data-stu-id="85986-114">To update the Sequential workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="85986-115">Pour mettre à jour workflowversionmap de façon à inclure les versions précédentes de flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="85986-116">Pour générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="85986-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="85986-117">Avant de suivre les étapes de cette rubrique, exécutez l'application, démarrez plusieurs workflows de chaque type et effectuez une ou deux propositions pour chacun.</span><span class="sxs-lookup"><span data-stu-id="85986-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="85986-118">Ces workflows persistants sont utilisés dans cette étape et l’étape suivante, [Comment : mettre à jour la définition d’une Instance de Workflow en cours d’exécution](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="85986-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85986-119">Chaque étape du didacticiel de mise en route dépend des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="85986-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="85986-120">Si vous n’avez pas effectué les étapes précédentes, vous pouvez télécharger une version complète du didacticiel à partir de [Windows Workflow Foundation (WF45) - didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="85986-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
###  <span data-ttu-id="85986-121"><a name="BKMK_BackupCopy"></a>Pour effectuer une copie du projet NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="85986-121"><a name="BKMK_BackupCopy"></a> To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1.  <span data-ttu-id="85986-122">Ouvrez le **WF45GettingStartedTutorial** solution dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] s’il n’est pas ouvert.</span><span class="sxs-lookup"><span data-stu-id="85986-122">Open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] if it is not open.</span></span>  
  
2.  <span data-ttu-id="85986-123">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="85986-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="85986-124">Fermer le **WF45GettingStartedTutorial** solution.</span><span class="sxs-lookup"><span data-stu-id="85986-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4.  <span data-ttu-id="85986-125">Ouvrez l’Explorateur Windows et accédez au répertoire dans lequel le fichier solution du didacticiel et les dossiers du projet sont situés.</span><span class="sxs-lookup"><span data-stu-id="85986-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5.  <span data-ttu-id="85986-126">Créez un dossier nommé **PreviousVersions** dans le même dossier que **NumberGuessWorkflowHost** et **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="85986-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="85986-127">Ce dossier est utilisé pour contenir les assemblys qui contiennent les différentes versions de workflow utilisées dans les étapes du didacticiel suivantes.</span><span class="sxs-lookup"><span data-stu-id="85986-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6.  <span data-ttu-id="85986-128">Accédez à la **NumberGuessWorkflowActivities\bin\debug** dossier (ou **bin\release** selon les paramètres du projet).</span><span class="sxs-lookup"><span data-stu-id="85986-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="85986-129">Copie **NumberGuessWorkflowActivities.dll** et collez-le dans le **PreviousVersions** dossier.</span><span class="sxs-lookup"><span data-stu-id="85986-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7.  <span data-ttu-id="85986-130">Renommer **NumberGuessWorkflowActivities.dll** dans les **PreviousVersions** dossier **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="85986-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85986-131">Les étapes de cette rubrique illustrent une façon de gérer les assemblys utilisés pour contenir plusieurs versions de workflow.</span><span class="sxs-lookup"><span data-stu-id="85986-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="85986-132">D'autres méthodes, telles que celles d'attribution de nom fort aux assemblys et d'inscription des assemblys dans le Global Assembly Cache peuvent également être utilisées.</span><span class="sxs-lookup"><span data-stu-id="85986-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>  
  
8.  <span data-ttu-id="85986-133">Créez un dossier nommé **NumberGuessWorkflowActivities_du** dans le même dossier que **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**et qui vient d’être ajouté **PreviousVersions** dossier, puis copiez tous les fichiers et sous-dossiers à partir de la **NumberGuessWorkflowActivities** dossier dans le nouvel  **NumberGuessWorkflowActivities_du** dossier.</span><span class="sxs-lookup"><span data-stu-id="85986-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="85986-134">Cette copie de sauvegarde du projet pour la version initiale des activités est utilisée dans [Comment : mettre à jour la définition d’une Instance de Workflow en cours d’exécution](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="85986-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
9. <span data-ttu-id="85986-135">Ouvrez à nouveau le **WF45GettingStartedTutorial** solution dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85986-135">Re-open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
###  <span data-ttu-id="85986-136"><a name="BKMK_UpdateWorkflows"></a>Pour mettre à jour les flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-136"><a name="BKMK_UpdateWorkflows"></a> To update the workflows</span></span>  
 <span data-ttu-id="85986-137">Dans cette section, les définitions de workflow sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="85986-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="85986-138">Les deux activités `WriteLine` qui fournissent des commentaires sur la proposition de l'utilisateur sont mises à jour, et une nouvelle activité `WriteLine`, qui fournit des informations supplémentaires sur le jeu une fois que le nombre est deviné, est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="85986-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>  
  
####  <span data-ttu-id="85986-139"><a name="BKMK_UpdateStateMachine"></a>Pour mettre à jour le flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-139"><a name="BKMK_UpdateStateMachine"></a> To update the StateMachine workflow</span></span>  
  
1.  <span data-ttu-id="85986-140">Dans **l’Explorateur de solutions**, sous le **NumberGuessWorkflowActivities** de projet, double-cliquez sur **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="85986-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="85986-141">Double-cliquez sur le **Guess Incorrect** transition sur l’ordinateur d’état.</span><span class="sxs-lookup"><span data-stu-id="85986-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>  
  
3.  <span data-ttu-id="85986-142">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="85986-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  <span data-ttu-id="85986-143">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="85986-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  <span data-ttu-id="85986-144">Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="85986-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
6.  <span data-ttu-id="85986-145">Double-cliquez sur le **Guess Correct** transition sur l’ordinateur d’état.</span><span class="sxs-lookup"><span data-stu-id="85986-145">Double-click the **Guess Correct** transition on the state machine.</span></span>  
  
7.  <span data-ttu-id="85986-146">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la sur la **activité déposer l’Action ici** étiquette de la transition.</span><span class="sxs-lookup"><span data-stu-id="85986-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>  
  
8.  <span data-ttu-id="85986-147">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="85986-147">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <span data-ttu-id="85986-148"><a name="BKMK_UpdateFlowchart"></a>Pour mettre à jour le workflow d’organigramme</span><span class="sxs-lookup"><span data-stu-id="85986-148"><a name="BKMK_UpdateFlowchart"></a> To update the Flowchart workflow</span></span>  
  
1.  <span data-ttu-id="85986-149">Dans **l’Explorateur de solutions**, sous le **NumberGuessWorkflowActivities** de projet, double-cliquez sur **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="85986-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="85986-150">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="85986-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="85986-151">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite.</span><span class="sxs-lookup"><span data-stu-id="85986-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="85986-152">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la sur le point de dépôt de la `True` action du plus haut `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="85986-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="85986-153">L'activité `WriteLine` est ajoutée à l'organigramme et liée à l'action `True` de `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="85986-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>  
  
5.  <span data-ttu-id="85986-154">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="85986-154">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <span data-ttu-id="85986-155"><a name="BKMK_UpdateSequential"></a>Pour mettre à jour le flux de travail séquentiel</span><span class="sxs-lookup"><span data-stu-id="85986-155"><a name="BKMK_UpdateSequential"></a> To update the Sequential workflow</span></span>  
  
1.  <span data-ttu-id="85986-156">Dans **l’Explorateur de solutions**, sous le **NumberGuessWorkflowActivities** de projet, double-cliquez sur **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="85986-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="85986-157">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="85986-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="85986-158">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="85986-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="85986-159">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la après le **DoWhile** activité afin que le  **WriteLine** est la dernière activité de la racine `Sequence` activité.</span><span class="sxs-lookup"><span data-stu-id="85986-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>  
  
5.  <span data-ttu-id="85986-160">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="85986-160">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <span data-ttu-id="85986-161"><a name="BKMK_UpdateWorkflowVersionMap"></a>Pour mettre à jour workflowversionmap de façon à inclure les versions précédentes de flux de travail</span><span class="sxs-lookup"><span data-stu-id="85986-161"><a name="BKMK_UpdateWorkflowVersionMap"></a> To update WorkflowVersionMap to include the previous workflow versions</span></span>  
  
1.  <span data-ttu-id="85986-162">Double-cliquez sur **WorkflowVersionMap.cs** (ou **WorkflowVersionMap.vb**) sous le **NumberGuessWorkflowHost** pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="85986-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
2.  <span data-ttu-id="85986-163">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="85986-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="85986-164">Ajoutez trois nouvelles identités de workflow juste au-dessous des trois déclarations d'identité de workflow existantes.</span><span class="sxs-lookup"><span data-stu-id="85986-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="85986-165">Ces nouvelles identités de workflow `v1` seront utilisées pour fournir la définition appropriée de workflow aux workflows démarrés avant que les mises à jour aient été effectuées.</span><span class="sxs-lookup"><span data-stu-id="85986-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 Identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
    ```  
  
    ```csharp  
    // Current version identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity;  
    static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
    // v1 identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
    ```  
  
4.  <span data-ttu-id="85986-166">Dans le constructeur `WorkflowVersionMap`, mettez à jour la propriété `Version` des trois identités actuelles de workflow vers `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="85986-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>  
  
    ```vb  
    'Add the current workflow version identities.  
    StateMachineNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
    ```  
  
    ```csharp  
    // Add the current workflow version identities.  
    StateMachineNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
    ```  
  
     <span data-ttu-id="85986-167">Le code qui ajoute les versions actuelles des workflow au dictionnaire utilise les versions actuelles qui sont référencées dans le projet ainsi, le code qui initialise les définitions de workflow n'a pas besoin d'être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="85986-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>  
  
5.  <span data-ttu-id="85986-168">Ajoutez le code suivant dans le constructeur juste après le code qui ajoute les versions actuelles au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="85986-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>  
  
    ```vb  
    'Initialize the previous workflow version identities.  
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
    ```  
  
    ```csharp  
    // Initialize the previous workflow version identities.  
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
    ```  
  
     <span data-ttu-id="85986-169">Ces identités de workflow sont associées aux versions initiales des définitions correspondantes de workflow.</span><span class="sxs-lookup"><span data-stu-id="85986-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>  
  
6.  <span data-ttu-id="85986-170">Ensuite, chargez l'assembly qui contient la première version des définitions de workflow, puis créez et ajoutez des définitions correspondantes de workflow au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="85986-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>  
  
    ```vb  
    'Add the previous version workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v1 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Add the previous version workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v1 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     <span data-ttu-id="85986-171">L'exemple suivant constitue l'intégralité de la classe `WorkflowVersionMap` mise à jour.</span><span class="sxs-lookup"><span data-stu-id="85986-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 Identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
  
            'Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            'Add the previous version workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v1 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        // v1 identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
  
            // Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            // Add the previous version workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v1 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {  
            return identity.ToString();  
        }  
    }  
    ```  
  
###  <span data-ttu-id="85986-172"><a name="BKMK_BuildAndRun"></a>Pour générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="85986-172"><a name="BKMK_BuildAndRun"></a> To build and run the application</span></span>  
  
1.  <span data-ttu-id="85986-173">Appuyez sur Ctrl+Maj+B pour générer l'application, puis sur Ctrl+F5 pour démarrer.</span><span class="sxs-lookup"><span data-stu-id="85986-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>  
  
2.  <span data-ttu-id="85986-174">Démarrer un nouveau flux de travail en cliquant sur **nouvelle partie**.</span><span class="sxs-lookup"><span data-stu-id="85986-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="85986-175">La version du workflow s'affiche dans la fenêtre d'état et reflète la version mise à jour du `WorkflowIdentity` associé.</span><span class="sxs-lookup"><span data-stu-id="85986-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="85986-176">Notez `InstanceId` de façon à afficher le fichier de suivi du workflow lorsqu'il se termine, puis entrez des propositions jusqu'à ce que le jeu soit terminé.</span><span class="sxs-lookup"><span data-stu-id="85986-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="85986-177">Notez comment la proposition de l'utilisateur est affichée dans les informations affichées dans la fenêtre d'état basée sur les mises à jour dans les activités `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="85986-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>  
  
 <span data-ttu-id="85986-178">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="85986-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="85986-179">**5 est trop élevée.** </span><span class="sxs-lookup"><span data-stu-id="85986-179">**5 is too high.** </span></span>  
<span data-ttu-id="85986-180">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-180">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-181">**3 est trop élevé.** </span><span class="sxs-lookup"><span data-stu-id="85986-181">**3 is too high.** </span></span>  
<span data-ttu-id="85986-182">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-182">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-183">**1 est trop faible.** </span><span class="sxs-lookup"><span data-stu-id="85986-183">**1 is too low.** </span></span>  
<span data-ttu-id="85986-184">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-184">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-185">**Félicitations, vous avez deviné le nombre en 4 tours.**</span><span class="sxs-lookup"><span data-stu-id="85986-185">**Congratulations, you guessed the number in 4 turns.**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="85986-186">Le texte mis à jour à partir des activités `WriteLine` s'affiche, mais la sortie de l'activité finale `WriteLine` ajoutée dans cette rubrique ne s'affiche pas.</span><span class="sxs-lookup"><span data-stu-id="85986-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="85986-187">Cela est dû au fait que la fenêtre d'état est mise à jour par le gestionnaire `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="85986-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="85986-188">Étant donné que le workflow se termine et n'est pas inactif après l'activité finale, le gestionnaire `PersistableIdle` n'est pas appelé.</span><span class="sxs-lookup"><span data-stu-id="85986-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="85986-189">Toutefois, un message similaire est affiché dans la fenêtre d'état par le gestionnaire `Completed`.</span><span class="sxs-lookup"><span data-stu-id="85986-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="85986-190">Si vous le souhaitez, le code peut être ajouté au gestionnaire `Completed` pour extraire le texte de `StringWriter` et pour l'afficher dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="85986-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>  
  
3.  <span data-ttu-id="85986-191">Ouvrez l’Explorateur Windows et accédez à la **NumberGuessWorkflowHost\bin\debug** dossier (ou **bin\release** selon les paramètres du projet) et ouvrez le fichier de suivi à l’aide du bloc-notes qui correspond le flux de travail terminé.</span><span class="sxs-lookup"><span data-stu-id="85986-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="85986-192">Si vous n’avez pas effectué une note de la `InstanceId`, vous pouvez identifier le fichier de suivi approprié à l’aide de la **Date de modification** informations dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="85986-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>  
  
 <span data-ttu-id="85986-193">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="85986-193">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="85986-194">**5 est trop élevée.** </span><span class="sxs-lookup"><span data-stu-id="85986-194">**5 is too high.** </span></span>  
<span data-ttu-id="85986-195">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-195">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-196">**3 est trop élevé.** </span><span class="sxs-lookup"><span data-stu-id="85986-196">**3 is too high.** </span></span>  
<span data-ttu-id="85986-197">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-197">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-198">**1 est trop faible.** </span><span class="sxs-lookup"><span data-stu-id="85986-198">**1 is too low.** </span></span>  
<span data-ttu-id="85986-199">**Entrez un nombre compris entre 1 et 10** </span><span class="sxs-lookup"><span data-stu-id="85986-199">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="85986-200">**2 est correct. Vous avez deviné en 4 tours.**</span><span class="sxs-lookup"><span data-stu-id="85986-200">**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="85986-201">La sortie mise à jour `WriteLine` est contenue dans le fichier de trace, y compris la sortie `WriteLine` ajoutée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="85986-201">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>  
  
4.  <span data-ttu-id="85986-202">Revenez à l'application d'estimation de nombre et sélectionnez l'un des workflows qui a été démarré avant que les mises à jour n'aient été effectuées.</span><span class="sxs-lookup"><span data-stu-id="85986-202">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="85986-203">Vous pouvez identifier la version du workflow actuellement sélectionné en examinant les informations de version qui s'affichent sous la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="85986-203">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="85986-204">Entrez des propositions et notez que les mises à jour d'état correspondent à la sortie d'activité `WriteLine` de la version antérieure, et n'incluez pas l'estimation de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="85986-204">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="85986-205">Cela est dû au fait que ces workflows utilisent la définition de workflow précédente qui n'a pas les mises à jour de `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="85986-205">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>  
  
     <span data-ttu-id="85986-206">Dans l’étape suivante, [Comment : mettre à jour la définition d’une Instance de Workflow en cours d’exécution](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), l’exécution `v1` les instances de flux de travail sont mis à jour afin qu’ils contiennent les nouvelles fonctionnalités comme le `v2` instances.</span><span class="sxs-lookup"><span data-stu-id="85986-206">In the next step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
