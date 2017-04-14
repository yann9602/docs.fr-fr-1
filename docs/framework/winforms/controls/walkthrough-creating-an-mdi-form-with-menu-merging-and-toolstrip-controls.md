---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un formulaire MDI avec la fusion de menus et des contr&#244;les ToolStrip | Microsoft Docs"
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
  - "formulaires MDI"
  - "formulaires MDI, créer"
  - "formulaires MDI, procédures pas à pas"
  - "MDI, créer des formulaires"
  - "interface multidocument (MDI) (formulaires)"
  - "barres d'outils (Windows Forms)"
  - "ToolStrip (contrôle Windows Forms)"
  - "ToolStripPanel (contrôle Windows Forms)"
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un formulaire MDI avec la fusion de menus et des contr&#244;les ToolStrip
L'espace de noms <xref:System.Windows.Forms?displayProperty=fullName> prend en charge les applications d'interface multidocument \(MDI\), et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus.  Les formulaires MDI peuvent également conserver des contrôles <xref:System.Windows.Forms.ToolStrip>.  
  
 Cette procédure pas à pas montre comment utiliser des contrôles <xref:System.Windows.Forms.ToolStripPanel> avec un formulaire MDI.  Le formulaire prend également en charge la fusion de menus avec les menus enfants.  Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d'un projet Windows Forms.  
  
-   Création du menu principal de votre formulaire.  Le nom réel du menu changera.  
  
-   Ajout du contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils**.  
  
-   Création d'un formulaire enfant.  
  
-   Réorganisation des contrôles <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan.  
  
 Lorsque vous aurez terminé, vous disposerez d'un formulaire MDI prenant en charge la fusion de menus et des contrôles <xref:System.Windows.Forms.ToolStrip> déplaçables.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Avoir des autorisations suffisantes pour être en mesure de créer et d'exécuter des projets d'application Windows Forms sur l'ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé MdiForm.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans le Concepteur Windows Forms, sélectionnez le formulaire.  
  
3.  Dans la fenêtre Propriétés, affectez au <xref:System.Windows.Forms.Form.IsMdiContainer%2A> la valeur `true`.  
  
## Création du menu principal.  
 Le formulaire MDI parent contient le menu principal.  Le menu principal possède un élément de menu nommé **Fenêtre**.  À l'aide de l'élément de menu **Fenêtre**, vous pouvez créer des formulaires enfants.  Les éléments de menu issus de formulaires enfants sont fusionnés dans le menu principal.  
  
#### Pour créer le menu principal  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> dans le formulaire.  
  
2.  Ajoutez un <xref:System.Windows.Forms.ToolStripMenuItem> au contrôle <xref:System.Windows.Forms.MenuStrip> et nommez\-le Fenêtre.  
  
3.  Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
4.  Dans la fenêtre Propriétés, affectez la valeur `ToolStripMenuItem1` à la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>.  
  
5.  Ajoutez un sous\-élément à l'élément de menu **Fenêtre**, puis nommez\-le Nouveau.  
  
6.  Dans la fenêtre Propriétés, cliquez sur **Événements**.  
  
7.  Double\-cliquez sur l'événement <xref:System.Windows.Forms.ToolStripItem.Click>.  
  
     Le Concepteur Windows Forms génère un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click>.  
  
8.  Insérez le code suivant dans le gestionnaire d'événements.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## Ajout du contrôle ToolStripPanel à la boîte à outils  
 Lorsque vous utilisez des contrôles <xref:System.Windows.Forms.MenuStrip> avec un formulaire MDI, vous devez avoir le contrôle <xref:System.Windows.Forms.ToolStripPanel>.  Vous devez ajouter le contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur Windows Forms.  
  
#### Pour ajouter le contrôle ToolStripPanel à la boîte à outils  
  
1.  Ouvrez la **Boîte à outils**, puis cliquez sur l'onglet **Tous les Windows Forms** pour afficher les contrôles Windows Forms disponibles.  
  
2.  Cliquez avec le bouton droit pour ouvrir le menu contextuel et sélectionnez **Choisir les éléments**.  
  
3.  Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, faites défiler la colonne **Nom** vers le bas jusqu'à **ToolStripPanel**.  
  
4.  Activez la case à cocher pour **ToolStripPanel**, puis cliquez sur **OK**.  
  
     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> apparaît dans la **boîte à outils**.  
  
## Création d'un formulaire enfant  
 Dans cette procédure, vous définirez une classe de formulaire enfant séparée qui a son propre contrôle <xref:System.Windows.Forms.MenuStrip>.  Les éléments de menu pour ce formulaire sont fusionnés avec ceux du formulaire parent.  
  
#### Pour définir un formulaire enfant  
  
1.  Ajoutez un nouveau formulaire nommé `ChildForm` au projet.  
  
     Pour plus d'informations, consultez [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/fr-fr/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> dans le formulaire enfant.  
  
3.  Cliquez sur le glyph de la balise active du contrôle <xref:System.Windows.Forms.MenuStrip> \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\), puis sélectionnez **Modifier les éléments**.  
  
4.  Dans la boîte de dialogue **Éditeur de collections Items**, ajoutez un nouveau <xref:System.Windows.Forms.ToolStripMenuItem>nommé ChildMenuItem au menu enfant.  
  
     Pour plus d'informations, consultez [ToolStrip Items Collection Editor](http://msdn.microsoft.com/fr-fr/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## Test du formulaire  
  
#### Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur l'élément de menu **Fenêtre** pour ouvrir le menu, puis sur **Nouveau**.  
  
     Un nouveau formulaire enfant est créé dans la zone cliente MDI du formulaire.  Le menu du formulaire enfant est fusionné avec le menu principal.  
  
3.  Fermez le formulaire enfant.  
  
     Le menu du formulaire enfant est supprimé du menu principal.  
  
4.  Cliquez plusieurs fois sur **Nouveau**.  
  
     Les formulaires enfants sont automatiquement répertoriés sous l'élément de menu **Fenêtre** car la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> du contrôle <xref:System.Windows.Forms.MenuStrip> est assignée.  
  
## Ajout de la prise en charge de ToolStrip  
 Dans cette procédure, vous ajouterez quatre contrôles <xref:System.Windows.Forms.ToolStrip> au formulaire parent MDI.  Chaque contrôle <xref:System.Windows.Forms.ToolStrip> est ajouté à l'intérieur d'un contrôle <xref:System.Windows.Forms.ToolStripPanel>, lequel est ancré au bord du formulaire.  
  
#### Pour ajouter des contrôles ToolStrip au formulaire parent MDI  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ToolStripPanel> dans le formulaire.  
  
2.  Le contrôle <xref:System.Windows.Forms.ToolStripPanel> étant sélectionné, double\-cliquez sur le contrôle <xref:System.Windows.Forms.ToolStrip> dans la **boîte à outils**.  
  
     Un contrôle <xref:System.Windows.Forms.ToolStrip> est créé dans le contrôle <xref:System.Windows.Forms.ToolStripPanel>.  
  
3.  Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.  
  
4.  Dans la fenêtre Propriétés, remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle par <xref:System.Windows.Forms.DockStyle>.  
  
     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> s'ancre sur le côté gauche du formulaire, sous le menu principal.  La zone cliente MDI s'ajuste au contrôle <xref:System.Windows.Forms.ToolStripPanel>.  
  
5.  Répétez les étapes 1 à 4.  
  
     Ancrez le nouveau contrôle <xref:System.Windows.Forms.ToolStripPanel> au bord supérieur du formulaire.  
  
     Le contrôle <xref:System.Windows.Forms.ToolStripPanel> est ancré sous le menu principal, mais à droite du premier contrôle <xref:System.Windows.Forms.ToolStripPanel>.  Cette étape illustre l'importance de l'ordre de plan pour positionner correctement les contrôles <xref:System.Windows.Forms.ToolStripPanel>.  
  
6.  Répétez les étapes 1 à 4 pour deux autres contrôles <xref:System.Windows.Forms.ToolStripPanel>.  
  
     Ancrez les nouveaux contrôles <xref:System.Windows.Forms.ToolStripPanel> à droite et en bas du formulaire.  
  
## Organisation des contrôles ToolStripPanel suivant l'ordre de plan  
 La position d'un contrôle <xref:System.Windows.Forms.ToolStripPanel> ancré sur votre formulaire MDI est déterminée par sa position dans l'ordre de plan.  Vous pouvez facilement organiser l'ordre de plan de vos contrôles dans la fenêtre Structure du document.  
  
#### Pour organiser les contrôles ToolStripPanel suivant l'ordre de plan  
  
1.  Dans le menu **Affichage**, cliquez sur **Autres fenêtres** , puis sur **Structure du document**.  
  
     La disposition de vos contrôles <xref:System.Windows.Forms.ToolStripPanel> issus de la procédure précédente n'est pas standard.  La raison en est que l'ordre de plan n'est pas correct.  Utilisez la fenêtre Structure du document pour modifier l'ordre de plan des contrôles.  
  
2.  Dans la fenêtre Structure du document, sélectionnez **ToolStripPanel4**.  
  
3.  Cliquez plusieurs fois sur le bouton fléché Bas, jusqu'à ce que **ToolStripPanel4** apparaisse en bas de la liste.  
  
     Le contrôle **ToolStripPanel4** est ancré au bord inférieur du formulaire, sous les autres contrôles.  
  
4.  Sélectionnez **ToolStripPanel2**.  
  
5.  Cliquez sur le bouton fléché bas une fois pour positionner le troisième contrôle de la liste.  
  
     Le contrôle **ToolStripPanel2** est ancré au bord supérieur du formulaire, sous le menu principal et au\-dessus des autres contrôles.  
  
6.  Sélectionnez différents contrôles dans la fenêtre **Structure du document** et placez\-les à différents endroits dans l'ordre de plan.  Notez l'effet de l'ordre de plan sur la position des contrôles ancrés.  Utilisez CTRL\+Z ou **Annuler** dans le menu **Edition** pour annuler les modifications apportées.  
  
## Point de contrôle  
  
#### Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur la poignée d'un contrôle <xref:System.Windows.Forms.ToolStrip> et placez\-le à différents endroits sur le formulaire en le faisant glisser.  
  
     Vous pouvez faire glisser un contrôle <xref:System.Windows.Forms.ToolStrip> d'un contrôle <xref:System.Windows.Forms.ToolStripPanel> à un autre.  
  
## Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un formulaire parent MDI avec des contrôles <xref:System.Windows.Forms.ToolStrip> et une fusion de menus.  Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à bien d'autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.  Pour plus d'informations, consultez [Vue d'ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créer un formulaire doté d'un menu standard automatiquement rempli.  Pour plus d'informations, consultez [Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Donnez à vos contrôles <xref:System.Windows.Forms.ToolStrip> un aspect professionnel.  Pour plus d'informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [Comment : insérer un MenuStrip dans un menu déroulant MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)   
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)