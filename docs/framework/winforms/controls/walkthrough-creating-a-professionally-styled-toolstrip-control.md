---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le ToolStrip de style professionnel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "barres d'outils (Windows Forms), procédures pas à pas"
  - "ToolStrip (contrôle Windows Forms), créer des contrôles de style professionnel"
  - "ToolStripProfessionalRenderer (classe Windows Forms)"
  - "ToolStripRenderer (classe Windows Forms)"
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le ToolStrip de style professionnel
Vous pouvez donner une apparence et un comportement professionnels aux contrôles <xref:System.Windows.Forms.ToolStrip> de votre application en écrivant votre propre classe dérivée du type <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
 Cette procédure pas à pas montre comment utiliser des contrôles <xref:System.Windows.Forms.ToolStrip> pour créer un contrôle composite qui ressemble au **Volet de navigation** fourni par Microsoft® Outlook®.  Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d'un projet Bibliothèque de contrôles Windows.  
  
-   Conception du contrôle StackView.  
  
-   Implémentation d'un convertisseur personnalisé.  
  
 Lorsque vous avez terminé, vous disposez d'un contrôle client personnalisé réutilisable doté de l'apparence professionnelle d'un contrôle Microsoft Office® XP.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un contrôle ToolStrip de style professionnel](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Avoir des autorisations suffisantes pour être en mesure de créer et d'exécuter des projets d'application Windows Forms sur l'ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## Création d'un projet Bibliothèque de contrôles Windows.  
 La première étape consiste à créer le projet Bibliothèque de contrôles.  
  
#### Pour créer le projet de bibliothèque de contrôles  
  
1.  Créez un projet Bibliothèque de contrôles Windows appelé `StackViewLibrary`.  
  
2.  Dans l'**Explorateur de solutions**, supprimez le contrôle par défaut du projet en supprimant le fichier source nommé "UserControl1.cs" ou "UserControl1.vb", selon le langage de votre choix.  
  
     Pour plus d'informations, consultez [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/fr-fr/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Ajoutez un nouvel élément <xref:System.Windows.Forms.UserControl> au projet **StackViewLibrary**.  Donnez le nom de base `StackView` au nouveau fichier source.  
  
