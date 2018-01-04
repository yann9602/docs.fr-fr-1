---
title: "Procédure : créer un workflow d'ordinateur d'état"
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
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95ba37b123b57ba9f86fefb55a860fb2122ccd3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="ad7a5-102">Procédure : créer un workflow d'ordinateur d'état</span><span class="sxs-lookup"><span data-stu-id="ad7a5-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="ad7a5-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="ad7a5-104">Cette rubrique Guide de création d’un workflow qui utilise les deux activités intégrées, telles que la <xref:System.Activities.Statements.StateMachine> activité et les activités personnalisées à partir de la précédente [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="ad7a5-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad7a5-106">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="ad7a5-107">Pour terminer cette rubrique, vous devez d’abord terminer [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="ad7a5-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad7a5-108">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="ad7a5-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="ad7a5-109">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="ad7a5-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="ad7a5-110">Avec le bouton droit **NumberGuessWorkflowActivities** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="ad7a5-111">Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="ad7a5-112">Sélectionnez **activité** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="ad7a5-113">Type `StateMachineNumberGuessWorkflow` dans les **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="ad7a5-114">Faites glisser un **StateMachine** activité à partir de la **Machine à états** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette sur l’aire de conception de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="ad7a5-115">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="ad7a5-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="ad7a5-116">Double-cliquez sur **StateMachineNumberGuessWorkflow.xaml** dans **l’Explorateur de solutions** pour afficher le flux de travail dans le concepteur, si elle n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="ad7a5-117">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="ad7a5-118">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="ad7a5-119">Type `MaxNumber` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="ad7a5-120">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="ad7a5-121">Type `Turns` dans le **nom** zone ci-dessous récemment ajouté `MaxNumber` argument, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez  **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="ad7a5-122">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="ad7a5-123">Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Variables** volet.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="ad7a5-124">Cliquez sur **créer la Variable**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ad7a5-125">Si aucun **créer une Variable** s’affiche, cliquez sur le <xref:System.Activities.Statements.StateMachine> activité sur l’aire de Concepteur de flux de travail pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="ad7a5-126">Type `Guess` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="ad7a5-127">Cliquez sur **créer la Variable**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="ad7a5-128">Type `Target` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="ad7a5-129">Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Variables** volet.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="ad7a5-130">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="ad7a5-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="ad7a5-131">Cliquez sur **State1** pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-131">Click **State1** to select it.</span></span> <span data-ttu-id="ad7a5-132">Dans le **fenêtre Propriétés**, modifiez le **DisplayName** à `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ad7a5-133">Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ad7a5-134">Double-cliquez sur récemment renommé **Initialize Target** état dans le Concepteur de flux de travail pour le développer.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="ad7a5-135">Faites glisser une **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **entrée** section de l’état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="ad7a5-136">Type `Target` dans les **à** boîte et l’expression suivante dans le **entrer une expression c#** ou **entrer une expression VB** boîte.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="ad7a5-137">Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="ad7a5-138">Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="ad7a5-139">Faites glisser un **état** activité à partir de la **Machine à états** section de la **boîte à outils** sur le Concepteur de flux de travail et placez-la sur le **Initialize Target** état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="ad7a5-140">Notez que quatre triangles apparaissent autour de le **Initialize Target** état lorsque le nouvel état est dessus.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="ad7a5-141">Déposez le nouvel état sur le triangle qui est immédiatement au-dessous du **Initialize Target** état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="ad7a5-142">Cela place le nouvel état sur le flux de travail et crée une transition à partir de la **Initialize Target** le nouvel état de l’état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="ad7a5-143">Cliquez sur **State1** pour le sélectionner, remplacez le **DisplayName** à `Enter Guess`, puis double-cliquez sur l’état dans le Concepteur de flux de travail pour le développer.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="ad7a5-144">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **entrée** section de l’état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="ad7a5-145">Tapez l’expression suivante dans le **texte** zone de la propriété de la **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="ad7a5-146">Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la dans le **quitter** section de l’état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="ad7a5-147">Type `Turns` dans le **à** boîte et `Turns + 1` dans le **entrer une expression c#** ou **entrer une expression VB** boîte.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="ad7a5-148">Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="ad7a5-149">Faites glisser un **FinalState** activité à partir de la **Machine à états** section de la **boîte à outils**, placez-la sur le **entrer l’estimation** d’état, puis déposez-la sur le triangle qui apparaît à droite de la **Enter Guess** afin que la création d’une transition entre l’état **Enter Guess** et **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="ad7a5-150">Le nom par défaut de la transition est **T2**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="ad7a5-151">Cliquez sur la transition dans le Concepteur de flux de travail pour la sélectionner, puis définir ses **DisplayName** à **Guess Correct**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="ad7a5-152">Puis cliquez sur le **FinalState**et faites-le glisser vers la droite afin qu’il y pour le nom complet de transition sans recouvrir un des deux États.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="ad7a5-153">Cela facilitera l'exécution des autres étapes du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="ad7a5-154">Double-cliquez sur récemment renommé **Guess Correct** transition dans le Concepteur de flux de travail pour le développer.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="ad7a5-155">Faites glisser un **ReadInt** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-la dans le **déclencheur** section de la transition.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="ad7a5-156">Dans le **fenêtre Propriétés** pour le **ReadInt** activité, type `"EnterGuess"` les guillemets le **BookmarkName** zone de valeur de propriété et `Guess`dans les **résultat** zone de valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="ad7a5-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="ad7a5-157">Tapez l’expression suivante dans le **Guess Correct** de transition **Condition** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="ad7a5-158">Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad7a5-159">Une transition se produit lorsque l'événement déclencheur est reçu et <xref:System.Activities.Statements.Transition.Condition%2A>, s'il est présent, prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="ad7a5-160">Pour cette transition, si l’utilisateur `Guess` correspond à généré de manière aléatoire `Target`, puis le contrôle passe à la **FinalState** et le workflow se termine.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="ad7a5-161">Selon que l’estimation est correcte, le flux de travail doit passer à la **FinalState** ou revenir à la **entrer une estimation** l’état d’un autre bloc try.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="ad7a5-162">Les deux transitions partagent le même déclencheur d’attente d’estimation de l’utilisateur doit être reçu via le **ReadInt** activité.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="ad7a5-163">Il s'agit d'une transition partagée.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-163">This is called a shared transition.</span></span> <span data-ttu-id="ad7a5-164">Pour créer une transition partagée, cliquez sur le cercle qui indique le début de la **Guess Correct** de transition et faites-le glisser vers l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="ad7a5-165">Dans ce cas la transition est une transition automatique, par conséquent, faites glisser le point de départ de la **Guess Correct** de transition et déposez-le vers le bas de la **Enter Guess** état.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="ad7a5-166">Après avoir créé la transition, sélectionnez-la dans le Concepteur de flux de travail et définissez son **DisplayName** propriété **Guess Incorrect**.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad7a5-167">Des transitions partagées peuvent également être créées à partir du Concepteur de transition en cliquant sur **ajouter une transition de déclencheur partagée** au bas du Concepteur de transition, puis en sélectionnant l’état cible souhaité dans le  **Les états disponibles pour la connexion** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad7a5-168">Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `false` (ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `false`), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="ad7a5-169">Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées (il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte).</span><span class="sxs-lookup"><span data-stu-id="ad7a5-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="ad7a5-170">Double-cliquez sur le **Guess Incorrect** transition dans le Concepteur de flux de travail pour le développer.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="ad7a5-171">Notez que la **déclencheur** est déjà défini sur le même **ReadInt** activité qui a été utilisé par le **Guess Correct** transition.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="ad7a5-172">Tapez l’expression suivante dans le **Condition** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="ad7a5-173">Faites glisser un **si** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la dans le **Action** section de la transition.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="ad7a5-174">Tapez l’expression suivante dans le **si** l’activité **Condition** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="ad7a5-175">Faites glisser deux **WriteLine** activités à partir de la **Primitives** section de la **boîte à outils** et déposez-les de sorte qu’un est dans le **puis** section de le **si** activité et l’autre est dans le **Else** section.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="ad7a5-176">Cliquez sur le **WriteLine** activité dans le **puis** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="ad7a5-177">Cliquez sur le **WriteLine** activité dans le **Else** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="ad7a5-178">Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="ad7a5-179">L'exemple suivant illustre le flux de travail terminé.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="ad7a5-180">![Flux de travail de Machine d’état terminé](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="ad7a5-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="ad7a5-181">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="ad7a5-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="ad7a5-182">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="ad7a5-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="ad7a5-183">Pour obtenir des instructions sur la façon d’exécuter le flux de travail, consultez la rubrique suivante, [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ad7a5-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="ad7a5-184">Si vous avez déjà effectué le [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) étape avec un style différent de flux de travail et à exécuter en utilisant le workflow de machine d’état à partir de cette étape, passez directement à la [pour générer et exécuter l’application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section de [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ad7a5-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7a5-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad7a5-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="ad7a5-186">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="ad7a5-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="ad7a5-187">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="ad7a5-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="ad7a5-188">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="ad7a5-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="ad7a5-189">Guide pratique pour créer une activité</span><span class="sxs-lookup"><span data-stu-id="ad7a5-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="ad7a5-190">Guide pratique pour exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="ad7a5-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
