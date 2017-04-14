---
title: "Proc&#233;dure&#160;: cr&#233;er un workflow d&#39;ordinateur d&#39;&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Proc&#233;dure&#160;: cr&#233;er un workflow d&#39;ordinateur d&#39;&#233;tat
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.Cette rubrique vous guide dans la création d'un workflow qui utilise à la fois des activités intégrées, telles que l'activité <xref:System.Activities.Statements.StateMachine>, et les activités personnalisées de la rubrique [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md) précédente.Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.Pour effectuer cette rubrique, vous devez d'abord effectuer [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation \(WF45\) \- Didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### Pour créer le workflow  
  
1.  Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, **Nouvel élément**.  
  
2.  Dans la liste **Installé**, dans le nœud **Éléments communs**, sélectionnez **Workflow**.Sélectionnez **Activité** dans la liste **Workflow**.  
  
3.  Dans la zone **Nom**, tapez `StateMachineNumberGuessWorkflow` et cliquez sur **Ajouter**.  
  
4.  Faites glisser une activité **StateMachine** de la section **State Machine** de la **Boîte à outils** et déposez\-la sur l'étiquette **Déposer l'activité ici** sur l'aire de conception de workflow.  
  
### Pour créer les variables et arguments du flux de travail  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur **StateMachineNumberGuessWorkflow.xaml** pour afficher le workflow dans le concepteur, si ce n'est pas déjà fait.  
  
2.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Arguments**.  
  
3.  Cliquez sur **Créer un argument**.  
  
4.  Tapez `MaxNumber` dans la zone **Nom**, sélectionnez **In** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE pour enregistrer l'argument.  
  
5.  Cliquez sur **Créer un argument**.  
  
6.  Tapez `Turns` dans la zone **Nom** située en dessous de l'argument `MaxNumber` récemment ajouté, sélectionnez **Out** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE.  
  
7.  Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.  
  
8.  Cliquez sur **Variables** dans la partie inférieure gauche du concepteur de workflow pour afficher le volet **Variables**.  
  
9. Cliquez sur **Créer une variable**.  
  
    > [!TIP]
    >  Si aucune zone **Créer une variable** n'est affichée, cliquez sur l'activité <xref:System.Activities.Statements.StateMachine> sur l'aire du concepteur de workflow pour sélectionner le workflow.  
  
10. Tapez `Guess` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **Créer une variable**.  
  
12. Tapez `Target` dans la zone **Nom**, sélectionnez **Int32** dans la liste déroulante **Type de variable**, puis appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Variables**.  
  
### Pour ajouter les activités de flux de travail  
  
1.  Cliquez sur **State1** pour le sélectionner.Dans **Fenêtre Propriétés**, remplacez **DisplayName** par `Initialize Target`.  
  
    > [!TIP]
    >  Si la **Fenêtre Propriétés** n'est pas affichée, sélectionnez **Fenêtre Propriétés** dans le menu **Affichage**.  
  
2.  Double\-cliquez sur l'état récemment renommé **Initialize Target** dans le concepteur de workflow pour le développer.  
  
3.  Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et déposez\-la dans la section **Entry** de l'état.Tapez `Target` dans la zone **À** et l'expression suivante dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si la fenêtre **Boîte à outils** n'est pas affichée, sélectionnez **Boîte à outils** dans le menu **Affichage**.  
  
4.  Revenez à la vue globale de machine à états dans le concepteur de workflow en cliquant sur **StateMachine** dans l'affichage de fil d'Ariane en haut du concepteur de workflow.  
  
5.  Faites glisser une activité **State** de la section **State Machine** de la **Boîte à outils** sur le concepteur de workflow et placez\-la sur l'état **Initialize Target**.Notez que quatre triangles apparaîtront autour de l'état **Initialize Target** lorsque le nouvel état est sur lui.Déposez le nouvel état sur le triangle qui est immédiatement au\-dessous de l'état **Initialize Target**.Cela place le nouvel état sous le workflow et crée une transition de l'état **Initialize Target** vers le nouvel état.  
  
6.  Cliquez sur **State1** pour le sélectionner, remplacez **DisplayName** par `Entrer l'estimation`, puis double\-cliquez sur l'état dans le concepteur de workflow pour le développer.  
  
7.  Faites glisser une activité **WriteLine** de la section **Primitives** de la **Boîte à outils** et déposez\-la dans la section **Entry** de l'état.  
  
8.  Tapez l'expression suivante dans la zone de propriété **Text** de **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Faites glisser une activité **Assign** de la section **Primitives** de la **Boîte à outils** et déposez\-la dans la section **Exit** de l'état.  
  
10. Tapez `Turns` dans la zone **À** et `Turns + 1` dans la zone **Entrer une expression C\#** ou **Entrer une expression VB**.  
  
11. Revenez à la vue globale de machine à états dans le concepteur de workflow en cliquant sur **StateMachine** dans l'affichage de fil d'Ariane en haut du concepteur de workflow.  
  
