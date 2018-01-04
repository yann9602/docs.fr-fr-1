---
title: "Comment : activer une commande"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27f8544a44a252eb1a1afd6e096f303360c14e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-command"></a>Comment : activer une commande
L’exemple suivant montre comment utiliser l’exécution de commandes dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  L’exemple montre comment associer un <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Button>, créez un <xref:System.Windows.Input.CommandBinding>et créer les gestionnaires d’événements qui implémentent la <xref:System.Windows.Input.RoutedCommand>.  Pour plus d’informations sur l’exécution des commandes, consultez le [vue d’ensemble de l’exécution des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Exemple  
 La première section de code crée la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], qui se compose d’un <xref:System.Windows.Controls.Button> et un <xref:System.Windows.Controls.StackPanel>et crée un <xref:System.Windows.Input.CommandBinding> qui associe les gestionnaires de commandes avec la <xref:System.Windows.Input.RoutedCommand>.  
  
 Le <xref:System.Windows.Input.ICommandSource.Command%2A> propriété de la <xref:System.Windows.Controls.Button> est associé le <xref:System.Windows.Input.ApplicationCommands.Close%2A> commande.  
  
 Le <xref:System.Windows.Input.CommandBinding> est ajouté à la <xref:System.Windows.Input.CommandBindingCollection> de la racine de <xref:System.Windows.Window>. Le <xref:System.Windows.Input.CommandBinding.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> gestionnaires d’événements sont attachés à cette liaison et associés à la <xref:System.Windows.Input.ApplicationCommands.Close%2A> commande.  
  
 Sans le <xref:System.Windows.Input.CommandBinding> il n’existe aucune commande logique, uniquement un mécanisme pour appeler la commande.  Lorsque le <xref:System.Windows.Controls.Button> est activé, le <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> est déclenché sur la cible de commande suivie par le <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Ces événements parcourent l’arborescence d’éléments recherchant un <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.  Il est important de noter que, car <xref:System.Windows.RoutedEvent> tunnel et se propagent dans l’arborescence d’éléments, soyez prudent en où le <xref:System.Windows.Input.CommandBinding> est placé.   Si le <xref:System.Windows.Input.CommandBinding> se trouve sur un frère de la cible de commande ou un autre nœud qui n’est pas sur l’itinéraire de le <xref:System.Windows.RoutedEvent>, le <xref:System.Windows.Input.CommandBinding> n’est pas accessible.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 La section suivante du code implémente le <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> gestionnaires d’événements.  
  
 Le <xref:System.Windows.Input.CommandManager.Executed> gestionnaire appelle une méthode pour fermer le fichier ouvert.  Le <xref:System.Windows.Input.CommandBinding.CanExecute> appelle une méthode pour déterminer si un fichier est ouvert.  Si un fichier est ouvert, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> a la valeur `true`; sinon, elle est définie sur `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)
