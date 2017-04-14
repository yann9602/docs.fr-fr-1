---
title: "Comment&#160;: raccorder une commande &#224; un contr&#244;le sans prise en charge de commande | Microsoft Docs"
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
  - "classes, Contrôle, attacher un RoutedCommand"
  - "classes, RoutedCommand, attacher à un Control"
  - "Control (classe), attacher un RoutedCommand"
  - "RoutedCommand (classe), attacher à un Control"
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: raccorder une commande &#224; un contr&#244;le sans prise en charge de commande
L'exemple suivant montre comment raccorder une <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Control> qui n'offre pas de prise en charge intégrée de la commande.  Pour obtenir un exemple complet qui raccorde des commandes à plusieurs sources, consultez [Créer un RoutedCommand personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose une bibliothèque de commandes courantes que les programmeurs rencontrent régulièrement.  Les classes qui constituent la bibliothèque de commandes sont les suivantes : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands> et <xref:System.Windows.Documents.EditingCommands>.  
  
 Les objets <xref:System.Windows.Input.RoutedCommand> statiques qui composent ces classes ne fournissent pas de logique de commande.  La logique de commande est associée à la commande à l'aide d'une <xref:System.Windows.Input.CommandBinding>.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], de nombreux contrôles offrent une prise en charge intégrée pour certaines commandes de la bibliothèque de commandes.  Par exemple, <xref:System.Windows.Controls.TextBox> prend en charge de nombreuses commandes de modification de l'application, telles que <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A> et <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Le développeur d'applications ne doit rien faire de spécial pour que ces commandes fonctionnent avec ces contrôles.  Si le contrôle <xref:System.Windows.Controls.TextBox> est la cible de la commande lors de l'exécution de celle\-ci, il gérera la commande à l'aide de la <xref:System.Windows.Input.CommandBinding> qui lui est intégrée.  
  
 L'exemple suivant indique comment utiliser un <xref:System.Windows.Controls.Button> comme source de la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  Une <xref:System.Windows.Input.CommandBinding> est créée. Elle associe le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> spécifié et le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> à la <xref:System.Windows.Input.RoutedCommand>.  
  
 D'abord, la source de la commande est créée.  Un <xref:System.Windows.Controls.Button> est utilisé comme source de la commande.  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Ensuite, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> et le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont créés.  Le <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre simplement une <xref:System.Windows.MessageBox> pour indiquer que la commande s'est exécutée.  Le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> affecte à la propriété <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> la valeur `true`.  Normalement, le gestionnaire de l'événement CanExecute effectue des contrôles plus fiables pour voir si la commande peut s'exécuter sur la cible de commande actuelle.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Enfin, une <xref:System.Windows.Input.CommandBinding> est créée sur la <xref:System.Windows.Window> racine de l'application qui associe les gestionnaires d'événements routés à la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## Voir aussi  
 [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [Raccorder une commande à un contrôle avec prise en charge de commande](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)