---
title: "Proc&#233;dure&#160;: cr&#233;er un workflow d&#39;organigramme | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Proc&#233;dure&#160;: cr&#233;er un workflow d&#39;organigramme
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.Cette rubrique vous guide dans la création d'un workflow qui utilise à la fois des activités intégrées, telles que l'activité <xref:System.Activities.Statements.Flowchart>, et les activités personnalisées de la rubrique [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md) précédente.Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.Pour effectuer cette rubrique, vous devez d'abord effectuer [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation \(WF45\) \- Didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### Pour créer le workflow  
  
1.  Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, **Nouvel élément**.  
  
2.  Dans la liste **Installé**, dans le nœud **Éléments communs**, sélectionnez **Workflow**.Sélectionnez **Activité** dans la liste **Workflow**.  
  
3.  Dans la zone **Nom**, tapez `FlowchartNumberGuessWorkflow` et cliquez sur **Ajouter**.  
  
4.  Faites glisser une activité **Flowchart** de la section **Organigramme** de la **Boîte à outils** et déposez\-la sur l'étiquette **Déposer l'activité ici** sur l'aire de conception de workflow.  
  
### Pour créer les variables et arguments du flux de travail  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur **FlowchartNumberGuessWorkflow.xaml** pour afficher le workflow dans le concepteur, si ce n'est pas déjà fait.  
  
2.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Arguments**.  
  
3.  Cliquez sur **Créer un argument**.  
  
4.  Tapez `MaxNumber` dans la zone **Nom**, sélectionnez **In** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE pour enregistrer l'argument.  
  
5.  Cliquez sur **Créer un argument**.  
  
6.  Tapez `Turns` dans la zone **Nom** située en dessous de l'argument `MaxNumber` récemment ajouté, sélectionnez **Out** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE.  
  
7.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.  
  
8.  Cliquez sur **Variables** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Variables**.  
  
9. Cliquez sur **Créer une variable**.  
  
    > [!TIP]
    >  Si aucune zone **Créer une variable** n'est affichée, cliquez sur l'activité <xref:System.Activities.Statements.Flowchart> sur l'aire du concepteur de workflow pour sélectionner le workflow.  
  
10. Tapez `Guess` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **Créer une variable**.  
  
12. Tapez `Target` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Variables**.  
  
### Pour ajouter les activités de flux de travail  
  
1.  Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et placez\-la sur le nœud **Début**, qui se trouve en haut de l'organigramme.Lorsque l'activité **Assign** se trouve sur le nœud **Début**, trois triangles apparaissent autour du nœud **Début**.Déposez l'activité **Assign** sur le triangle qui est directement sous le nœud **Début**.Cela crée les deux éléments ensemble et indique l'activité **Assign** comme première activité dans l'organigramme.  
  
    > [!NOTE]
    >  Les activités peuvent également être définies comme activité de départ dans le workflow en les liant manuellement au nœud de démarrage.Pour ce faire, placez le pointeur de la souris sur le nœud **Début**, cliquez sur l'un des rectangles qui s'affichent lorsque la souris se trouve sur le nœud **Début**, et faites glisser la ligne de connexion vers le bas jusqu'à l'activité souhaitée, puis déposez\-la sur l'un des rectangles qui s'affichent.Vous pouvez également désigner l'activité en tant qu'activité initiale en cliquant avec le bouton droit sur l'activité et en choisissant **Définir en tant que StartNode**.  
  
2.  Tapez `Target` dans la zone **À** et l'expression suivante dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si la fenêtre **Boîte à outils** n'est pas affichée, sélectionnez **Boîte à outils** dans le menu **Affichage**.  
  
