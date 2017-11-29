---
title: Vue d'ensemble de Menu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81611e7c5f509314b10e3188106870bdc67dfb0e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="menu-overview"></a>Vue d'ensemble de Menu
La <xref:System.Windows.Controls.Menu> classe vous permet d’organiser des éléments associés aux commandes et gestionnaires d’événements dans un ordre hiérarchique. Chaque <xref:System.Windows.Controls.Menu> élément contient une collection de <xref:System.Windows.Controls.MenuItem> éléments.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Contrôle Menu  
 Le <xref:System.Windows.Controls.Menu> contrôle présente une liste d’éléments qui spécifient des commandes ou des options pour une application. En règle générale, en cliquant sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou entraîne l’application à exécuter une commande.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Création de menus  
 L’exemple suivant crée un <xref:System.Windows.Controls.Menu> à manipuler du texte dans un <xref:System.Windows.Controls.TextBox>. Le <xref:System.Windows.Controls.Menu> contient <xref:System.Windows.Controls.MenuItem> objets qui utilisent le <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, et <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriétés et le <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, et <xref:System.Windows.Controls.MenuItem.Click> événements.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems avec raccourcis clavier  
 Raccourcis clavier sont des combinaisons de caractères qui peuvent être entrées avec le clavier pour appeler <xref:System.Windows.Controls.Menu> commandes. Par exemple, le raccourci clavier de la **copie** est CTRL+C. Il existe deux propriétés à utiliser avec les raccourcis clavier et des éléments de menu :<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> propriété à attribuer le texte de raccourci clavier à <xref:System.Windows.Controls.MenuItem> contrôles. Cette opération ne fait que placer le raccourci clavier dans l’élément de menu.  Il n’associe pas la commande avec le <xref:System.Windows.Controls.MenuItem>. L’application doit gérer l’entrée de l’utilisateur pour exécuter l’action.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Commande  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.MenuItem.Command%2A> propriété pour associer le **ouvrir** et **enregistrer** avec des commandes <xref:System.Windows.Controls.MenuItem> contrôles. Non seulement la propriété de la commande associer une commande avec un <xref:System.Windows.Controls.MenuItem>, mais elle fournit également le texte de mouvement d’entrée à utiliser comme un raccourci.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Le <xref:System.Windows.Controls.MenuItem> classe a également un <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> propriété qui spécifie l’élément où la commande se produit. Si <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas défini, l’élément qui a le focus clavier reçoit la commande. Pour plus d’informations sur les commandes, consultez [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Styles de menu  
 Avec contrôle de style, vous pouvez modifier considérablement l’apparence et le comportement de <xref:System.Windows.Controls.Menu> contrôles sans devoir écrire un contrôle personnalisé. En plus de définir des propriétés visuelles, vous pouvez également appliquer un <xref:System.Windows.Style> aux parties individuelles d’un contrôle, modifier le comportement de parties du contrôle à travers des propriétés ou ajouter des parties supplémentaires ou modifier la disposition d’un contrôle. Les exemples suivants illustrent plusieurs façons d’ajouter un <xref:System.Windows.Style> à un <xref:System.Windows.Controls.Menu> contrôle.  
  
 Le premier exemple de code définit un <xref:System.Windows.Style> appelée `Simple` qui montre comment utiliser les paramètres système actuels dans votre style. Le code assigne la couleur du pinceau `MenuHighlightBrush` comme couleur d’arrière-plan du menu et celle du pinceau `MenuTextBrush` comme couleur de premier plan du menu. Notez que vous utilisez des clés de ressource pour assigner les pinceaux.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 L’exemple suivant utilise <xref:System.Windows.Trigger> les éléments qui vous permettent de modifier l’apparence d’un <xref:System.Windows.Controls.MenuItem> en réponse aux événements qui se produisent sur le <xref:System.Windows.Controls.Menu>. Lorsque vous déplacez la souris sur le <xref:System.Windows.Controls.Menu>, la couleur de premier plan et de modifier les caractéristiques de police des éléments de menu.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de galerie de contrôles WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
