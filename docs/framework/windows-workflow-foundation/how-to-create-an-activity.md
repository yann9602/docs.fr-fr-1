---
title: "Procédure : créer une activité"
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26385d91b4201820a5f6ba77b512e7bcfd5372c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="1116b-102">Procédure : créer une activité</span><span class="sxs-lookup"><span data-stu-id="1116b-102">How to: Create an Activity</span></span>
<span data-ttu-id="1116b-103">Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1116b-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="1116b-104">La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="1116b-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="1116b-105">Cette rubrique indique comment créer deux activités.</span><span class="sxs-lookup"><span data-stu-id="1116b-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="1116b-106">La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1116b-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="1116b-107">L'implémentation de la deuxième activité est définie à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="1116b-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="1116b-108">Ces activités sont utilisées dans les procédures du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1116b-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1116b-109">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="1116b-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="1116b-110">Pour créer le projet de bibliothèque d'activités</span><span class="sxs-lookup"><span data-stu-id="1116b-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="1116b-111">Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et choisissez **nouveau**, **projet** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="1116b-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="1116b-112">Développez le **autres Types de projets** nœud dans le **installé**, **modèles** et **Solutions Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1116b-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="1116b-113">Sélectionnez **nouvelle Solution** à partir de la **Solutions Visual Studio** liste.</span><span class="sxs-lookup"><span data-stu-id="1116b-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="1116b-114">Dans la liste déroulante de la version du .NET Framework, vérifiez que **.NET Framework 4.5** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1116b-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="1116b-115">Type `WF45GettingStartedTutorial` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1116b-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="1116b-116">Avec le bouton droit **WF45GettingStartedTutorial** dans **l’Explorateur de solutions** et choisissez **ajouter**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1116b-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1116b-117">Si la fenêtre **Explorateur de solutions** n'est pas affichée, sélectionnez **Explorateur de solutions** dans le menu **Affichage** .</span><span class="sxs-lookup"><span data-stu-id="1116b-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="1116b-118">Dans le nœud **Installé** , sélectionnez **Visual C#**, **Workflow** (ou **Visual Basic**, **Workflow**).</span><span class="sxs-lookup"><span data-stu-id="1116b-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="1116b-119">Vérifiez que **.NET Framework 4.5** est sélectionné dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] liste déroulante de la version.</span><span class="sxs-lookup"><span data-stu-id="1116b-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="1116b-120">Sélectionnez **bibliothèque d’activités** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="1116b-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="1116b-121">Type `NumberGuessWorkflowActivities` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1116b-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1116b-122">En fonction du langage de programmation qui est configuré comme langage principal dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], le **Visual C#** ou **Visual Basic** nœud peut se trouver sous le **autres langages**nœud dans le **installé** nœud.</span><span class="sxs-lookup"><span data-stu-id="1116b-122">Depending on which programming language is configured as the primary language in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="1116b-123">Avec le bouton droit **Activity1.xaml** dans **l’Explorateur de solutions** et choisissez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="1116b-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="1116b-124">Pour confirmer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="1116b-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="1116b-125">Pour créer l'activité ReadInt</span><span class="sxs-lookup"><span data-stu-id="1116b-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="1116b-126">Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="1116b-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="1116b-127">Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="1116b-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1116b-128">Sélectionnez **activité de Code** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="1116b-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="1116b-129">Type `ReadInt` dans les **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1116b-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="1116b-130">Remplacez la définition `ReadInt` existante par la définition suivante.</span><span class="sxs-lookup"><span data-stu-id="1116b-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1116b-131">L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code.</span><span class="sxs-lookup"><span data-stu-id="1116b-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="1116b-132"><xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1116b-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="1116b-133">Pour créer l'activité Prompt</span><span class="sxs-lookup"><span data-stu-id="1116b-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="1116b-134">Appuyez sur CTRL+MAJ+B pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="1116b-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="1116b-135">La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.</span><span class="sxs-lookup"><span data-stu-id="1116b-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="1116b-136">Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="1116b-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="1116b-137">Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="1116b-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1116b-138">Sélectionnez **activité** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="1116b-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="1116b-139">Type `Prompt` dans les **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1116b-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="1116b-140">Double-cliquez sur **Prompt.xaml** dans **l’Explorateur de solutions** à afficher dans le concepteur si elle n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="1116b-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="1116b-141">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour afficher le **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="1116b-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="1116b-142">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="1116b-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="1116b-143">Type `BookmarkName` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="1116b-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="1116b-144">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="1116b-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="1116b-145">Type `Result` dans les **nom** zone située sous récemment ajouté `BookmarkName` argument, sélectionnez **hors** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="1116b-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="1116b-146">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="1116b-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="1116b-147">Type `Text` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="1116b-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="1116b-148">Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1116b-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="1116b-149">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="1116b-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="1116b-150">Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette de la **Invite** Concepteur d’activités.</span><span class="sxs-lookup"><span data-stu-id="1116b-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1116b-151">Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="1116b-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="1116b-152">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette de la **Séquence** activité.</span><span class="sxs-lookup"><span data-stu-id="1116b-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="1116b-153">Lier le **texte** argument de la **WriteLine** activité à la **texte** argument de la **invite** activité en tapant `Text` dans le **entrer une expression c#** ou **entrer une expression VB** zone le **propriétés** fenêtre et appuyez sur l’onglet clé deux fois.</span><span class="sxs-lookup"><span data-stu-id="1116b-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="1116b-154">Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété.</span><span class="sxs-lookup"><span data-stu-id="1116b-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="1116b-155">Cette propriété peut également être définie en tapant `Text` dans les **entrer une expression c#** ou **entrer une expression VB** zone sur l’activité elle-même.</span><span class="sxs-lookup"><span data-stu-id="1116b-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1116b-156">Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="1116b-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="1116b-157">Faites glisser un **ReadInt** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-la dans le **séquence** activité afin qu’elle suive le **WriteLine** activité.</span><span class="sxs-lookup"><span data-stu-id="1116b-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="1116b-158">Lier le **BookmarkName** argument de la **ReadInt** activité à la **BookmarkName** argument de la **invite** activité en tapant `BookmarkName` dans les **entrer une expression VB** zone située à droite de la **BookmarkName** argument dans le **fenêtre Propriétés**, puis appuyez sur la touche TAB deux reprises pour fermer la fenêtre de membres de liste IntelliSense et d’enregistrer la propriété.</span><span class="sxs-lookup"><span data-stu-id="1116b-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="1116b-159">Lier le **résultat** argument de la **ReadInt** activité à la **résultat** argument de la **invite** activité en tapant `Result` dans le **entrer une expression VB** zone située à droite de la **résultat** argument dans le **fenêtre Propriétés**, puis appuyez sur la touche TAB.</span><span class="sxs-lookup"><span data-stu-id="1116b-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="1116b-160">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="1116b-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="1116b-161">Pour obtenir des instructions sur la création d’un flux de travail à l’aide de ces activités, consultez l’étape suivante du didacticiel, [Comment : créer un flux de travail](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1116b-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1116b-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1116b-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="1116b-163">Conception et implémentation d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="1116b-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="1116b-164">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="1116b-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="1116b-165">Guide pratique pour créer un workflow</span><span class="sxs-lookup"><span data-stu-id="1116b-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="1116b-166">Utilisation d’ExpressionTextBox dans un concepteur d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="1116b-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
