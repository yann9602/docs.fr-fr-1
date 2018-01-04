---
title: "Guide pratique pour raccorder une commande à un contrôle avec prise en charge de commande"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b190868b8718442966a22d7be14d976ec47f53b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Guide pratique pour raccorder une commande à un contrôle avec prise en charge de commande
L’exemple suivant montre comment raccorder un <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Control> qui a généré prise en charge de la commande.  Pour obtenir un exemple complet qui raccorde des commandes à plusieurs sources, consultez l’exemple [Créer un exemple RoutedCommand personnalisé](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une bibliothèque de commandes courantes que les programmeurs d’applications rencontrent régulièrement.  Les classes qui constituent la bibliothèque de commandes sont : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, et <xref:System.Windows.Documents.EditingCommands>.  
  
 La méthode statique <xref:System.Windows.Input.RoutedCommand> les objets qui composent ces classes ne fournissent pas la logique de commande.  La logique de la commande est associée à la commande avec un <xref:System.Windows.Input.CommandBinding>.  Certains contrôles ont un CommandBindings intégré pour certaines commandes.  Ce mécanisme permet à la sémantique d’une commande de rester la même, tandis que l’implémentation réelle peut changer.  A <xref:System.Windows.Controls.TextBox>, par exemple, gère les <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande différemment à un contrôle conçu pour prendre en charge des images, mais l’idée de ce que signifie le point de coller un élément reste le même.  La logique de commande ne peut pas être fournie par la commande. Elle doit plutôt être fournie par le contrôle ou l’application.  
  
 De nombreux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offrent une prise en charge intégrée de certaines commandes de la bibliothèque de commandes.  <xref:System.Windows.Controls.TextBox>, par exemple, prend en charge la plupart des commandes de modification d’application telles que <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, et <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Le développeur d’application n’a aucune action spéciale à effectuer pour que ces commandes fonctionnent avec ces contrôles.  Si le <xref:System.Windows.Controls.TextBox> est la cible de commande lorsque la commande est exécutée, elle gère la commande à l’aide de la <xref:System.Windows.Input.CommandBinding> qui est intégré au contrôle.  
  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.MenuItem> comme source de commande pour le <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande, où un <xref:System.Windows.Controls.TextBox> est la cible de la commande.  La logique qui définit comment les <xref:System.Windows.Controls.TextBox> effectue le collage est intégré à la <xref:System.Windows.Controls.TextBox> contrôle.  
  
 A <xref:System.Windows.Controls.MenuItem> est créé et il est <xref:System.Windows.Controls.MenuItem.Command%2A> est définie sur la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande.  Le <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas définie explicitement sur la <xref:System.Windows.Controls.TextBox> objet.  Lorsque le <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n'est pas définie, la cible de la commande est l’élément qui a le focus clavier.  Si l’élément qui a le focus clavier ne prend pas en charge la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande ou Impossible actuellement d’exécuter la commande Coller (le Presse-papiers est vide, par exemple), le <xref:System.Windows.Controls.MenuItem> est grisée.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Raccorder une commande à un contrôle sans prise en charge de commande](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