## Conception du contrôle StackView  
 Le contrôle `StackView` est un contrôle composite doté d'un contrôle <xref:System.Windows.Forms.ToolStrip> enfant.  Pour plus d'informations sur les contrôles composites, consultez [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### Pour concevoir le contrôle StackView  
  
1.  Depuis la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ToolStrip> vers l'aire de conception.  
  
2.  Dans la fenêtre **Propriétés**, définissez les propriétés du contrôle <xref:System.Windows.Forms.ToolStrip> en fonction du tableau suivant.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |Nom|`stackStrip`|  
    |CanOverflow|`false`|  
    |Dock|<xref:System.Windows.Forms.DockStyle>|  
    |Police|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle>|  
    |Padding|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode>|  
  
3.  Dans le Concepteur Windows Forms, cliquez sur le bouton **Ajouter** du contrôle <xref:System.Windows.Forms.ToolStrip> et ajoutez un <xref:System.Windows.Forms.ToolStripButton> au contrôle `stackStrip`.  
  
4.  Dans la fenêtre **Propriétés**, définissez les propriétés du contrôle <xref:System.Windows.Forms.ToolStripButton> en fonction du tableau suivant.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |Nom|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margin|`0, 0, 0, 0`|  
    |Padding|`3, 3, 3, 3`|  
    |Texte|Courrier|  
    |TextAlign|<xref:System.Drawing.ContentAlignment>|  
  
5.  Répétez l'étape 7 pour trois contrôles <xref:System.Windows.Forms.ToolStripButton> supplémentaires.  
  
     Nommez les contrôles `calendarStackButton`, `contactsStackButton` et `tasksStackButton`.  Affectez à la propriété <xref:System.Windows.Forms.Control.Text%2A> les valeurs Calendrier, Contacts et Tâches, respectivement.  
  
## Gestion des événements  
 Pour que le contrôle `StackView` se comporte correctement, deux événements sont nécessaires.  Gérez l'événement <xref:System.Windows.Forms.UserControl.Load> pour positionner le contrôle correctement.  Gérez l'événement <xref:System.Windows.Forms.ToolStripItem.Click> pour chaque <xref:System.Windows.Forms.ToolStripButton> afin de donner à l'état du contrôle `StackView` un comportement identique au contrôle <xref:System.Windows.Forms.RadioButton>.  
  
#### Pour gérer des événements  
  
1.  Dans le Concepteur Windows Forms, sélectionnez le contrôle `StackView`.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur **Événements**.  
  
3.  Double\-cliquez sur l'événement Load pour générer le gestionnaire d'événements `StackView_Load`.  
  
4.  Dans le gestionnaire d'événements `StackView_Load`, copiez et collez le code suivant.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Dans le Concepteur Windows Forms, sélectionnez le contrôle `mailStackButton`.  
  
6.  Dans la fenêtre **Propriétés**, cliquez sur **Événements**.  
  
7.  Double\-cliquez sur l'événement Click.  
  
     Le Concepteur Windows Forms génère le gestionnaire d'événements `mailStackButton_Click`.  
  
8.  Remplacez le nom du gestionnaire d'événements `mailStackButton_Click` par `stackButton_Click`.  
  
     Pour plus d'informations, consultez [How to: Rename an Identifier \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Insérez le code suivant dans le gestionnaire d'événements `stackButton_Click`.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Dans le Concepteur Windows Forms, sélectionnez le contrôle `calendarStackButton`.  
  
11. Dans la fenêtre **Propriétés**, affectez à l'événement Click le gestionnaire d'événements `stackButton_Click`.  
  
12. Répétez les étapes 10 et 11 pour les contrôles `contactsStackButton` et `tasksStackButton`.  
  
## Définition d'icônes  
 Chaque bouton `StackView` a une icône associée.  Pour plus de facilité, chaque icône est représentée sous forme de chaîne encodée en base64 qui est désérialisée avant qu'un <xref:System.Drawing.Bitmap> ne soit créé à partir de celle\-ci.  Dans un environnement de production, vous stockez des données Bitmap en tant que ressource et vos icônes s'affichent dans le Concepteur Windows Forms.  Pour plus d'informations, consultez [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/fr-fr/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### Pour définir des icônes  
  
1.  Dans l'éditeur de code, insérez le code suivant dans la définition de classe `StackView`.  Ce code initialise les bitmaps pour les icônes <xref:System.Windows.Forms.ToolStripButton>.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Ajoutez un appel à la méthode `InitializeImages` dans le constructeur de classe `StackView`.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## Implémentation d'un convertisseur personnalisé  
 Vous pouvez personnaliser la plupart des éléments du contrôle `StackView` en implémentant une classe qui dérive de la classe <xref:System.Windows.Forms.ToolStripRenderer>.  Dans cette procédure, vous implémenterez une classe <xref:System.Windows.Forms.ToolStripProfessionalRenderer> qui personnalise la poignée et dessine des arrière\-plans dégradés pour les contrôles <xref:System.Windows.Forms.ToolStripButton>.  
  
#### Pour implémenter un convertisseur personnalisé  
  
1.  Insérez le code suivant dans la définition du contrôle `StackView`.  
  
     Il s'agit de la définition de la classe `StackRenderer` qui substitue les méthodes <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder> et <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> afin de produire une apparence personnalisée.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  Dans le constructeur du contrôle `StackView`, créez une nouvelle instance de la classe `StackRenderer` et assignez\-la à la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A> du contrôle `stackStrip`.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## Test du contrôle StackView  
 Le contrôle `StackView` dérive de la classe <xref:System.Windows.Forms.UserControl>.  Par conséquent, vous pouvez tester le contrôle à l'aide du **Conteneur de test UserControl**.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### Pour tester le contrôle StackView  
  
1.  Appuyez sur F5 pour générer le projet et lancer le **Conteneur de test UserControl**.  
  
2.  Déplacez le pointeur sur les boutons du contrôle `StackView`, puis cliquez sur un bouton pour visualiser l'apparence de son état sélectionné.  
  
## Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un contrôle client personnalisé réutilisable doté de l'apparence professionnelle d'un contrôle Office XP.  Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à bien d'autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.  Pour plus d'informations, consultez [Vue d'ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créer un formulaire doté d'un menu standard automatiquement rempli.  Pour plus d'informations, consultez [Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Créez un formulaire d'interface multidocument \(MDI\) avec des contrôles d'ancrage <xref:System.Windows.Forms.ToolStrip>.  Pour plus d'informations, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [Comment : fournir des éléments de menu standard à un formulaire](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)