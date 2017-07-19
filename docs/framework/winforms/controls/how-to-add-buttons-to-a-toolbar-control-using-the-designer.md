---
title: "Comment&#160;: ajouter des boutons &#224; un contr&#244;le ToolBar &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "exemples (Windows Forms), barres d'outils"
  - "ToolBar (contrôle Windows Forms), ajouter des boutons"
  - "ToolBar (contrôle Windows Forms), ajouter des menus déroulants"
  - "ToolBar (contrôle Windows Forms), ajouter des séparateurs"
  - "barres d'outils (Windows Forms), ajouter des boutons"
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: ajouter des boutons &#224; un contr&#244;le ToolBar &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les boutons que vous ajoutez au contrôle <xref:System.Windows.Forms.ToolBar> sont une partie intégrante de ce dernier.  Ces boutons peuvent être utilisés pour accéder facilement aux commandes de menu, mais ils peuvent également être placés dans une autre zone de l'interface utilisateur de votre application pour exposer à vos utilisateurs des commandes qui ne sont pas disponibles dans la structure de menu.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ToolBar>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter des boutons au moment du design  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.ToolBar>.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur la propriété <xref:System.Windows.Forms.ToolBar.Buttons%2A> pour la sélectionner, puis sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour ouvrir l'**éditeur de collections ToolBarButton**.  
  
3.  Utilisez les boutons **Ajouter** et **Supprimer** pour ajouter des boutons au contrôle <xref:System.Windows.Forms.ToolBar> ou en supprimer.  
  
4.  Configurez les propriétés des boutons individuels dans la fenêtre **Propriétés** qui s'affiche dans le volet situé dans la partie droite de l'éditeur.  Le tableau suivant présente des propriétés importantes à prendre en compte  
  
    |Propriété|Description|  
    |---------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Définit le menu à afficher dans le bouton déroulant de barre d'outils.  La propriété <xref:System.Windows.Forms.ToolBarButton.Style%2A> du bouton de barre d'outils doit avoir la valeur <xref:System.Windows.Forms.ToolBarButtonStyle>.  Cette propriété utilise une instance de la classe <xref:System.Windows.Forms.ContextMenu> comme référence.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Définit si un bouton bascule de barre d'outils est partiellement enfoncé.  La propriété <xref:System.Windows.Forms.ToolBarButton.Style%2A> du bouton de barre d'outils doit avoir la valeur <xref:System.Windows.Forms.ToolBarButtonStyle>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Définit si un bouton bascule de barre d'outils est actuellement enfoncé.  La propriété <xref:System.Windows.Forms.ToolBarButton.Style%2A> du bouton de barre d'outils doit avoir la valeur <xref:System.Windows.Forms.ToolBarButtonStyle> ou <xref:System.Windows.Forms.ToolBarButtonStyle>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Définit le style du bouton de barre d'outils.  Doit avoir l'une des valeurs de l'énumération <xref:System.Windows.Forms.ToolBarButtonStyle>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|La chaîne de texte affichée par le bouton.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Le texte affiché sous forme d'info\-bulle du bouton.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue et créer les volets spécifiés.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolBar>   
 [Comment : définir une icône pour un bouton de barre d'outils](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [Comment : déclencher des événements de menu pour les boutons de barre d'outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [Vue d'ensemble du contrôle ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)   
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)