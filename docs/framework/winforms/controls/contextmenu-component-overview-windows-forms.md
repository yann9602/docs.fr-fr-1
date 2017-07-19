---
title: "Vue d&#39;ensemble du composant ContextMenu (Windows Forms) | Microsoft Docs"
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
  - "ContextMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "menus contextuels, ContextMenu (composant)"
  - "ContextMenu (composant Windows Forms), à propos du composant ContextMenu"
  - "menus contextuels, ContextMenu (composant)"
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Vue d&#39;ensemble du composant ContextMenu (Windows Forms)
> [!IMPORTANT]
>  Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent les contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes et leur ajoutent des fonctionnalités, <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms permet de fournir aux utilisateurs un menu contextuel aisément accessible constitué des commandes les plus fréquemment utilisées qui sont associées à l'objet sélectionné.  Les éléments d'un menu contextuel constituent souvent un sous\-ensemble des éléments des menus principaux qui s'affichent ailleurs dans l'application.  Un utilisateur peut en général accéder à un menu contextuel en cliquant avec le bouton droit sur la souris.  Sur les Windows Forms, les menus contextuels sont associés aux contrôles.  
  
## Propriétés de clé  
 Vous pouvez associer un menu contextuel à un contrôle en affectant comme valeur à la propriété <xref:System.Windows.Forms.Control.ContextMenu%2A> de ce dernier le composant <xref:System.Windows.Forms.ContextMenu>.  Un seul menu contextuel peut être associé à plusieurs contrôles ; toutefois, à chaque contrôle ne peut être associé qu'un seul menu contextuel.  
  
 La principale propriété du composant <xref:System.Windows.Forms.ContextMenu> est <xref:System.Windows.Forms.Menu.MenuItems%2A>.  Vous pouvez ajouter des éléments de menu en créant des objets <xref:System.Windows.Forms.MenuItem> par programme et les ajoutant au <xref:System.Windows.Forms.Menu.MenuItemCollection> du menu contextuel.  Les options d'un menu contextuel étant habituellement extraites d'autres menus, il suffit de les copier pour les ajouter.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContextMenu>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>