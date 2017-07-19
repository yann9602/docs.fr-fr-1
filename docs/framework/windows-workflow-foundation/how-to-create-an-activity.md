---
title: "Proc&#233;dure&#160;: cr&#233;er une activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: 39
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 39
---
# Proc&#233;dure&#160;: cr&#233;er une activit&#233;
Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités.Cette rubrique indique comment créer deux activités.La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution.L'implémentation de la deuxième activité est définie à l'aide d'autres activités.Ces activités sont utilisées dans les procédures du didacticiel.  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation \(WF45\) \- Didacticiel de mise en route](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### Pour créer le projet de bibliothèque d'activités  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et choisissez **Nouveau**, **Projet** dans le menu **Fichier**.  
  
2.  Dans la liste **Modèlesinstallés**, développez le nœud **Autres types de projets** et sélectionnez **Solutions Visual Studio**.  
  
3.  Dans la liste **Solutions Visual Studio**, sélectionnez **Nouvelle solution**.Dans la liste déroulante de la version du .NET Framework, vérifiez que **.NET Framework 4.5** est sélectionné.Dans la zone **Nom**, tapez `WF45GettingStartedTutorial` et cliquez sur **OK**.  
  
4.  Cliquez avec le bouton droit sur **WF45GettingStartedTutorial** dans l'**Explorateur de solutions**, puis choisissez **Ajouter**, **Nouveau projet**.  
  
    > [!TIP]
    >  Si la fenêtre **Explorateur de solutions** n'est pas affichée, sélectionnez **Explorateur de solutions** dans le menu **Affichage**.  
  
5.  Dans le nœud **Installé**, sélectionnez **Visual C\#**, **Workflow** \(ou **Visual Basic**, **Workflow**\).Dans la liste déroulante des versions du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vérifiez que **.NET Framework 4.5** est sélectionné.Sélectionnez **Bibliothèque d'activités** dans la liste **Workflow**.Dans la zone **Nom**, tapez `NumberGuessWorkflowActivities`, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En fonction du langage de programmation qui est configuré comme langage principal dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], le nœud **Visual C\#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.  
  
6.  Cliquez avec le bouton droit sur **Activity1.xaml** dans l'**Explorateur de solutions** et choisissez **Supprimer**.Pour confirmer, cliquez sur **OK**.  
  
### Pour créer l'activité ReadInt  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
2.  Dans la liste **Installé**, dans le nœud **Éléments communs**, sélectionnez **Workflow**.Sélectionnez **Activité de code** dans la liste **Workflow**.  
  
3.  Dans la zone **Nom**, tapez `ReadInt`, puis cliquez sur **Ajouter**.  
  
4.  Remplacez la définition `ReadInt` existante par la définition suivante.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code.<xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.  
  
### Pour créer l'activité Prompt  
  
1.  Appuyez sur CTRL\+MAJ\+B pour générer le projet.La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.  
  
2.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
3.  Dans la liste **Installé**, dans le nœud **Éléments communs**, sélectionnez **Workflow**.Sélectionnez **Activité** dans la liste **Workflow**.  
  
4.  Dans la zone **Nom**, tapez `Prompt`, puis cliquez sur **Ajouter**.  
  
5.  Dans l'**Explorateur de solutions**, double\-cliquez sur **Prompt.xaml** pour l'afficher dans le concepteur, si ce n'est pas déjà fait.  
  
6.  Pour afficher le volet **Arguments**, dans la partie inférieure gauche du concepteur d'activités, cliquez sur **Arguments**.  
  
7.  Cliquez sur **Créer un argument**.  
  
8.  Tapez `BookmarkName` dans la zone **Nom**, sélectionnez **In** dans la liste déroulante **Direction**, choisissez **String** dans la liste déroulante **Type d'argument** et appuyez sur Entrée pour enregistrer l'argument.  
  
9. Cliquez sur **Créer un argument**.  
  
10. Tapez `Result` dans la zone **Nom** située sous l'argument `BookmarkName` récemment ajouté, sélectionnez **Out** dans la liste déroulante **Direction**, sélectionnez **Int32** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE.  
  
11. Cliquez sur **Créer un argument**.  
  
12. Tapez `Text` dans la zone **Nom**, sélectionnez **In** dans la liste déroulante **Direction**, sélectionnez **String** dans la liste déroulante **Type d'argument**, puis appuyez sur ENTRÉE pour enregistrer l'argument.  
  
     Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.  
  
13. Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.  
  
14. Faites glisser une activité **Sequence** de la section **Organigramme** de la **Boîte à outils** et déposez\-la sur l'étiquette **Déposer l'activité ici** du concepteur de workflow **Prompt**.  
  
    > [!TIP]
    >  Si la fenêtre **Boîte à outils** n'est pas affichée, sélectionnez **Boîte à outils** dans le menu **Affichage**.  
  
15. Faites glisser une activité **WriteLine** de la section **Primitives** de la **Boîte à outils** et déposez\-la sur l'étiquette **Déposer l'activité ici** de l'activité **Sequence**.  
  
16. Liez l'argument **Text** de l'activité **WriteLine** à l'argument **Text** de l'activité **Prompt** en tapant `Text` dans la zone **Entrer une expression VB** ou **Entrer une expression C\#** dans la **Fenêtre Propriétés**, et appuyez deux fois sur la touche Tab.Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété.Cette propriété peut également être définie en tapant `Text` dans la zone **Entrer une expression VB** ou **Entrer une expression C\#** sur l'activité elle\-même.  
  
    > [!TIP]
    >  Si la **Fenêtre Propriétés** n'est pas affichée, sélectionnez **Fenêtre Propriétés** dans le menu **Affichage**.  
  
17. Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **Boîte à outils** et déposez\-la dans l'activité **Sequence** afin qu'elle suive l'activité **WriteLine**.  
  
18. Liez l'argument **BookmarkName** de l'activité **ReadInt** à l'argument **BookmarkName** de l'activité **Prompt** en tapant `BookmarkName` dans la zone **Entrer une expression VB** à droite de l'argument **BookmarkName** dans la **Fenêtre Propriétés**, et appuyez deux fois sur la touche TAB pour fermer la fenêtre des membres de la liste IntelliSense et enregistrer la propriété.  
  
19. Liez l'argument **Result** de l'activité **ReadInt** à l'argument **Result** de l'activité **Prompt** en tapant `Result` dans la zone **Entrer une expression VB** à droite de l'argument **Result** dans la **Fenêtre Propriétés**, et appuyez deux fois sur la touche TAB.  
  
20. Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
     Pour obtenir des instructions sur la procédure de création d'un workflow à l'aide de ces activités, consultez l'étape suivante du didacticiel, [Procédure : créer un workflow](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md).  
  
## Voir aussi  
 <xref:System.Activities.CodeActivity>   
 <xref:System.Activities.NativeActivity%601>   
 [Conception et implémentation d'activités personnalisées](../../../docs/framework/windows-workflow-foundation//designing-and-implementing-custom-activities.md)   
 [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [Procédure : créer un workflow](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)   
 [Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)