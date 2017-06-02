---
title: "Vue d&#39;ensemble du composant MainMenu (Windows Forms) | Microsoft Docs"
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
  - "MenuItem"
  - "MainMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MainMenu (contrôle Windows Forms), à propos du contrôle MainMenu"
  - "menus"
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du composant MainMenu (Windows Forms)
> [!IMPORTANT]
>  Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent les contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes et leur ajoutent des fonctionnalités, <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Le composant <xref:System.Windows.Forms.MainMenu> Windows Forms permet d'afficher un menu au moment de l'exécution.  Tous les sous\-menus du menu principal et leurs éléments sont des objets <xref:System.Windows.Forms.MenuItem>.  
  
## Propriétés de clé  
 Un élément de menu peut être désigné comme élément par défaut si vous affectez à la propriété <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> la valeur `true`.  L'élément par défaut s'affiche en gras lorsque l'utilisateur clique sur le menu.  La propriété <xref:System.Windows.Forms.MenuItem.Checked%2A> de l'élément de menu peut avoir la valeur `true` ou `false`, et indique si l'élément de menu est sélectionné.  La propriété <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> de l'élément de menu personnalise l'apparence de l'élément sélectionné :<xref:System.Windows.Forms.MenuItem.RadioCheck%2A> si sa valeur est `true`, une case d'option apparaît en regard de l'élément ;<xref:System.Windows.Forms.MenuItem.RadioCheck%2A> si sa valeur est `false`, une coche apparaît en regard de l'élément.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MainMenu>   
 <xref:System.Windows.Forms.Menu>   
 <xref:System.Windows.Forms.MenuItem>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)