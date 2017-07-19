---
title: "Proc&#233;dure pas &#224; pas&#160;: mise &#224; disposition d&#39;&#233;l&#233;ments de menu standard pour un formulaire | Microsoft Docs"
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
  - "éléments de menu, standard"
  - "StatusStrip (contrôle Windows Forms)"
  - "barres d'outils (Windows Forms), procédures pas à pas"
  - "ToolStrip (contrôle Windows Forms)"
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Proc&#233;dure pas &#224; pas&#160;: mise &#224; disposition d&#39;&#233;l&#233;ments de menu standard pour un formulaire
Vous pouvez fournir un menu standard pour vos formulaires avec le contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
 Cette procédure pas à pas montre comment utiliser un contrôle <xref:System.Windows.Forms.MenuStrip> pour créer un menu standard.  Le formulaire répond également quand un utilisateur sélectionne un élément de menu.  Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d'un projet Windows Forms.  
  
-   Création d'un menu standard.  
  
-   Création d'un contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
-   Gestion de la sélection des éléments de menu.  
  
 Lorsque vous aurez terminé, vous disposerez d'un formulaire doté d'un menu standard affichant les sélections d'éléments de menu dans un contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : fournir des éléments de menu standard à un formulaire](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Avoir des autorisations suffisantes pour être en mesure de créer et d'exécuter des projets d'application Windows Forms sur l'ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé StandardMenuForm.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans le Concepteur Windows Forms, sélectionnez le formulaire.  
  
## Création d'un menu standard  
 Le Concepteur Windows Forms peut remplir automatiquement un contrôle <xref:System.Windows.Forms.MenuStrip> avec des éléments de menu standard.  
  
#### Pour créer un menu standard  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> dans votre formulaire.  
  
2.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) du contrôle <xref:System.Windows.Forms.MenuStrip>, puis sélectionnez **Insérer des éléments standard**.  
  
     Le contrôle <xref:System.Windows.Forms.MenuStrip> est rempli avec les éléments de menu standard.  
  
3.  Cliquez sur l'élément de menu **Fichier** pour voir ses éléments de menu par défaut et les icônes correspondantes.  
  
## Création d'un contrôle StatusStrip  
 Utilisez le contrôle <xref:System.Windows.Forms.StatusStrip> pour afficher l'état de vos applications Windows Forms.  Dans l'exemple actuel, les éléments de menu sélectionnés par l'utilisateur sont affichés dans un contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
#### Pour créer un contrôle StatusStrip  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.StatusStrip> dans votre formulaire.  
  
     Le contrôle <xref:System.Windows.Forms.StatusStrip> s'ancre automatiquement en bas du formulaire.  
  
2.  Cliquez sur le bouton déroulant du contrôle <xref:System.Windows.Forms.StatusStrip> et sélectionnez **StatusLabel** pour ajouter un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> au contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
## Gestion de la sélection d'élément  
 Gérez l'événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> pour répondre à la sélection d'un élément de menu par l'utilisateur.  
  
#### Pour gérer la sélection d'élément  
  
1.  Cliquez sur l'élément de menu **Fichier** que vous avez créé dans la section Création d'un menu standard.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur **Événements**.  
  
3.  Double\-cliquez sur l'événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.  
  
     Le Concepteur Windows Forms génère un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.  
  
4.  Insérez le code suivant dans le gestionnaire d'événements.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Insérez la définition de méthode utilitaire `UpdateStatus` dans le formulaire.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## Point de contrôle  
  
#### Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur l'élément de menu **Fichier** pour ouvrir le menu.  
  
3.  Dans le menu **Fichier**, cliquez sur l'un des éléments pour le sélectionner.  
  
     Le contrôle <xref:System.Windows.Forms.StatusStrip> affiche l'élément sélectionné.  
  
## Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un formulaire avec un menu standard.  Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à bien d'autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.  Pour plus d'informations, consultez [Vue d'ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créez un formulaire d'interface multidocument \(MDI\) avec des contrôles d'ancrage <xref:System.Windows.Forms.ToolStrip>.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Donnez à vos contrôles <xref:System.Windows.Forms.ToolStrip> un aspect professionnel.  Pour plus d'informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)