12. Faites glisser une activité **FinalState** de la section **State Machine** de la **Boîte à outils**, placez\-la sur l'état **Enter Guess**, puis déposez\-la sur le triangle qui apparaît à droite de l'état **Enter Guess** afin qu'une transition soit créée entre **Enter Guess** et **FinalState**.  
  
13. Le nom par défaut de la transition est **T2**.Cliquez sur la transition dans le concepteur de workflow pour la sélectionner, et affectez à **DisplayName** la valeur **Correct Guess**.Sélectionnez **FinalState**, et faites\-le glisser vers la droite pour qu'il y ait de la place pour afficher le nom complet de la transition sans recouvrir l'un ou l'autre des deux états.Cela facilitera l'exécution des autres étapes du didacticiel.  
  
14. Double\-cliquez sur la transition récemment renommée **Estimation correcte** dans le concepteur de workflow pour la développer.  
  
15. Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **Boîte à outils** et déposez \-la dans la section **Trigger** de la transition.  
  
16. Dans **Fenêtre Propriétés** pour l'activité **ReadInt**, tapez `"EnterGuess"` sans oublier les guillemets dans la zone de valeur de propriété **BookmarkName**, et tapez `Guess` dans la zone de valeur de propriété **Result**  
  
17. Tapez l'expression suivante dans la zone de valeur de propriété **Condition** de la transition **Guess Correct**.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Revenez à la vue globale de machine à états dans le concepteur de workflow en cliquant sur **StateMachine** dans l'affichage de fil d'Ariane en haut du concepteur de workflow.  
  
    > [!NOTE]
    >  Une transition se produit lorsque l'événement déclencheur est reçu et <xref:System.Activities.Statements.Transition.Condition%2A>, s'il est présent, prend la valeur `True`.Pour cette transition, si le `Guess` de l'utilisateur correspond au `Target` généré de manière aléatoire, le contrôle passe à **FinalState** et le workflow se termine.  
  
19. Selon que cette estimation est correcte ou non, le workflow doit passer à l'état **FinalState** ou à l'état **Enter Guess** pour une autre tentative.Les deux transitions partagent le même déclencheur d'attente de l'estimation de l'utilisateur qui doit être reçu via l'activité **ReadInt**.Il s'agit d'une transition partagée.Pour créer une transition partagées, cliquez sur le cercle qui indique le début de la transition **Guess Correct** et faites\-le glisser vers l'état souhaité.Dans ce cas la transition est une transition automatique, par conséquent, faites glisser le point de départ de la transition **Guess Correct** et déposez\-le vers le bas de l'état **Enter Guess**.Après avoir créé la transition, sélectionnez\-la dans le concepteur de workflow et affectez à sa propriété **DisplayName** la valeur **Guess Incorrect**.  
  
    > [!NOTE]
    >  Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l'état cible souhaité dans la liste déroulante **États disponibles pour la connexion**.  
  
    > [!NOTE]
    >  Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `false` \(ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `false`\), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés.Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées \(il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte\).  
  
20. Double\-cliquez sur la transition **Guess Incorrect** dans le concepteur de workflow pour la développer.Notez que **Trigger** est déjà défini à la même activité **ReadInt** que celle utilisée par la transition **Guess Correct**.  
  
21. Dans la zone de valeur de propriété **Condition**, tapez l'expression suivante :  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Faites glisser une activité **If** de la section **Flux de contrôle** de la **Boîte à outils** et déposez\-la dans la section **Action** de la transition.  
  
23. Tapez l'expression suivante dans la zone de valeur de propriété **Condition** de l'activité **If**.  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
24. Faites glisser deux activités **WriteLine** de la section **Primitives** de la **Boîte à outils** et déposez\-les de façon à ce qu'une d'entre elles soit dans la section **Then** de l'activité **If**, et l'autre dans la section **Else**.  
  
25. Cliquez sur l'activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l'expression suivante dans la zone de valeur de propriété **Texte**.  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
26. Cliquez sur l'activité **WriteLine** dans la section **Else** pour la sélectionner, puis tapez l'expression suivante dans la zone de valeur de propriété **Texte**.  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
27. Revenez à la vue globale de machine à états dans le concepteur de workflow en cliquant sur **StateMachine** dans l'affichage de fil d'Ariane en haut du concepteur de workflow.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Flux de travail de l'ordinateur d'état terminé](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### Pour générer le flux de travail  
  
1.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
     Pour obtenir des instructions sur la procédure d'exécution du workflow, consultez la rubrique suivante, [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).Si vous avez déjà terminé l'étape [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) avec un style différent de workflow et souhaitez l'exécuter en utilisant le workflow de machine à états de cette étape, passez à la section [Pour générer et exécuter l'application](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md).  
  
## Voir aussi  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Programmation Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [Conception des flux de travaux](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [Procédure : créer une activité](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [Procédure : exécuter un workflow](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)