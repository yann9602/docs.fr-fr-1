---
title: "Comment&#160;: d&#233;finir une ic&#244;ne pour un bouton ToolBar &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "boutons (Windows Forms), images"
  - "exemples (Windows Forms), barres d'outils"
  - "icônes (Windows Forms), boutons de barre d'outils"
  - "images (Windows Forms), boutons de barre d'outils"
  - "ToolBar (contrôle Windows Forms), ajouter des icônes aux boutons"
  - "barres d'outils (Windows Forms), ajouter des icônes aux boutons"
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;finir une ic&#244;ne pour un bouton ToolBar &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les boutons <xref:System.Windows.Forms.ToolBar> sont capables d'afficher des icônes pour faciliter l'identification par les utilisateurs.  Cela s'obtient en ajoutant des images dans le composant <xref:System.Windows.Forms.ImageList> et en l'associant au contrôle <xref:System.Windows.Forms.ToolBar>.  
  
 La procédure suivante nécessite un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ToolBar> et un composant <xref:System.Windows.Forms.ImageList>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir l'icône d'un bouton de barre d'outils au moment du design  
  
1.  Ajoutez des images au composant <xref:System.Windows.Forms.ImageList>.  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des images ImageList avec le concepteur](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Sélectionnez le contrôle <xref:System.Windows.Forms.ToolBar> sur votre formulaire.  
  
3.  Dans la fenêtre **Propriétés**, affectez le composant <xref:System.Windows.Forms.ImageList> à la propriété <xref:System.Windows.Forms.ToolBar.ImageList%2A> du contrôle <xref:System.Windows.Forms.ToolBar>.  
  
4.  Cliquez sur la propriété <xref:System.Windows.Forms.ToolBar.Buttons%2A> du contrôle <xref:System.Windows.Forms.ToolBar> pour la sélectionner, puis sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour ouvrir l'**éditeur de collections ToolBarButton**.  
  
5.  Utilisez le bouton **Ajouter** pour ajouter des boutons au contrôle <xref:System.Windows.Forms.ToolBar>.  
  
6.  Dans la fenêtre **Propriétés** qui s'affiche dans le volet situé dans la partie droite de l'**éditeur de collections ToolBarButton**, affectez à la propriété <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> de chaque bouton de barre d'outils une des valeurs de la liste, laquelle est issue des images que vous avez ajoutées au composant <xref:System.Windows.Forms.ImageList>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolBar>   
 [Comment : déclencher des événements de menu pour les boutons de barre d'outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)