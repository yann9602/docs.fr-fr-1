---
title: "Procédure : créer un workflow séquentiel"
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
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bf6d8b499903522ee09021bb9339ece6a5894eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-sequential-workflow"></a>Procédure : créer un workflow séquentiel
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique Guide de création d’un workflow qui utilise les deux activités intégrées, telles que la <xref:System.Activities.Statements.Sequence> activité et les activités personnalisées à partir de la précédente [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) rubrique. Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour terminer cette rubrique, vous devez d’abord terminer [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-workflow"></a>Pour créer le flux de travail  
  
1.  Avec le bouton droit **NumberGuessWorkflowActivities** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément**.  
  
2.  Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **Workflow** liste.  
  
3.  Type `SequentialNumberGuessWorkflow` dans les **nom** , puis cliquez sur **ajouter**.  
  
4.  Faites glisser un **séquence** activité à partir de la **flux de contrôle** section du **boîte à outils** et déposez-la sur le **déposer l’activité ici** étiquette sur le aire de conception de workflow.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail  
  
1.  Double-cliquez sur **SequentialNumberGuessWorkflow.xaml** dans **l’Explorateur de solutions** pour afficher le flux de travail dans le concepteur, si elle n’est pas affichée.  
  
2.  Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.  
  
3.  Cliquez sur **créer un Argument**.  
  
4.  Type `MaxNumber` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.  
  
5.  Cliquez sur **créer un Argument**.  
  
6.  Type `Turns` dans le **nom** zone ci-dessous récemment ajouté `MaxNumber` argument, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez  **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.  
  
7.  Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.  
  
8.  Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Variables** volet.  
  
9. Cliquez sur **créer la Variable**.  
  
    > [!TIP]
    >  Si aucun **créer une Variable** s’affiche, cliquez sur le **séquence** activité sur l’aire de Concepteur de flux de travail pour le sélectionner.  
  
10. Type `Guess` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **créer la Variable**.  
  
12. Type `Target` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Variables** volet.  
  
### <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail  
  
1.  Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **séquence** activité. Type `Target` dans les **à** boîte et l’expression suivante dans le **entrer une expression c#** ou **entrer une expression VB** boîte.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
2.  Faites glisser un **DoWhile** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-le sur le flux de travail afin qu’il soit sous la **affecter** activité.  
  
3.  Tapez l’expression suivante dans le **DoWhile** l’activité **Condition** zone de valeur de propriété.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     Une activité <xref:System.Activities.Statements.DoWhile> exécute ses activités enfants puis évalue son <xref:System.Activities.Statements.DoWhile.Condition%2A>. Si <xref:System.Activities.Statements.DoWhile.Condition%2A> a la valeur `True`, les activités dans <xref:System.Activities.Statements.DoWhile> s'exécutent encore. Dans cet exemple, l'estimation de l'utilisateur est évaluée et <xref:System.Activities.Statements.DoWhile> continue jusqu'à ce que l'estimation soit correcte.  
  
4.  Faites glisser un **invite** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-la dans le **DoWhile** activité à partir de l’étape précédente.  
  
5.  Dans le **fenêtre Propriétés**, type `"EnterGuess"` les guillemets le **BookmarkName** zone de valeur de propriété pour le **invite** activité. Type `Guess` dans les **résultat** zone de valeur de propriété et tapez l’expression suivante dans le **texte** zone de propriété.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.  
  
6.  Faites glisser une **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le dans le **DoWhile** activité afin qu’elle suive le **Invite** activité.  
  
    > [!NOTE]
    >  Lorsque vous déposez le **affecter** activité, notez comment le Concepteur de workflow ajoute automatiquement un **séquence** activité pour contenir le **invite** activité et récemment ajouté **Affecter** activité.  
  
7.  Type `Turns` dans le **à** boîte et `Turns + 1` dans le **entrer une expression c#** ou **entrer une expression VB** boîte.  
  
8.  Faites glisser une **si** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la dans le **séquence** activité afin qu’elle suive le qui vient d’être ajouté **affecter** activité.  
  
9. Tapez l’expression suivante dans le **si** l’activité **Condition** zone de valeur de propriété.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Faites glisser une autre **si** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la dans le **puis** section de la première **Si** activité.  
  
11. Tapez l’expression suivante dans récemment ajouté **si** l’activité **Condition** zone de valeur de propriété.  
  
    ```
    Guess < Target  
    ```  
  
12. Faites glisser deux **WriteLine** activités à partir de la **Primitives** section de la **boîte à outils** et déposez-les de sorte qu’un est dans le **puis** section de récemment ajouté **si** activité et l’autre est dans le **Else** section.  
  
13. Cliquez sur le **WriteLine** activité dans le **puis** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Cliquez sur le **WriteLine** activité dans le **Else** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Flux de travail séquentiel terminé](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Pour générer le flux de travail  
  
1.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur la façon d’exécuter le flux de travail, consultez la rubrique suivante, [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Si vous avez déjà effectué le [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) étape avec un style différent de flux de travail et à exécuter à l’aide du flux de travail séquentiel à partir de cette étape, passez directement à la [pour générer et exécuter l’application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)section de [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programmation Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Conception des workflows](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Didacticiel Bien démarrer](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Guide pratique pour créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Guide pratique pour exécuter un workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
