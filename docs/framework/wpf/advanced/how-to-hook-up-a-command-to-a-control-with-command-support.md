---
title: "Comment&#160;: raccorder une commande &#224; un contr&#244;le avec prise en charge de commande | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe de contrôle, attacher un RoutedCommand"
  - "classes, contrôle, attacher un RoutedCommand"
  - "RoutedCommand (classe), attacher à un contrôle"
  - "classes, RoutedCommand, attacher à un contrôle"
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: raccorder une commande &#224; un contr&#244;le avec prise en charge de commande
L’exemple suivant montre comment raccorder une <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Control> qui intègre la prise en charge de la commande.  Pour obtenir un exemple complet qui raccorde des commandes à plusieurs sources, consultez le [créer un RoutedCommand personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159980) exemple.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Fournit une bibliothèque de commandes courantes que les programmeurs rencontrent régulièrement.  Les classes qui constituent la bibliothèque de commandes sont : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, et <xref:System.Windows.Documents.EditingCommands>.  
  
 La méthode statique <xref:System.Windows.Input.RoutedCommand> objets qui composent ces classes ne fournissent pas de logique de commande.  La logique de la commande est associée à la commande avec un <xref:System.Windows.Input.CommandBinding>.  Certains contrôles ont CommandBindings intégrées pour certaines commandes.  Ce mécanisme permet à la sémantique d’une commande de rester la même, bien que l’implémentation réelle peut changer.  A <xref:System.Windows.Controls.TextBox>, par exemple, gère les <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande différemment qu’un contrôle conçu pour prendre en charge les images, mais l’idée de ce que cela signifie coller un élément reste le même.  La logique de commande ne peut pas être fournie par la commande, mais plutôt qu’il doit être fournie par le contrôle ou l’application.  
  
 De nombreux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont en charge intégrée pour certaines commandes dans la bibliothèque de commandes.  <xref:System.Windows.Controls.TextBox>, par exemple, prend en charge la plupart des commandes de modification d’application tel que <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, et <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Le développeur d’applications ne devra pas faire quelque chose de spécial pour que ces commandes fonctionnent avec ces contrôles.  Si le <xref:System.Windows.Controls.TextBox> est la cible de commande lorsque la commande est exécutée, il gérera la commande à l’aide de la <xref:System.Windows.Input.CommandBinding> qui est intégré au contrôle.  
  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.MenuItem> comme source de commande pour le <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande, où un <xref:System.Windows.Controls.TextBox> est la cible de la commande.  Toute la logique qui définit comment la <xref:System.Windows.Controls.TextBox> effectue le collage est intégré à la <xref:System.Windows.Controls.TextBox> contrôle.  
  
 A <xref:System.Windows.Controls.MenuItem> est créé et il est <xref:System.Windows.Controls.MenuItem.Command%2A> est définie sur le <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande.  Le <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas définie explicitement sur la <xref:System.Windows.Controls.TextBox> objet.  Lors de la <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas définie, la cible de la commande est l’élément qui a le focus clavier.  Si l’élément qui a le focus clavier ne prend pas en charge la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande ou actuellement impossible d’exécuter la commande Coller (le Presse-papiers est vide, par exemple), la <xref:System.Windows.Controls.MenuItem> apparaît en grisé.  
  
 [!code-xml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des commande](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [Raccorder une commande à un contrôle sans prise en charge de commande](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)