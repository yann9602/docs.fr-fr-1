---
title: Vue d'ensemble du composant MainMenu (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f5cfe3a97bbbd4d5ba2d3ba089736599b6a2190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a>Vue d'ensemble du composant MainMenu (Windows Forms)
> [!IMPORTANT]
>  Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacer et ajouter des fonctionnalités à la <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> contrôles des versions antérieures, <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous choisissez.  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> composant affiche un menu au moment de l’exécution. Tous les sous-menus du menu principal et les éléments individuels sont <xref:System.Windows.Forms.MenuItem> objets.  
  
## <a name="key-properties"></a>Principales propriétés  
 Un élément de menu peut être désigné comme élément par défaut en définissant le <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> propriété `true`. L’élément par défaut s’affiche en gras lorsque l’utilisateur clique sur le menu. L’élément de menu <xref:System.Windows.Forms.MenuItem.Checked%2A> propriété est `true` ou `false`et indique si l’élément de menu est sélectionné. L’élément de menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> propriété personnalise l’apparence de l’élément sélectionné : si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> a la valeur `true`, une case s’affiche en regard de l’élément ; si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> a la valeur `false`, une coche apparaît en regard de l’élément.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
