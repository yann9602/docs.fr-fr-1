---
title: "Comment&#160;: activer une commande | Microsoft Docs"
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
  - "CommandBindings"
  - "exécution de commandes"
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: activer une commande
L'exemple suivant indique comment utiliser l'exécution de commandes dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  L'exemple montre comment associer une <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Button>, créer une <xref:System.Windows.Input.CommandBinding> et créer les gestionnaires d'événements qui implémentent la <xref:System.Windows.Input.RoutedCommand>.  Pour plus d'informations sur l'exécution des commandes, consultez [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## Exemple  
 La première section du code crée l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], qui se compose d'un <xref:System.Windows.Controls.Button> et d'un <xref:System.Windows.Controls.StackPanel>, et crée une <xref:System.Windows.Input.CommandBinding> qui associe les gestionnaires de commandes à la <xref:System.Windows.Input.RoutedCommand>.  
  
 La propriété <xref:System.Windows.Input.ICommandSource.Command%2A> du <xref:System.Windows.Controls.Button> est associée à la commande <xref:System.Windows.Input.ApplicationCommands.Close%2A>.  
  
 La <xref:System.Windows.Input.CommandBinding> est ajoutée à la <xref:System.Windows.Input.CommandBindingCollection> de la <xref:System.Windows.Window> racine.  Les gestionnaires d'événements <xref:System.Windows.Input.CommandBinding.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> sont attachés à cette liaison et associés à la commande <xref:System.Windows.Input.ApplicationCommands.Close%2A>.  
  
 Sans la <xref:System.Windows.Input.CommandBinding>, il n'y a aucune commande logique, uniquement un mécanisme pour appeler la commande.  Lorsque l'utilisateur clique sur le <xref:System.Windows.Controls.Button>, l'<xref:System.Windows.RoutedEvent> <xref:System.Windows.Input.CommandManager.PreviewExecuted> est déclenché sur la cible de la commande suivie par l'<xref:System.Windows.RoutedEvent> <xref:System.Windows.Input.CommandManager.Executed>.  Ces événements parcourent l'arborescence d'éléments à la recherche d'une <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.  Il convient de noter que comme l'<xref:System.Windows.RoutedEvent> effectue un tunneling et se propage à travers l'arborescence d'éléments, vous devez prêter une attention particulière à l'endroit où la <xref:System.Windows.Input.CommandBinding> est placée.  Si la <xref:System.Windows.Input.CommandBinding> se trouve sur un frère de la cible de commande ou un autre nœud qui n'est pas sur l'itinéraire du <xref:System.Windows.RoutedEvent>, la <xref:System.Windows.Input.CommandBinding> sera inaccessible.  
  
 [!code-xml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 La section suivante du code implémente les gestionnaires d'événements <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 Le gestionnaire <xref:System.Windows.Input.CommandManager.Executed> appelle une méthode pour fermer le fichier ouvert.  Le gestionnaire <xref:System.Windows.Input.CommandBinding.CanExecute> appelle une méthode pour déterminer si un fichier est ouvert.  Si un fichier est ouvert, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> a la valeur `true` ; sinon, il a la valeur `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## Voir aussi  
 [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)