3.  Faites glisser une activité **Prompt** de la section **NumberGuessWorkflowActivities** de la **Boîte à outils**, déposez\-la au\-dessous de l'activité **Assign** de l'étape précédente, puis connectez l'activité **Prompt** à l'activité **Assign**.Il existe trois façons de connecter les deux activités.La première consiste à les connecter lorsque vous déposez l'activité **Prompt** sur le workflow.Lorsque vous faites glisser l'activité **Prompt** vers le workflow, placez\-la sur l'activité **Assign** et déposez\-la sur l'un des quatre triangles qui apparaît lorsque l'activité **Prompt** est positionnée sur l'activité **Assign**.La seconde consiste à déposer l'activité **Prompt** sur le workflow à l'emplacement souhaité.Ensuite, placez le pointeur de la souris sur l'activité **Assign** et faites glisser l'un des rectangles qui apparaît sous l'activité **Prompt**.Faites glisser la souris de sorte que la ligne de connexion de l'activité **Assign** se connecte à un des rectangles de l'activité **Prompt** et relâchez le bouton de la souris.La troisième méthode est très similaire à la première, mais au lieu de faire glisser l'activité **Prompt** depuis la **Boîte à outils**, vous la faites glisser de son emplacement sur l'aire de conception de workflow, vous la positionnez sur l'activité **Assign** et vous la déposez sur l'un des triangles qui apparaît.  
  
4.  Dans la zone de valeur de propriété **BookmarkName** de la **Fenêtre Propriétés** pour l'activité **Prompt**, tapez `"EnterGuess"` sans oublier les guillemets.Dans la zone de valeur de propriété **Résultat**, tapez `Guess`, et dans la zone de propriété **Texte**, tapez l'expression suivante :  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Si la **Fenêtre Propriétés** n'est pas affichée, sélectionnez **Fenêtre Propriétés** dans le menu **Affichage**.  
  
5.  Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et connectez\-la à l'aide d'une des méthodes décrites à l'étape précédente de façon à ce qu'elle se trouve en dessous de l'activité **Prompt**.  
  
6.  Tapez `Turns` dans la zone **À** et `Turns + 1` dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
7.  Faites glisser une activité **FlowDecision** de la section **Organigramme** de la **Boîte à outils** et connectez\-la en dessous de l'activité **Assign**.Dans la zone de valeur de propriété **Condition** de la **Fenêtre Propriétés**, tapez l'expression suivante :  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Faites glisser une autre activité **FlowDecision** de la **Boîte à outils** et déposez\-la en dessous de la première.Connectez les deux activités en effectuant un glisser du rectangle étiqueté **False** en haut de l'activité **FlowDecision**, au rectangle en haut de la deuxième activité **FlowDecision**.  
  
    > [!TIP]
    >  Si les étiquettes **True** et **False** n'apparaissent pas dans l'activité **FlowDecision**, pointez avec la souris sur **FlowDecision**.  
  
9. Cliquez sur la deuxième activité **FlowDecision** pour la sélectionner.Dans la zone de valeur de propriété **Condition** de la **Fenêtre Propriétés**, tapez l'expression suivante :  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
10. Faites glisser deux activités **WriteLine** de la section **Primitives** de la **Boîte à outils** et déposez\-les de sorte qu'elles soient côte à côte en dessous des deux activités **FlowDecision**.Connectez l'action **True** de l'activité **FlowDecision** inférieure à l'activité **WriteLine** la plus à gauche, et l'action **False** à l'activité **WriteLine** la plus à droite.  
  
11. Cliquez sur l'activité **WriteLine** la plus à gauche pour la sélectionner et dans la zone de valeur de propriété **Texte** de la **Fenêtre Propriétés**, tapez l'expression suivante :  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
12. Connectez l'activité **WriteLine** au côté gauche de l'activité **Prompt** située au\-dessus.  
  
13. Cliquez sur l'activité **WriteLine** la plus à droite pour la sélectionner et dans la zone de valeur de propriété **Texte** de la **Fenêtre Propriétés**, tapez l'expression suivante :  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
14. Connectez l'activité **WriteLine** au côté droit de l'activité **Prompt** située au\-dessus.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Windows Workflow Foundation terminée](../../../docs/framework/windows-workflow-foundation//media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### Pour générer le flux de travail  
  
1.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
     Pour obtenir des instructions sur la procédure d'exécution du workflow, consultez la rubrique suivante, [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).Si vous avez déjà terminé l'étape [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) avec un style différent de workflow et souhaitez l'exécuter en utilisant le workflow d'organigramme de cette étape, passez à la section [Pour générer et exécuter l'application](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).  
  
## Voir aussi  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Programmation Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [Conception des flux de travaux](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)