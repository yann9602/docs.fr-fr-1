---
title: "Vue d&#39;ensemble du contr&#244;le ToolBar (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ToolBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolBar (contrôle Windows Forms), à propos des contrôles ToolBar"
  - "barres d'outils (Windows Forms), à propos des barres d'outils"
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble du contr&#244;le ToolBar (Windows Forms)
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle <xref:System.Windows.Forms.ToolBar> Windows Forms est utilisé dans les formulaires comme une barre de contrôles affichant une rangée de menus déroulants et de boutons bitmap qui activent des commandes.  Ainsi, le fait de cliquer sur un bouton de barre d'outils peut revenir à choisir une commande dans un menu.  Les boutons peuvent être configurés pour apparaître et se comporter comme des boutons de commande, des menus déroulants ou des séparateurs.  En règle générale, une barre d'outils contient des boutons et des menus correspondant à des éléments dans la structure de menus d'une application et offre ainsi un accès rapide à ses fonctions et commandes les plus fréquemment utilisées.  
  
## Utilisation du contrôle ToolBar  
 Un contrôle <xref:System.Windows.Forms.ToolBar> est généralement « ancré » en haut de la fenêtre parent, mais il peut également être ancré de n'importe quel côté de la fenêtre.  Une barre d'outils peut afficher des info\-bulles lorsque l'utilisateur pointe avec la souris sur un bouton.  Une info\-bulle est une petite fenêtre indépendante contenant une brève description de la fonction du bouton ou du menu.  Pour afficher les info\-bulles, la propriété <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> doit avoir la valeur `true`.  
  
> [!NOTE]
>  Certaines applications comportent des contrôles très similaires à la barre d'outils, capables de « flotter » au\-dessus de la fenêtre d'application et d'être repositionnés.  Le contrôle ToolBar Windows Forms ne permet pas ces actions.  
  
 Lorsque la propriété <xref:System.Windows.Forms.ToolBar.Appearance%2A> a la valeur [Normal](frlrfSystemWindowsFormsToolBarAppearanceClassTopic), les boutons de barre d'outils s'affichent en relief et en trois dimensions.  Vous pouvez attribuer à la propriété <xref:System.Windows.Forms.ToolBar.Appearance%2A> de la barre d'outils la valeur <xref:System.Windows.Forms.ToolBarAppearance> pour donner à la barre d'outils et à ses boutons un aspect plat.  Lorsque le pointeur de la souris passe sur un bouton à deux dimensions, ce dernier prend un aspect tridimensionnel.  Les boutons de barre d'outils peuvent être divisés en groupes logiques à l'aide de séparateurs.  Un séparateur est un bouton de barre d'outils avec la propriété <xref:System.Windows.Forms.ToolBarButton.Style%2A> ayant la valeur [Séparateur](frlrfSystemWindowsFormsToolBarButtonStyleClassTopic).  Il se présente comme un espace vide dans la barre d'outils.  Lorsque la barre d'outils a un aspect à deux dimensions, les séparateurs se présentent comme des lignes et non comme des espaces entre les boutons.  
  
 Le contrôle <xref:System.Windows.Forms.ToolBar> permet de créer des barres d'outils en ajoutant des objets <xref:System.Windows.Forms.Button> à une collection <xref:System.Windows.Forms.ToolBar.Buttons%2A>.  Vous pouvez utiliser l'Éditeur de collections pour ajouter des boutons à un contrôle <xref:System.Windows.Forms.ToolBar> ; à chaque objet <xref:System.Windows.Forms.Button> doit être assigné un texte ou une image \(ou les deux\).  L'image est fournie par un composant [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) associé.  Au moment de l'exécution, vous pouvez ajouter ou retirer des boutons de la <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> à l'aide des méthodes <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> et <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>.  Pour programmer les boutons d'une <xref:System.Windows.Forms.ToolBar>, ajoutez le code aux événements <xref:System.Windows.Forms.ToolBar.ButtonClick> de la <xref:System.Windows.Forms.ToolBar>, à l'aide de la propriété <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> de la classe <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> afin de déterminer le bouton qui a fait l'objet d'un clic.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolBar>   
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [Comment : ajouter des boutons à un contrôle ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [Comment : définir une icône pour un bouton de barre d'outils](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [Comment : déclencher des événements de menu pour les boutons de barre d'outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)