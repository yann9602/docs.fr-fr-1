---
title: "Proc&#233;dure&#160;: cr&#233;er un workflow s&#233;quentiel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Proc&#233;dure&#160;: cr&#233;er un workflow s&#233;quentiel
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.Cette rubrique vous guide dans la création d'un workflow qui utilise à la fois des activités intégrées, telles que l'activité <xref:System.Activities.Statements.Sequence>, et les activités personnalisées de la rubrique [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md) précédente.Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.Pour effectuer cette rubrique, vous devez d'abord effectuer [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation \(WF45\) \- Didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### Pour créer le workflow  
  
1.  Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, **Nouvel élément**.  
  
2.  Dans la liste **Installé**, dans le nœud **Éléments communs**, sélectionnez **Workflow**.Sélectionnez **Activité** dans la liste **Workflow**.  
  
3.  Dans la zone **Nom**, tapez `SequentialNumberGuessWorkflow` et cliquez sur **Ajouter**.  
  
4.  Faites glisser une activité **Sequence** de la section **Organigramme** de la **Boîte à outils** et déposez\-la sur l'étiquette **Déposer l'activité ici** sur l'aire de conception de workflow.  
  
### Pour créer les variables et arguments du flux de travail  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur **SequentialNumberGuessWorkflow.xaml** pour afficher le workflow dans le concepteur, si ce n'est pas déjà fait.  
  
2.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Arguments**.  
  
3.  Cliquez sur **Créer un argument**.  
  
4.  Tapez `MaxNumber` dans la zone **Nom**, sélectionnez **In** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE pour enregistrer l'argument.  
  
5.  Cliquez sur **Créer un argument**.  
  
6.  Tapez `Turns` dans la zone **Nom** située en dessous de l'argument `MaxNumber` récemment ajouté, sélectionnez **Out** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE.  
  
7.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.  
  
8.  Cliquez sur **Variables** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Variables**.  
  
9. Cliquez sur **Créer une variable**.  
  
    > [!TIP]
    >  Si aucune zone **Créer une variable** n'est affichée, cliquez sur l'activité **Sequence** sur l'aire du concepteur de workflow pour sélectionner le workflow.  
  
10. Tapez `Guess` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **Créer une variable**.  
  
12. Tapez `Target` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Variables**.  
  
### Pour ajouter les activités de flux de travail  
  
1.  Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et déposez\-la dans l'activité **Sequence**.Tapez `Target` dans la zone **À** et l'expression suivante dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si la fenêtre **Boîte à outils** n'est pas affichée, sélectionnez **Boîte à outils** dans le menu **Affichage**.  
  
2.  Faites glisser une activité **DoWhile** de la section **Flux de contrôle** de la **Boîte à outils** et déposez\-la dans le workflow afin qu'elle se trouve au\-dessous de l'activité **Assign**.  
  
3.  Tapez l'expression suivante dans la zone de valeur de propriété **Condition** de l'activité **DoWhile**.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     Une activité <xref:System.Activities.Statements.DoWhile> exécute ses activités enfants puis évalue son <xref:System.Activities.Statements.DoWhile.Condition%2A>.Si <xref:System.Activities.Statements.DoWhile.Condition%2A> a la valeur `True`, les activités dans <xref:System.Activities.Statements.DoWhile> s'exécutent encore.Dans cet exemple, l'estimation de l'utilisateur est évaluée et <xref:System.Activities.Statements.DoWhile> continue jusqu'à ce que l'estimation soit correcte.  
  
4.  Faites glisser une activité **Prompt** de la section **NumberGuessWorkflowActivities** de la **Boîte à outils** et déposez\-la dans l'activité **DoWhile** de l'étape précédente.  
  
5.  Dans la zone de valeur de propriété **BookmarkName** de la **Fenêtre Propriétés** pour l'activité **Prompt**, tapez `"EnterGuess"` sans oublier les guillemets.Dans la zone de valeur de propriété **Résultat**, tapez `Guess`, et dans la zone de propriété **Texte**, tapez l'expression suivante :  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Si la **Fenêtre Propriétés** n'est pas affichée, sélectionnez **Fenêtre Propriétés** dans le menu **Affichage**.  
  
6.  Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et déposez\-la dans l'activité **DoWhile** de sorte qu'elle suive l'activité **Prompt**.  
  
    > [!NOTE]
    >  Lorsque vous déposez l'activité **Assign**, notez comment le concepteur de workflow ajoute automatiquement une activité **Sequence** pour contenir l'activité **Prompt** et l'activité **Assign** récemment ajoutée.  
  
7.  Tapez `Turns` dans la zone **À** et `Turns + 1` dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
8.  Faites glisser une activité **If** de la section **Control Flow** de la **Boîte à outils** et déposez\-la dans l'activité **Sequence** afin qu'elle suive l'activité **Assign** récemment ajoutée.  
  
9. Tapez l'expression suivante dans la zone de valeur de propriété **Condition** de l'activité **If**.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Faites glisser une autre activité **If** de la section **Control Flow** de la **Boîte à outils** et déposez \-la dans la section **Then** de la première activité **If**.  
  
11. Tapez l'expression suivante dans la zone de valeur de propriété **Condition** de l'activité **If** récemment ajoutée.  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
12. Faites glisser deux activités **WriteLine** de la section **Primitives** de la **Boîte à outils** et déposez\-les de façon à ce qu'une d'entre elles soit dans la section **Then** de l'activité **If** récemment ajoutée, et l'autre dans la section **Else**.  
  
13. Cliquez sur l'activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l'expression suivante dans la zone de valeur de propriété **Texte**.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Cliquez sur l'activité **WriteLine** dans la section **Else** pour la sélectionner, puis tapez l'expression suivante dans la zone de valeur de propriété **Texte**.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Flux de travail séquentiel terminé](../../../docs/framework/windows-workflow-foundation//media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### Pour générer le flux de travail  
  
1.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
     Pour obtenir des instructions sur la procédure d'exécution du workflow, consultez la rubrique suivante, [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).Si vous avez déjà terminé l'étape [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) avec un style différent de workflow et souhaitez l'exécuter en utilisant le workflow séquentiel de cette étape, passez à la section [Pour générer et exécuter l'application](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).  
  
## Voir aussi  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Programmation Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [Conception des flux de travaux](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)