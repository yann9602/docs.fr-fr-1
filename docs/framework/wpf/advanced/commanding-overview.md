---
title: Vue d'ensemble des commandes
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
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb7d05cdf5f6a80a0a247a5f429052cc9a8368b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="commanding-overview"></a>Vue d'ensemble des commandes
<a name="introduction"></a> L’exécution de commandes est un mécanisme d’entrée dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] qui fournit la gestion des entrées à un niveau plus sémantique que l’entrée de périphérique. Les opérations **Copier**, **Couper** et **Coller** sont des exemples de commandes figurant dans de nombreuses applications.  
  
 Cette vue d’ensemble explique ce qu’est une commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], quelles classes font partie du modèle d’exécution de commandes, et comment utiliser et créer des commandes dans vos applications.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Qu’est-ce qu’une commande ?](#commands_at_10000_feet)  
  
-   [Exemple de commande simple dans WPF](#simple_command)  
  
-   [Quatre principaux concepts de l’exécution de commandes WPF](#Four_main_Concepts)  
  
-   [Bibliothèque de commandes](#Command_Library)  
  
-   [Création de commandes personnalisées](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Qu’est-ce qu’une commande ?  
 Les commandes ont plusieurs fonctions. La première est de séparer la sémantique et l’objet qui appelle une commande de la logique qui exécute la commande. Cela permet à des sources diverses d’appeler la même logique de commande, et permet de personnaliser celle-ci pour différentes cibles. Par exemple, les opérations d’édition **Copier**, **Couper** et **Coller**, qui figurent dans de nombreuses applications, peuvent être appelées à l’aide de différentes actions utilisateur si elles sont implémentées à l’aide de commandes. Une application peut permettre à un utilisateur de couper du texte ou des objets sélectionnés en cliquant sur un bouton, en choisissant un élément dans un menu ou en utilisant une combinaison de touches telle que Ctrl+X. Grâce aux commandes, vous pouvez lier chaque type d’action de l’utilisateur à la même logique.  
  
 Une autre fonction des commandes consiste à indiquer si une action est disponible. Si vous coupez un objet ou du texte, l’action n’a de sens que si quelque chose est sélectionné. Si un utilisateur essaie de couper un objet ou du texte sans rien avoir sélectionné, rien ne se passe. Pour indiquer cela à l’utilisateur, de nombreuses applications désactivent les boutons et les éléments de menu afin que l’utilisateur sache s’il est possible ou non d’exécuter une action. Une commande peut indiquer si une action est possible en implémentant la <xref:System.Windows.Input.ICommand.CanExecute%2A> (méthode). Un bouton peut s’abonner à la <xref:System.Windows.Input.ICommand.CanExecuteChanged> événement et être désactivé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne `false` ou être activé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne `true`.  
  
 La sémantique d’une commande peut être cohérente parmi plusieurs applications et classes, mais la logique de l’action est propre à l’objet sur lequel elle est exécutée. La combinaison de touches Ctrl+X appelle la commande **Couper** dans les classes de texte, les classes d’image et les navigateurs web, mais la logique qui effectue réellement l’opération **Couper** est définie par l’application qui exécute cette opération. A <xref:System.Windows.Input.RoutedCommand> permet aux clients d’implémenter la logique. Un objet texte peut couper le texte sélectionné dans le Presse-papiers, tandis qu’un objet image peut couper l’image sélectionnée. Lorsqu’une application gère le <xref:System.Windows.Input.CommandManager.Executed> événement, il a accès à la cible de la commande et prendre les mesures appropriées en fonction du type de la cible.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Exemple de commande simple dans WPF  
 La façon la plus simple d’utiliser une commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à utiliser prédéfini <xref:System.Windows.Input.RoutedCommand> à partir d’une des classes de la bibliothèque de commandes ; utilisez un contrôle qui a une prise en charge native pour la gestion de la commande ; et utiliser un contrôle qui a une prise en charge native pour appeler une commande.  Le <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande est une des commandes prédéfinies dans la <xref:System.Windows.Input.ApplicationCommands> classe.  Le <xref:System.Windows.Controls.TextBox> contrôle a généré dans la logique permettant de gérer la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande.  Et la <xref:System.Windows.Controls.MenuItem> classe a une prise en charge native pour appeler des commandes.  
  
 L’exemple suivant montre comment configurer un <xref:System.Windows.Controls.MenuItem> afin que lorsque l’utilisateur clique dessus, il appelle la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande sur un <xref:System.Windows.Controls.TextBox>, en supposant que le <xref:System.Windows.Controls.TextBox> a le focus clavier.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Quatre principaux concepts de l’exécution de commandes WPF  
 Le modèle de commande routée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut être divisé en quatre concepts principaux : la commande, la source de commande, la cible de commande et la liaison de commande.  
  
-   La *commande* est l’action à exécuter.  
  
-   La *source de la commande* est l’objet qui appelle la commande.  
  
-   La *cible de la commande* est l’objet sur lequel la commande est exécutée.  
  
-   La *liaison de commande* est l’objet qui mappe la logique de commande à la commande.  
  
 Dans l’exemple précédent, le <xref:System.Windows.Input.ApplicationCommands.Paste%2A> est la commande, le <xref:System.Windows.Controls.MenuItem> est la source de la commande, le <xref:System.Windows.Controls.TextBox> est la cible de commande, et la liaison de commande est fournie par le <xref:System.Windows.Controls.TextBox> contrôle.  Il est important de noter qu’il n’est pas toujours le cas qui le <xref:System.Windows.Input.CommandBinding> est fournie par le contrôle qui est la classe cible de commande.  Très souvent la <xref:System.Windows.Input.CommandBinding> doit être créée par le développeur d’applications, ou le <xref:System.Windows.Input.CommandBinding> peut être associé à un ancêtre de la cible de commande.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Commandes  
 Commandes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créés en implémentant le <xref:System.Windows.Input.ICommand> interface.  <xref:System.Windows.Input.ICommand>expose deux méthodes, <xref:System.Windows.Input.ICommand.Execute%2A>, et <xref:System.Windows.Input.ICommand.CanExecute%2A>et d’un événement, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A>exécute les actions qui sont associées à la commande. <xref:System.Windows.Input.ICommand.CanExecute%2A>Détermine si la commande peut s’exécuter sur la cible de commande actuelle. <xref:System.Windows.Input.ICommand.CanExecuteChanged>est déclenché si le Gestionnaire de commandes qui centralise les opérations d’exécution de commandes détecte une modification de la source de commande qui peut invalider une commande qui a été générée, mais pas encore exécutée par la liaison de commande.  Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation de <xref:System.Windows.Input.ICommand> est la <xref:System.Windows.Input.RoutedCommand> classe et est le focus de cette vue d’ensemble.  
  
 Les principales sources d’entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont la souris, le clavier, l’encre et les commandes routées.  Les entrées plus orientés sur les appareils utilisent un <xref:System.Windows.RoutedEvent> pour notifier des objets dans une page d’application qu’un événement d’entrée s’est produit.  A <xref:System.Windows.Input.RoutedCommand> n’est pas différente.  Le <xref:System.Windows.Input.RoutedCommand.Execute%2A> et <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> méthodes d’un <xref:System.Windows.Input.RoutedCommand> ne contiennent pas la logique d’application pour la commande, mais plutôt de déclencher des événements routés ce tunnel et de propagation dans l’arborescence d’éléments jusqu'à ce qu’ils rencontrent un objet avec un <xref:System.Windows.Input.CommandBinding>.  Le <xref:System.Windows.Input.CommandBinding> contient les gestionnaires pour ces événements et les gestionnaires d’exécuter la commande.  Pour plus d’informations sur le routage d’événements dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Le <xref:System.Windows.Input.RoutedCommand.Execute%2A> méthode sur un <xref:System.Windows.Input.RoutedCommand> déclenche le <xref:System.Windows.Input.CommandManager.PreviewExecuted> et <xref:System.Windows.Input.CommandManager.Executed> sur la cible de commande.  Le <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> méthode sur un <xref:System.Windows.Input.RoutedCommand> déclenche le <xref:System.Windows.Input.CommandManager.CanExecute> et <xref:System.Windows.Input.CommandManager.PreviewCanExecute> sur la cible de commande.  Ces événements tunneling et se propage dans l’arborescence d’éléments jusqu'à ce qu’ils rencontrent un objet qui a un <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un ensemble de commandes routés courantes répartie sur plusieurs classes : <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, et <xref:System.Windows.Documents.EditingCommands>.  Ces classes contiennent uniquement de la <xref:System.Windows.Input.RoutedCommand> objets et pas la logique d’implémentation de la commande.  La logique d’implémentation incombe à l’objet sur lequel la commande est exécutée.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Sources de commande  
 Une source de commande est l’objet qui appelle la commande.  Exemples de sources de commande sont <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, et <xref:System.Windows.Input.KeyGesture>.  
  
 Sources de commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentent généralement le <xref:System.Windows.Input.ICommandSource> interface.  
  
 <xref:System.Windows.Input.ICommandSource>expose trois propriétés : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, et <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>est la commande à exécuter lorsque la source de commande est appelée.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>est l’objet sur lequel exécuter la commande.  Il est important de noter que dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> propriété sur <xref:System.Windows.Input.ICommandSource> s’applique uniquement lorsque le <xref:System.Windows.Input.ICommand> est un <xref:System.Windows.Input.RoutedCommand>.  Si le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est définie sur une <xref:System.Windows.Input.ICommandSource> et la commande correspondante n’est pas un <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée. Si le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> n’est pas défini, l’élément avec le focus clavier sera la cible de commande.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>est un type de données défini par l’utilisateur utilisé pour passer des informations aux gestionnaires d’implémentation de la commande.  
  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes qui implémentent <xref:System.Windows.Input.ICommandSource> sont <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, et <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, et <xref:System.Windows.Documents.Hyperlink> appeler une commande lorsque vous cliquiez dessus et qu’un <xref:System.Windows.Input.InputBinding> appelle une commande lorsque le <xref:System.Windows.Input.InputGesture> associé avec elle est effectuée.  
  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.MenuItem> dans un <xref:System.Windows.Controls.ContextMenu> comme source de commande pour la <xref:System.Windows.Input.ApplicationCommands.Properties%2A> commande.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 En général, une source de commande écoutera le <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> événement.  Cet événement signale à la source de commande que la capacité de la commande à s’exécuter sur la cible de commande actuelle a peut-être changé.  La source de commande peut interroger l’état actuel de la <xref:System.Windows.Input.RoutedCommand> à l’aide de la <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> (méthode).  La source de commande peut ensuite se désactiver si la commande ne peut pas s’exécuter.  Ceci est un <xref:System.Windows.Controls.MenuItem> grisé lorsqu’une commande ne peut pas s’exécuter.  
  
 Un <xref:System.Windows.Input.InputGesture> peut être utilisé comme source de commande.  Deux types de mouvements d’entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont les <xref:System.Windows.Input.KeyGesture> et <xref:System.Windows.Input.MouseGesture>.  Vous pouvez considérer un <xref:System.Windows.Input.KeyGesture> comme un raccourci clavier, tels que CTRL + C.  A <xref:System.Windows.Input.KeyGesture> est composé d’un <xref:System.Windows.Input.Key> et un ensemble de <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> est composé d’un <xref:System.Windows.Input.MouseAction> et un ensemble facultatif de <xref:System.Windows.Input.ModifierKeys>.  
  
 Dans l’ordre pour un <xref:System.Windows.Input.InputGesture> pour agir comme source de commande, il doit être associé à une commande. Il existe plusieurs façons d’accomplir cela.  Consiste à utiliser un <xref:System.Windows.Input.InputBinding>.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Input.KeyBinding> entre un <xref:System.Windows.Input.KeyGesture> et un <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Un autre moyen d’associer un <xref:System.Windows.Input.InputGesture> à un <xref:System.Windows.Input.RoutedCommand> consiste à ajouter la <xref:System.Windows.Input.InputGesture> à la <xref:System.Windows.Input.InputGestureCollection> sur la <xref:System.Windows.Input.RoutedCommand>.  
  
 L’exemple suivant montre comment ajouter un <xref:System.Windows.Input.KeyGesture> à la <xref:System.Windows.Input.InputGestureCollection> d’un <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> associe une commande avec les gestionnaires d’événements qui implémentent la commande.  
  
 Le <xref:System.Windows.Input.CommandBinding> classe contient un <xref:System.Windows.Input.CommandBinding.Command%2A> propriété, et <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, et <xref:System.Windows.Input.CommandBinding.CanExecute> événements.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>est la commande qui le <xref:System.Windows.Input.CommandBinding> est associé.  Les gestionnaires d’événements qui sont attachés à la <xref:System.Windows.Input.CommandBinding.PreviewExecuted> et <xref:System.Windows.Input.CommandBinding.Executed> événements implémentent la logique de commande.  Les gestionnaires d’événements est attaché à la <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> et <xref:System.Windows.Input.CommandBinding.CanExecute> les événements de déterminer si la commande peut s’exécuter sur la cible de commande actuelle.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Input.CommandBinding> sur la racine <xref:System.Windows.Window> d’une application.  Le <xref:System.Windows.Input.CommandBinding> associe le <xref:System.Windows.Input.ApplicationCommands.Open%2A> avec <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> gestionnaires.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Ensuite, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont créés.  Le <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre un <xref:System.Windows.MessageBox> qui affiche une chaîne indiquant que la commande a été exécutée.  Le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> définit le <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> propriété `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> est attaché à un objet spécifique, comme la racine <xref:System.Windows.Window> de l’application ou un contrôle.  L’objet qui le <xref:System.Windows.Input.CommandBinding> est attaché définit la portée de la liaison.  Par exemple, un <xref:System.Windows.Input.CommandBinding> attaché à un ancêtre de la commande cible peut être atteint par le <xref:System.Windows.Input.CommandBinding.Executed> événement, mais un <xref:System.Windows.Input.CommandBinding> attaché à un descendant de la commande cible ne peut pas être atteint.  Il s’agit d’une conséquence directe de la façon dont un <xref:System.Windows.RoutedEvent> tunnel et se propage à partir de l’objet qui déclenche l’événement.  
  
 Dans certaines situations le <xref:System.Windows.Input.CommandBinding> est attachée à la cible de la commande elle-même, comme avec la <xref:System.Windows.Controls.TextBox> classe et le <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, et <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commandes. Pourtant, il est souvent plus commode d’attacher la <xref:System.Windows.Input.CommandBinding> à un ancêtre de la cible de commande, telles que la main <xref:System.Windows.Window> ou l’objet d’Application, en particulier si le même <xref:System.Windows.Input.CommandBinding> peut être utilisé pour plusieurs cibles de commande.  Il y a des décisions de conception à prendre en compte quand vous créez votre infrastructure de commandes.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Cible de commande  
 La cible de commande est l’élément sur lequel la commande est exécutée.  D’un <xref:System.Windows.Input.RoutedCommand>, la cible de commande est l’élément au niveau duquel le routage de la <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandManager.CanExecute> démarre.  Comme indiqué précédemment, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> propriété sur <xref:System.Windows.Input.ICommandSource> s’applique uniquement lorsque le <xref:System.Windows.Input.ICommand> est un <xref:System.Windows.Input.RoutedCommand>.  Si le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est définie sur une <xref:System.Windows.Input.ICommandSource> et la commande correspondante n’est pas un <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée.  
  
 La source de commande peut définir explicitement la cible de commande.  Si la cible de commande n’est pas définie, l’élément ayant le focus clavier est utilisé comme cible de commande.  L’un des avantages liés à l’utilisation de l’élément ayant le focus clavier comme cible de commande est que cela permet au développeur de l’application d’utiliser la même source de commande pour appeler une commande sur plusieurs cibles sans avoir à effectuer le suivi de la cible de commande.  Par exemple, si un <xref:System.Windows.Controls.MenuItem> appelle la **coller** dans une application qui a un <xref:System.Windows.Controls.TextBox> contrôle et un <xref:System.Windows.Controls.PasswordBox> (contrôle), la cible peut être soit le <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.PasswordBox> selon lequel contrôle a le focus clavier.  
  
 L’exemple suivant montre comment définir explicitement la cible de commande dans le balisage et dans le code-behind.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 Le <xref:System.Windows.Input.CommandManager> numéro de commande prend en charge des fonctions associées.  Il fournit un ensemble de méthodes statiques pour l’ajout et suppression de <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, et <xref:System.Windows.Input.CommandManager.CanExecute> gestionnaires d’événements vers et à partir d’un élément spécifique.  Il fournit un moyen pour inscrire <xref:System.Windows.Input.CommandBinding> et <xref:System.Windows.Input.InputBinding> objets dans une classe spécifique.  Le <xref:System.Windows.Input.CommandManager> fournit également un moyen, via le <xref:System.Windows.Input.CommandManager.RequerySuggested> événement, afin de signaler à une commande qu’elle doit déclencher le <xref:System.Windows.Input.ICommand.CanExecuteChanged> événement.  
  
 Le <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> méthode force le <xref:System.Windows.Input.CommandManager> pour déclencher le <xref:System.Windows.Input.CommandManager.RequerySuggested> événement.  Cela est utile pour les conditions qui doivent désactiver/activer une commande mais n’est pas les conditions qui le <xref:System.Windows.Input.CommandManager> connaît.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Bibliothèque de commandes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un ensemble de commandes prédéfinies.  La bibliothèque de commandes se compose des classes suivantes : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>et le <xref:System.Windows.Input.ComponentCommands>.  Ces classes fournissent des commandes telles que <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> et <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, et <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Bon nombre de ces commandes incluent un jeu de liaisons d’entrée par défaut.  Par exemple, si vous spécifiez que votre application gère la commande de copie, vous obtenez automatiquement la liaison de clavier « Ctrl+C ». Vous obtenez également des liaisons pour d’autres périphériques d’entrée, tels que les informations de reconnaissance vocale et les mouvements de stylet [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)].  
  
 Quand vous référencez des commandes dans les différentes bibliothèques de commandes à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez généralement omettre le nom de la classe de bibliothèque qui expose la propriété de commande statique. En général, les noms des commandes ne sont pas plus ambigus que des chaînes, et les types propriétaires existent pour fournir un regroupement logique de commandes, mais ne sont pas nécessaires pour éviter les ambiguïtés. Par exemple, vous pouvez spécifier `Command="Cut"` plutôt que la version plus détaillée `Command="ApplicationCommands.Cut"`. Il s’agit d’un mécanisme pratique qui est intégré à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur pour les commandes (plus précisément, il est un comportement de convertisseur de type de <xref:System.Windows.Input.ICommand>, qui le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au moment du chargement des références de processeur).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Création de commandes personnalisées  
 Si les commandes dans les classes de la bibliothèque de commandes ne répondent pas à vos besoins, vous pouvez créer vos propres commandes.  Il existe deux façons de créer une commande personnalisée.  La première consiste à démarrer dès le départ et le mettre en œuvre la <xref:System.Windows.Input.ICommand> interface.  L’autre manière, l’approche la plus courante, consiste à créer un <xref:System.Windows.Input.RoutedCommand> ou <xref:System.Windows.Input.RoutedUICommand>.  
  
 Pour obtenir un exemple de création d’un fichier <xref:System.Windows.Input.RoutedCommand>, consultez [créer un exemple de propriété RoutedCommand personnalisé](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Vue d’ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Implémenter ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Guide pratique pour ajouter une commande à un MenuItem](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [Créer un exemple RoutedCommand personnalisé](http://go.microsoft.com/fwlink/?LinkID=159980)
