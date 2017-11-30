---
title: "Procédure : créer un workflow d'organigramme"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 570e51c3b9c8ee227a9c5688fc7caa1b4a0d9c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="6fc53-102">Procédure : créer un workflow d'organigramme</span><span class="sxs-lookup"><span data-stu-id="6fc53-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="6fc53-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6fc53-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6fc53-104">Cette rubrique Guide de création d’un workflow qui utilise les deux activités intégrées, telles que la <xref:System.Activities.Statements.Flowchart> activité et les activités personnalisées à partir de la précédente [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="6fc53-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6fc53-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="6fc53-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fc53-106">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="6fc53-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6fc53-107">Pour terminer cette rubrique, vous devez d’abord terminer [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="6fc53-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fc53-108">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="6fc53-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="6fc53-109">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="6fc53-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="6fc53-110">Avec le bouton droit **NumberGuessWorkflowActivities** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="6fc53-111">Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="6fc53-112">Sélectionnez **activité** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="6fc53-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="6fc53-113">Type `FlowchartNumberGuessWorkflow` dans les **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="6fc53-114">Faites glisser un **organigramme** activité à partir de la **organigramme** section du **boîte à outils** et déposez-la sur le **déposer l’activité ici** étiquette sur le aire de conception de workflow.</span><span class="sxs-lookup"><span data-stu-id="6fc53-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="6fc53-115">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="6fc53-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="6fc53-116">Double-cliquez sur **FlowchartNumberGuessWorkflow.xaml** dans **l’Explorateur de solutions** pour afficher le flux de travail dans le concepteur, si elle n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="6fc53-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="6fc53-117">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="6fc53-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="6fc53-118">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="6fc53-119">Type `MaxNumber` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="6fc53-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="6fc53-120">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="6fc53-121">Type `Turns` dans le **nom** zone ci-dessous récemment ajouté `MaxNumber` argument, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez  **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6fc53-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="6fc53-122">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="6fc53-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="6fc53-123">Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Variables** volet.</span><span class="sxs-lookup"><span data-stu-id="6fc53-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="6fc53-124">Cliquez sur **créer la Variable**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6fc53-125">Si aucun **créer une Variable** s’affiche, cliquez sur le <xref:System.Activities.Statements.Flowchart> activité sur l’aire de Concepteur de flux de travail pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="6fc53-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="6fc53-126">Type `Guess` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="6fc53-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="6fc53-127">Cliquez sur **créer la Variable**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="6fc53-128">Type `Target` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="6fc53-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="6fc53-129">Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Variables** volet.</span><span class="sxs-lookup"><span data-stu-id="6fc53-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="6fc53-130">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="6fc53-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="6fc53-131">Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et placez-la sur le **Démarrer** nœud, qui est en haut de la diagramme de flux.</span><span class="sxs-lookup"><span data-stu-id="6fc53-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="6fc53-132">Lorsque le **affecter** activité se trouve sur le **Démarrer** nœud, trois triangles apparaissent autour de le **Démarrer** nœud.</span><span class="sxs-lookup"><span data-stu-id="6fc53-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="6fc53-133">Supprimer le **affecter** activité sur le triangle qui est directement sous le **Démarrer** nœud.</span><span class="sxs-lookup"><span data-stu-id="6fc53-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="6fc53-134">Cela lie les deux éléments ensemble et désigne le **affecter** activité comme première activité dans le diagramme de flux.</span><span class="sxs-lookup"><span data-stu-id="6fc53-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6fc53-135">Les activités peuvent également être définies comme activité de départ dans le workflow en les liant manuellement au nœud de démarrage.</span><span class="sxs-lookup"><span data-stu-id="6fc53-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="6fc53-136">Pour ce faire, pointez la souris sur le **Démarrer** nœud, cliquez sur un des rectangles qui s’affichent lorsque la souris se trouve sur le **Démarrer** nœud et faites glisser la connexion de la ligne jusqu'à l’activité souhaitée, puis déposez-le sur l’un des les rectangles qui s’affichent.</span><span class="sxs-lookup"><span data-stu-id="6fc53-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="6fc53-137">Vous pouvez également désigner activité en tant qu’activité de départ en cliquant avec le droit de l’informatique et en choisissant **définir en tant que nœud début**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="6fc53-138">Type `Target` dans les **à** boîte et l’expression suivante dans le **entrer une Expression c#** ou **entrer une expression VB** boîte.</span><span class="sxs-lookup"><span data-stu-id="6fc53-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6fc53-139">Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="6fc53-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="6fc53-140">Faites glisser un **invite** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils**, déposez-la au-dessous la **affecter** activité du précédent pas à pas et vous connecter le **invite** activité à la **affecter** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="6fc53-141">Il existe trois façons de connecter les deux activités.</span><span class="sxs-lookup"><span data-stu-id="6fc53-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="6fc53-142">La première consiste à les connecter lorsque vous déposez le **invite** activité sur le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6fc53-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="6fc53-143">Lorsque vous faites glisser le **invite** activité du workflow, placez-la sur le **affecter** activité et déposez-la sur un des quatre triangles qui apparaît lorsque le **invite** activité se trouve sur le **affecter** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="6fc53-144">La seconde consiste à supprimer la **invite** activité sur le flux de travail à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="6fc53-145">Ensuite, pointez la souris sur le **affecter** activité et faites glisser un des rectangles qui apparaît sous le **invite** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="6fc53-146">Faites glisser la souris afin que la ligne de connexion à partir de la **affecter** activité se connecte à un des rectangles de le **invite** activité et relâchez le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="6fc53-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="6fc53-147">La troisième méthode est très similaire à la première, mais au lieu de faire glisser le **invite** activité à partir de la **boîte à outils**, vous faites glisser à partir de son emplacement sur l’aire de conception de workflow, placez-la sur le  **Affecter** activité et déposez-la sur un des triangles qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6fc53-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="6fc53-148">Dans le **fenêtre Propriétés** pour le **invite** activité, type `"EnterGuess"` les guillemets le **BookmarkName** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="6fc53-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="6fc53-149">Type `Guess` dans les **résultat** zone de valeur de propriété et tapez l’expression suivante dans le **texte** zone de propriété.</span><span class="sxs-lookup"><span data-stu-id="6fc53-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6fc53-150">Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="6fc53-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="6fc53-151">Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et connectez-vous à l’aide d’une des méthodes décrites dans l’étape précédente, afin qu’il soit sous la  **Invite de commandes** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="6fc53-152">Type `Turns` dans le **à** boîte et `Turns + 1` dans le **entrer une expression c#** ou **entrer une expression VB** boîte.</span><span class="sxs-lookup"><span data-stu-id="6fc53-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="6fc53-153">Faites glisser un **FlowDecision** à partir de la **organigramme** section de la **boîte à outils** et connectez-la en dessous le **affecter** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="6fc53-154">Dans le **fenêtre Propriétés**, tapez l’expression suivante dans le **Condition** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="6fc53-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="6fc53-155">Faites glisser une autre **FlowDecision** activité à partir de la **boîte à outils** et déposez-le sous le premier.</span><span class="sxs-lookup"><span data-stu-id="6fc53-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="6fc53-156">Connecter les deux activités en faisant glisser le rectangle qui porte le nom **False** en haut **FlowDecision** activité vers le rectangle en haut de la seconde **FlowDecision**activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6fc53-157">Si vous ne voyez pas le **True** et **False** des étiquettes sur le **FlowDecision**, pointez la souris sur le **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="6fc53-158">Cliquez sur le second **FlowDecision** activité pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="6fc53-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="6fc53-159">Dans le **fenêtre Propriétés**, tapez l’expression suivante dans le **Condition** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="6fc53-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="6fc53-160">Faites glisser deux **WriteLine** activités à partir de la **Primitives** section de la **boîte à outils** et déposez-les de sorte qu’elles soient côte à côte sous les deux **FlowDecision**  activités.</span><span class="sxs-lookup"><span data-stu-id="6fc53-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="6fc53-161">Connecter le **True** action du bas **FlowDecision** activité la plus à gauche **WriteLine** activité et le **False** action à la à l’extrême droite **WriteLine** activité.</span><span class="sxs-lookup"><span data-stu-id="6fc53-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="6fc53-162">Cliquez sur le plus à gauche **WriteLine** activité pour la sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété du **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="6fc53-163">Connecter le **WriteLine** sur le côté gauche de la **invite** activité qui est au-dessus de lui.</span><span class="sxs-lookup"><span data-stu-id="6fc53-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="6fc53-164">Cliquez sur le plus à droite **WriteLine** activité pour la sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété du **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6fc53-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="6fc53-165">Connecter le **WriteLine** activité vers la droite de la **invite** activité au-dessus de lui.</span><span class="sxs-lookup"><span data-stu-id="6fc53-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="6fc53-166">L'exemple suivant illustre le flux de travail terminé.</span><span class="sxs-lookup"><span data-stu-id="6fc53-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="6fc53-167">![Fin de Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="6fc53-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="6fc53-168">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="6fc53-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="6fc53-169">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="6fc53-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="6fc53-170">Pour obtenir des instructions sur la façon d’exécuter le flux de travail, consultez la rubrique suivante, [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6fc53-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="6fc53-171">Si vous avez déjà effectué le [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) étape avec un style différent de flux de travail et à exécuter à l’aide du workflow d’organigramme à partir de cette étape, passez directement à la [pour générer et exécuter l’application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)section de [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6fc53-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc53-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fc53-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="6fc53-173">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6fc53-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="6fc53-174">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="6fc53-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="6fc53-175">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="6fc53-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="6fc53-176">Guide pratique pour créer une activité</span><span class="sxs-lookup"><span data-stu-id="6fc53-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="6fc53-177">Guide pratique pour exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="6fc53-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
