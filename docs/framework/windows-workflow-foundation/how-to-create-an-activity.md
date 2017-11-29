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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b52daa513bad9d0cb05fcabb27ff5755f8dba2a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-activity"></a>Procédure : créer une activité
Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)]. La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités. Cette rubrique indique comment créer deux activités. La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution. L'implémentation de la deuxième activité est définie à l'aide d'autres activités. Ces activités sont utilisées dans les procédures du didacticiel.  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-activity-library-project"></a>Pour créer le projet de bibliothèque d'activités  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et choisissez **nouveau**, **projet** à partir de la **fichier** menu.  
  
2.  Développez le **autres Types de projets** nœud dans le **installé**, **modèles** et **Solutions Visual Studio**.  
  
3.  Sélectionnez **nouvelle Solution** à partir de la **Solutions Visual Studio** liste. Dans la liste déroulante de la version du .NET Framework, vérifiez que **.NET Framework 4.5** est sélectionné. Type `WF45GettingStartedTutorial` dans les **nom** , puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **WF45GettingStartedTutorial** dans **l’Explorateur de solutions** et choisissez **ajouter**, **nouveau projet**.  
  
    > [!TIP]
    >  Si la fenêtre **Explorateur de solutions** n'est pas affichée, sélectionnez **Explorateur de solutions** dans le menu **Affichage** .  
  
5.  Dans le nœud **Installé** , sélectionnez **Visual C#**, **Workflow** (ou **Visual Basic**, **Workflow**). Vérifiez que **.NET Framework 4.5** est sélectionné dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] liste déroulante de la version. Sélectionnez **bibliothèque d’activités** à partir de la **Workflow** liste. Type `NumberGuessWorkflowActivities` dans les **nom** , puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En fonction du langage de programmation qui est configuré comme langage principal dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], le **Visual C#** ou **Visual Basic** nœud peut se trouver sous le **autres langages**nœud dans le **installé** nœud.  
  
6.  Avec le bouton droit **Activity1.xaml** dans **l’Explorateur de solutions** et choisissez **supprimer**. Pour confirmer, cliquez sur **OK** .  
  
### <a name="to-create-the-readint-activity"></a>Pour créer l'activité ReadInt  
  
1.  Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.  
  
2.  Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**. Sélectionnez **activité de Code** à partir de la **Workflow** liste.  
  
3.  Type `ReadInt` dans les **nom** , puis cliquez sur **ajouter**.  
  
4.  Remplacez la définition `ReadInt` existante par la définition suivante.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code. <xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.  
  
### <a name="to-create-the-prompt-activity"></a>Pour créer l'activité Prompt  
  
1.  Appuyez sur CTRL+MAJ+B pour générer le projet. La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.  
  
2.  Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.  
  
3.  Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **Workflow** liste.  
  
4.  Type `Prompt` dans les **nom** , puis cliquez sur **ajouter**.  
  
5.  Double-cliquez sur **Prompt.xaml** dans **l’Explorateur de solutions** à afficher dans le concepteur si elle n’est pas affichée.  
  
6.  Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour afficher le **Arguments** volet.  
  
7.  Cliquez sur **créer un Argument**.  
  
8.  Type `BookmarkName` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.  
  
9. Cliquez sur **créer un Argument**.  
  
10. Type `Result` dans les **nom** zone située sous récemment ajouté `BookmarkName` argument, sélectionnez **hors** à partir de la **Direction** la liste déroulante, sélectionnez **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.  
  
11. Cliquez sur **créer un Argument**.  
  
12. Type `Text` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** la liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.  
  
     Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.  
  
13. Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.  
  
14. Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette de la **Invite** Concepteur d’activités.  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
15. Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-la sur la **déposer l’activité ici** étiquette de la **Séquence** activité.  
  
16. Lier le **texte** argument de la **WriteLine** activité à la **texte** argument de la **invite** activité en tapant `Text` dans le **entrer une expression c#** ou **entrer une expression VB** zone le **propriétés** fenêtre et appuyez sur l’onglet clé deux fois. Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété. Cette propriété peut également être définie en tapant `Text` dans les **entrer une expression c#** ou **entrer une expression VB** zone sur l’activité elle-même.  
  
    > [!TIP]
    >  Si le **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.  
  
17. Faites glisser un **ReadInt** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-la dans le **séquence** activité afin qu’elle suive le **WriteLine** activité.  
  
18. Lier le **BookmarkName** argument de la **ReadInt** activité à la **BookmarkName** argument de la **invite** activité en tapant `BookmarkName` dans les **entrer une expression VB** zone située à droite de la **BookmarkName** argument dans le **fenêtre Propriétés**, puis appuyez sur la touche TAB deux reprises pour fermer la fenêtre de membres de liste IntelliSense et d’enregistrer la propriété.  
  
19. Lier le **résultat** argument de la **ReadInt** activité à la **résultat** argument de la **invite** activité en tapant `Result` dans le **entrer une expression VB** zone située à droite de la **résultat** argument dans le **fenêtre Propriétés**, puis appuyez sur la touche TAB.  
  
20. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur la création d’un flux de travail à l’aide de ces activités, consultez l’étape suivante du didacticiel, [Comment : créer un flux de travail](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Conception et implémentation d’activités personnalisées](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Didacticiel Bien démarrer](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Guide pratique pour créer un workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Utilisation d’ExpressionTextBox dans un concepteur d’activités personnalisées](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
