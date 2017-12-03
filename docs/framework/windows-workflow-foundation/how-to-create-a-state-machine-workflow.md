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
ms.openlocfilehash: 5b094fd88321ffcf8d3bb5cdefe870bd12524b4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a>Procédure : créer un workflow d'ordinateur d'état
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique Guide de création d’un workflow qui utilise les deux activités intégrées, telles que la <xref:System.Activities.Statements.StateMachine> activité et les activités personnalisées à partir de la précédente [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) rubrique. Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour terminer cette rubrique, vous devez d’abord terminer [Comment : créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-workflow"></a>Pour créer le flux de travail  
  
1.  Avec le bouton droit **NumberGuessWorkflowActivities** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément**.  
  
2.  Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **Workflow** liste.  
  
3.  Type `StateMachineNumberGuessWorkflow` dans les **nom** , puis cliquez sur **ajouter**.  
  
4.  Faites glisser un **StateMachine** activité à partir de la **Machine à états** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette sur l’aire de conception de flux de travail.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail  
  
1.  Double-cliquez sur **StateMachineNumberGuessWorkflow.xaml** dans **l’Explorateur de solutions** pour afficher le flux de travail dans le concepteur, si elle n’est pas affichée.  
  
2.  Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.  
  
3.  Cliquez sur **créer un Argument**.  
  
4.  Type `MaxNumber` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.  
  
5.  Cliquez sur **créer un Argument**.  
  
6.  Type `Turns` dans le **nom** zone ci-dessous récemment ajouté `MaxNumber` argument, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez  **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.  
  
7.  Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.  
  
8.  Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Variables** volet.  
  
9. Cliquez sur **créer la Variable**.  
  
    > [!TIP]
    >  Si aucun **créer une Variable** s’affiche, cliquez sur le <xref:System.Activities.Statements.StateMachine> activité sur l’aire de Concepteur de flux de travail pour le sélectionner.  
  
10. Type `Guess` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **créer la Variable**.  
  
12. Type `Target` dans les **nom** boîte, sélectionnez **Int32** à partir de la **le type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Variables** volet.  
  
### <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail  
  
1.  Cliquez sur **State1** pour le sélectionner. Dans le **fenêtre Propriétés**, modifiez le **DisplayName** à `Initialize Target`.  
  
    > [!TIP]
    >  Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.  
  
2.  Double-cliquez sur récemment renommé **Initialize Target** état dans le Concepteur de flux de travail pour le développer.  
  
3.  Faites glisser une **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **entrée** section de l’état. Type `Target` dans les **à** boîte et l’expression suivante dans le **entrer une expression c#** ou **entrer une expression VB** boîte.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
4.  Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.  
  
5.  Faites glisser un **état** activité à partir de la **Machine à états** section de la **boîte à outils** sur le Concepteur de flux de travail et placez-la sur le **Initialize Target** état. Notez que quatre triangles apparaissent autour de le **Initialize Target** état lorsque le nouvel état est dessus. Déposez le nouvel état sur le triangle qui est immédiatement au-dessous du **Initialize Target** état. Cela place le nouvel état sur le flux de travail et crée une transition à partir de la **Initialize Target** le nouvel état de l’état.  
  
6.  Cliquez sur **State1** pour le sélectionner, remplacez le **DisplayName** à `Enter Guess`, puis double-cliquez sur l’état dans le Concepteur de flux de travail pour le développer.  
  
7.  Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **entrée** section de l’état.  
  
8.  Tapez l’expression suivante dans le **texte** zone de la propriété de la **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la dans le **quitter** section de l’état.  
  
10. Type `Turns` dans le **à** boîte et `Turns + 1` dans le **entrer une expression c#** ou **entrer une expression VB** boîte.  
  
11. Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.  
  
12. Faites glisser un **FinalState** activité à partir de la **Machine à états** section de la **boîte à outils**, placez-la sur le **entrer l’estimation** d’état, puis déposez-la sur le triangle qui apparaît à droite de la **Enter Guess** afin que la création d’une transition entre l’état **Enter Guess** et **FinalState**.  
  
13. Le nom par défaut de la transition est **T2**. Cliquez sur la transition dans le Concepteur de flux de travail pour la sélectionner, puis définir ses **DisplayName** à **Guess Correct**. Puis cliquez sur le **FinalState**et faites-le glisser vers la droite afin qu’il y pour le nom complet de transition sans recouvrir un des deux États. Cela facilitera l'exécution des autres étapes du didacticiel.  
  
14. Double-cliquez sur récemment renommé **Guess Correct** transition dans le Concepteur de flux de travail pour le développer.  
  
15. Faites glisser un **ReadInt** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-la dans le **déclencheur** section de la transition.  
  
16. Dans le **fenêtre Propriétés** pour le **ReadInt** activité, type `"EnterGuess"` les guillemets le **BookmarkName** zone de valeur de propriété et `Guess`dans les **résultat** zone de valeur de propriété  
  
17. Tapez l’expression suivante dans le **Guess Correct** de transition **Condition** zone de valeur de propriété.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.  
  
    > [!NOTE]
    >  Une transition se produit lorsque l'événement déclencheur est reçu et <xref:System.Activities.Statements.Transition.Condition%2A>, s'il est présent, prend la valeur `True`. Pour cette transition, si l’utilisateur `Guess` correspond à généré de manière aléatoire `Target`, puis le contrôle passe à la **FinalState** et le workflow se termine.  
  
19. Selon que l’estimation est correcte, le flux de travail doit passer à la **FinalState** ou revenir à la **entrer une estimation** l’état d’un autre bloc try. Les deux transitions partagent le même déclencheur d’attente d’estimation de l’utilisateur doit être reçu via le **ReadInt** activité. Il s'agit d'une transition partagée. Pour créer une transition partagée, cliquez sur le cercle qui indique le début de la **Guess Correct** de transition et faites-le glisser vers l’état souhaité. Dans ce cas la transition est une transition automatique, par conséquent, faites glisser le point de départ de la **Guess Correct** de transition et déposez-le vers le bas de la **Enter Guess** état. Après avoir créé la transition, sélectionnez-la dans le Concepteur de flux de travail et définissez son **DisplayName** propriété **Guess Incorrect**.  
  
    > [!NOTE]
    >  Des transitions partagées peuvent également être créées à partir du Concepteur de transition en cliquant sur **ajouter une transition de déclencheur partagée** au bas du Concepteur de transition, puis en sélectionnant l’état cible souhaité dans le  **Les états disponibles pour la connexion** liste déroulante.  
  
    > [!NOTE]
    >  Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `false` (ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `false`), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés. Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées (il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte).  
  
20. Double-cliquez sur le **Guess Incorrect** transition dans le Concepteur de flux de travail pour le développer. Notez que la **déclencheur** est déjà défini sur le même **ReadInt** activité qui a été utilisé par le **Guess Correct** transition.  
  
21. Tapez l’expression suivante dans le **Condition** zone de valeur de propriété.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Faites glisser un **si** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la dans le **Action** section de la transition.  
  
23. Tapez l’expression suivante dans le **si** l’activité **Condition** zone de valeur de propriété.  
  
    ```
    Guess < Target  
    ```  
  
24. Faites glisser deux **WriteLine** activités à partir de la **Primitives** section de la **boîte à outils** et déposez-les de sorte qu’un est dans le **puis** section de le **si** activité et l’autre est dans le **Else** section.  
  
25. Cliquez sur le **WriteLine** activité dans le **puis** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Cliquez sur le **WriteLine** activité dans le **Else** pour le sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Revenir à la globale vue dans le Concepteur de flux de travail de machine d’état en cliquant sur **StateMachine** dans la barre de navigation s’affichent en haut du Concepteur de workflow.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Flux de travail de Machine d’état terminé](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Pour générer le flux de travail  
  
1.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur la façon d’exécuter le flux de travail, consultez la rubrique suivante, [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Si vous avez déjà effectué le [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) étape avec un style différent de flux de travail et à exécuter en utilisant le workflow de machine d’état à partir de cette étape, passez directement à la [pour générer et exécuter l’application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section de [Comment : exécuter un Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programmation Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Conception des workflows](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Didacticiel Bien démarrer](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Guide pratique pour créer une activité](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Guide pratique pour exécuter un workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
