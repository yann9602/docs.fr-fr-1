---
title: "Comment : raccorder une commande à un contrôle sans prise en charge de commande"
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
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 804c4ffd54a0f8cc94e8849a223b1af8b27a58b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Comment : raccorder une commande à un contrôle sans prise en charge de commande
L’exemple suivant montre comment raccorder un <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Control> qui n’ont pas intégrée prise en charge de la commande.  Pour obtenir un exemple complet qui raccorde des commandes à plusieurs sources, consultez l’exemple [Créer un exemple RoutedCommand personnalisé](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une bibliothèque de commandes courantes que les programmeurs d’applications rencontrent régulièrement.  Les classes qui constituent la bibliothèque de commandes sont : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, et <xref:System.Windows.Documents.EditingCommands>.  
  
 La méthode statique <xref:System.Windows.Input.RoutedCommand> les objets qui composent ces classes ne fournissent pas la logique de commande.  La logique de la commande est associée à la commande avec un <xref:System.Windows.Input.CommandBinding>.  Dans de nombreux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont en charge intégrée pour certaines commandes dans la bibliothèque de commandes.  <xref:System.Windows.Controls.TextBox>, par exemple, prend en charge la plupart des commandes de modification d’application telles que <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, et <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Le développeur d’application n’a aucune action spéciale à effectuer pour que ces commandes fonctionnent avec ces contrôles.  Si le <xref:System.Windows.Controls.TextBox> est la cible de commande lorsque la commande est exécutée, elle gère la commande à l’aide de la <xref:System.Windows.Input.CommandBinding> qui est intégré au contrôle.  
  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.Button> comme source de commande pour la <xref:System.Windows.Input.ApplicationCommands.Open%2A> commande.  A <xref:System.Windows.Input.CommandBinding> est créé qui associe spécifié <xref:System.Windows.Input.CanExecuteRoutedEventHandler> et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> avec la <xref:System.Windows.Input.RoutedCommand>.  
  
 Tout d’abord, la source de commande est créée.  A <xref:System.Windows.Controls.Button> est utilisé comme source de la commande.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Ensuite, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont créés.  Le <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre simplement une <xref:System.Windows.MessageBox> pour indiquer que la commande exécutée.  Le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> définit le <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> propriété `true`.  Normalement, le peut exécuter gestionnaire effectue des vérifications plus robustes pour voir si la commande peut s’exécuter sur la cible de commande actuelle.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Enfin, un <xref:System.Windows.Input.CommandBinding> est créé sur la racine <xref:System.Windows.Window> de l’application qui associe les gestionnaires d’événements routés vers le <xref:System.Windows.Input.ApplicationCommands.Open%2A> commande.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Raccorder une commande à un contrôle avec prise en charge de commande](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
