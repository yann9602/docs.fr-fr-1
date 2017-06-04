---
title: "Vue d&#39;ensemble des commandes | Microsoft Docs"
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
  - "classes, CommandBinding"
  - "bibliothèque de commandes"
  - "CommandBindings"
  - "exécution de commandes"
  - "CommandManager"
  - "commandes, définition de"
  - "interfaces ICommandSource"
  - "interfaces, ICommandSource"
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# Vue d&#39;ensemble des commandes
<a name="introduction"></a> L'exécution des commandes est un mécanisme d'entrée dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] qui permet de gérer les entrées à un niveau plus sémantique que l'entrée de périphérique.  Les opérations **Copier**, **Couper**et **Coller** sont des exemples de commandes présentes dans de nombreuses applications.  
  
 Cette vue d'ensemble définit les commandes présentes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], indique quelles classes font partie du modèle d'exécution de commande et comment utiliser et créer des commandes dans vos applications.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Qu'est\-ce qu'une commande ?](#commands_at_10000_feet)  
  
-   [Exemple de commande simple dans WPF](#simple_command)  
  
-   [Quatre principaux concepts de l'exécution de commande dans WPF](#Four_main_Concepts)  
  
-   [Bibliothèque de commandes](#Command_Library)  
  
-   [Création de commandes personnalisées](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## Qu'est\-ce qu'une commande ?  
 Les commandes ont plusieurs utilisations.  La première est de séparer la sémantique et l'objet qui appelle une commande de la logique qui exécute la commande.  Cela permet à des diverses sources d'appeler la même logique de commande et de personnaliser la logique de commande par rapport à différentes cibles.  Par exemple, les opérations d'édition **Copier**, **Couper** et **Coller**, que l'on trouve dans de nombreuses applications, peuvent être appelées à l'aide d'actions utilisateur différentes, si elles sont implémentés à l'aide de commandes.  Une application peut permettre à un utilisateur de couper des objets ou du texte en cliquant sur un bouton, en choisissant un élément d'un menu ou à l'aide d'une combinaison de touches, telle que CTRL\+X.  En utilisant des commandes, vous pouvez lier chaque type d'action utilisateur à la même logique.  
  
 Une autre utilisation des commandes est d'indiquer si une action est disponible.  Pour revenir à l'exemple de couper un objet ou du texte, cette action ne présente d'intérêt que si un élément est sélectionné.  Si un utilisateur essaie de couper un objet ou du texte sans avoir rien sélectionné, rien ne se passe.  Pour l'indiquer à l'utilisateur, de nombreuses applications désactivent des boutons et des éléments de menu pour que l'utilisateur sache qu'il n'est pas possible d'exécuter cette action.  Une commande peut indiquer si une action est possible en implémentant la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A>.  Un bouton peut s'inscrire à l'événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> et être désactivé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne la valeur `false` ou être activé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne la valeur `true`.  
  
 La sémantique d'une commande peut être cohérente dans les applications et les classes, mais la logique de l'action est propre à l'objet concerné par l'action.  La combinaison de touches CTRL\+X appelle la commande **Couper** dans les classes de texte, les classes d'image et les navigateurs Web, mais la logique réelle de l'opération **Couper** est définie par l'application qui exécute cette opération.  Un <xref:System.Windows.Input.RoutedCommand> permet aux clients d'implémenter la logique.  Un objet de texte peut couper le texte sélectionné dans le presse\-papiers et un objet d'image peut couper l'image sélectionnée.  Lorsqu'une application gère l'événement <xref:System.Windows.Input.CommandManager.Executed>, elle a accès à la cible de la commande et peut entreprendre l'action appropriée en fonction du type de la cible.  
  
<a name="simple_command"></a>   
## Exemple de commande simple dans WPF  
 La manière la plus simple d'utiliser une commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à utiliser une <xref:System.Windows.Input.RoutedCommand> prédéfinie de l'une des classes de la bibliothèque de commandes, utiliser un contrôle doté d'une prise en charge native pour gérer la commande et utiliser un contrôle doté d'une prise en charge native pour appeler une commande.  La commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A> est l'une des commandes prédéfinies de la classe <xref:System.Windows.Input.ApplicationCommands>.  Le contrôle <xref:System.Windows.Controls.TextBox> est doté d'une logique intégrée pour gérer la commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  Et la classe <xref:System.Windows.Controls.MenuItem> possède une prise en charge native pour appeler des commandes.  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.MenuItem> pour que, lorsque l'utilisateur clique dessus, il appelle la commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A> dans une <xref:System.Windows.Controls.TextBox>, si la <xref:System.Windows.Controls.TextBox> a le focus clavier.  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## Quatre principaux concepts de l'exécution de commande dans WPF  
 Le modèle de commande routée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut être subdivisé en quatre concepts principaux : la commande, la source de la commande, la cible de la commande et la liaison de commande.  
  
-   La *commande* est l'action à exécuter.  
  
-   La *source de la commande* est l'objet qui appelle la commande.  
  
-   La *cible de la commande* est l'objet sur lequel la commande est exécutée.  
  
-   La *liaison de commande* \(command binding\) est l'objet qui mappe la logique de commande à la commande.  
  
 Dans l'exemple précédent, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> est la commande, <xref:System.Windows.Controls.MenuItem> est la source de la commande, <xref:System.Windows.Controls.TextBox> est la cible de la commande, et la liaison de commande est fournie par le contrôle <xref:System.Windows.Controls.TextBox>.  Il convient de noter que la <xref:System.Windows.Input.CommandBinding> n'est pas toujours fournie par le contrôle qui correspond à la classe de cible de commande.  Souvent, la <xref:System.Windows.Input.CommandBinding> doit être créée par le développeur d'applications ou la <xref:System.Windows.Input.CommandBinding> peut être jointe à un ancêtre de la cible de la commande.  
  
<a name="Commands"></a>   
### Commandes  
 Les commandes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées en implémentant l'interface <xref:System.Windows.Input.ICommand>.  <xref:System.Windows.Input.ICommand> expose deux méthodes :<xref:System.Windows.Input.ICommand.Execute%2A> et <xref:System.Windows.Input.ICommand.CanExecute%2A>, et l'événement <xref:System.Windows.Input.ICommand.CanExecuteChanged>.  <xref:System.Windows.Input.ICommand.Execute%2A> effectue les actions associées à la commande. <xref:System.Windows.Input.ICommand.CanExecute%2A> détermine si la commande peut s'exécuter sur la cible de la commande actuelle.  <xref:System.Windows.Input.ICommand.CanExecuteChanged> se déclenche lorsque le gestionnaire de commandes qui centralise les opérations d'exécution de commandes détecte une modification dans la source de la commande qui peut invalider une commande déclenchée mais pas encore exécutée par la liaison de commande.  L'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de <xref:System.Windows.Input.ICommand> est la classe <xref:System.Windows.Input.RoutedCommand> et est le focus de cette vue d'ensemble.  
  
 Les principales sources d'entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont la souris, le clavier, l'encre et les commandes routées.  La plupart des entrées orientées périphérique utilisent un <xref:System.Windows.RoutedEvent> pour signaler aux objets d'une page d'application qu'un événement d'entrée s'est produit.  Une <xref:System.Windows.Input.RoutedCommand> fonctionne de la même manière.  Les méthodes <xref:System.Windows.Input.RoutedCommand.Execute%2A> et <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> d'une <xref:System.Windows.Input.RoutedCommand> ne contiennent pas la logique d'application pour la commande, mais elles déclenchent des événements routés qui se chargent du tunneling et de la propagation dans l'arborescence d'éléments jusqu'à ce qu'ils rencontrent un objet avec <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> contient les gestionnaires pour ces événements et ce sont ces gestionnaires qui effectuent la commande.  Pour plus d'informations sur le routage d'événements dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 La méthode <xref:System.Windows.Input.RoutedCommand.Execute%2A> sur une <xref:System.Windows.Input.RoutedCommand> déclenche les événements <xref:System.Windows.Input.CommandManager.PreviewExecuted> et <xref:System.Windows.Input.CommandManager.Executed> sur la cible de la commande.  La méthode <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> sur une <xref:System.Windows.Input.RoutedCommand> déclenche les événements <xref:System.Windows.Input.CommandManager.CanExecute> et <xref:System.Windows.Input.CommandManager.PreviewCanExecute> sur la cible de la commande.  Ces événements créent un tunnel et se propagent dans l'arborescence d'éléments jusqu'à ce qu'ils rencontrent un objet qui a une <xref:System.Windows.Input.CommandBinding> pour cette commande.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un jeu de commandes routées communes réparties sur plusieurs classes : <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands> et <xref:System.Windows.Documents.EditingCommands>.  Ces classes contiennent uniquement des objets <xref:System.Windows.Input.RoutedCommand> et pas la logique d'implémentation de la commande.  La logique d'implémentation est la responsabilité de l'objet sur lequel la commande est exécutée.  
  
<a name="Command_Sources"></a>   
### Sources de la commande  
 Une source de commande correspond à l'objet qui appelle la commande.  <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button> et <xref:System.Windows.Input.KeyGesture> sont des exemples de sources de commande.  
  
 Les sources de commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentent généralement l'interface <xref:System.Windows.Input.ICommandSource>.  
  
 <xref:System.Windows.Input.ICommandSource> expose trois propriétés : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> et <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> :  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> est la commande à exécuter lorsque la source de la commande est appelée.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est l'objet sur lequel la commande s'exécute.  Il convient de noter que dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la propriété <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> sur <xref:System.Windows.Input.ICommandSource> s'applique uniquement lorsque <xref:System.Windows.Input.ICommand> est une <xref:System.Windows.Input.RoutedCommand>.  Si <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> a la valeur <xref:System.Windows.Input.ICommandSource> et que la commande correspondante n'est pas une <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée.  Si la <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> n'est pas définie, l'élément avec le focus clavier devient la cible de la commande.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> est un type de données défini par l'utilisateur utilisé pour passer des informations aux gestionnaires qui implémentent la commande.  
  
 Les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui implémentent <xref:System.Windows.Input.ICommandSource> sont <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink> et <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> et <xref:System.Windows.Documents.Hyperlink> appellent une commande lorsque l'utilisateur clique dessus, et <xref:System.Windows.Input.InputBinding> appelle une commande lorsque le <xref:System.Windows.Input.InputGesture> qui lui est associé est exécuté.  
  
 L'exemple suivant indique comment utiliser un <xref:System.Windows.Controls.MenuItem> dans un <xref:System.Windows.Controls.ContextMenu> comme source de la commande <xref:System.Windows.Input.ApplicationCommands.Properties%2A>.  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 En général, une source de commande écoutera l'événement <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>.  Cet événement informe la source de la commande que la capacité de la commande à s'exécuter sur la cible de commande actuelle a peut\-être changé.  La source de la commande peut interroger l'état actuel de la <xref:System.Windows.Input.RoutedCommand> en utilisant la méthode <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>.  La source de la commande peut ensuite se désactiver si la commande ne peut pas s'exécuter.  Par exemple, un <xref:System.Windows.Controls.MenuItem> devient grisé lorsqu'une commande ne peut pas s'exécuter.  
  
 Un <xref:System.Windows.Input.InputGesture> peut être utilisé comme source de commande.  Deux types de mouvements d'entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont : <xref:System.Windows.Input.KeyGesture> et <xref:System.Windows.Input.MouseGesture>.  Un <xref:System.Windows.Input.KeyGesture> peut correspondre à un raccourci clavier \(CTRL\+C, par exemple\).  Un <xref:System.Windows.Input.KeyGesture> comprend une <xref:System.Windows.Input.Key> et un ensemble de <xref:System.Windows.Input.ModifierKeys>.  Un <xref:System.Windows.Input.MouseGesture> comprend une <xref:System.Windows.Input.MouseAction> et un ensemble facultatif de <xref:System.Windows.Input.ModifierKeys>.  
  
 Pour qu'un <xref:System.Windows.Input.InputGesture> agisse comme source de commande, il doit être associé à une commande.  Il existe plusieurs façons d'accomplir cette tâche.  Vous pouvez utiliser une <xref:System.Windows.Input.InputBinding>.  
  
 L'exemple suivant indique comment créer une <xref:System.Windows.Input.KeyBinding> entre un <xref:System.Windows.Input.KeyGesture> et une <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Pour associer un <xref:System.Windows.Input.InputGesture> à une <xref:System.Windows.Input.RoutedCommand>, vous pouvez également ajouter le <xref:System.Windows.Input.InputGesture> à la <xref:System.Windows.Input.InputGestureCollection> de la <xref:System.Windows.Input.RoutedCommand>.  
  
 L'exemple suivant indique comment ajouter un <xref:System.Windows.Input.KeyGesture> à la <xref:System.Windows.Input.InputGestureCollection> d'une <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### CommandBinding  
 Une <xref:System.Windows.Input.CommandBinding> associe une commande aux gestionnaires d'événements qui implémentent la commande.  
  
 La classe <xref:System.Windows.Input.CommandBinding> contient une propriété <xref:System.Windows.Input.CommandBinding.Command%2A>, et des événements <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> et <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> est la commande à laquelle la <xref:System.Windows.Input.CommandBinding> est associée.  Les gestionnaires d'événements attachés aux événements <xref:System.Windows.Input.CommandBinding.PreviewExecuted> et <xref:System.Windows.Input.CommandBinding.Executed> implémentent la logique de commande.  Les gestionnaires d'événements attachés aux événements <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> et <xref:System.Windows.Input.CommandBinding.CanExecute> déterminent si la commande peut s'exécuter sur la cible de commande actuelle.  
  
 L'exemple suivant indique comment créer une <xref:System.Windows.Input.CommandBinding> à la racine <xref:System.Windows.Window> d'une application.  <xref:System.Windows.Input.CommandBinding> associe la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A> aux gestionnaires <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 [!code-xml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Ensuite, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> et un <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont créés.  Le <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre un <xref:System.Windows.MessageBox> qui affiche une chaîne indiquant que la commande a été exécutée.  Le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> affecte à la propriété <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> la valeur `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 Une <xref:System.Windows.Input.CommandBinding> est attachée à un objet spécifique, tel que la <xref:System.Windows.Window> racine de l'application ou un contrôle.  L'objet auquel le <xref:System.Windows.Input.CommandBinding> est attaché définit la portée de la liaison.  Par exemple, une <xref:System.Windows.Input.CommandBinding> attachée à un ancêtre de la cible de la commande peut être atteinte par l'événement <xref:System.Windows.Input.CommandBinding.Executed>, mais une <xref:System.Windows.Input.CommandBinding> attachée à un descendant de la cible de commande ne peut pas être atteinte.  Il s'agit d'une conséquence directe de la manière dont un <xref:System.Windows.RoutedEvent> crée un tunnel et se propage à partir de l'objet qui déclenche l'événement.  
  
 Dans certaines situations, la <xref:System.Windows.Input.CommandBinding> est attachée à la cible de la commande elle\-même, comme avec la classe <xref:System.Windows.Controls.TextBox> et les commandes <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A> et <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  Pourtant, il est souvent plus commode d'attacher la <xref:System.Windows.Input.CommandBinding> à un ancêtre de la cible de commande, comme la <xref:System.Windows.Window> principale ou l'objet application, surtout si une même <xref:System.Windows.Input.CommandBinding> peut être utilisée pour plusieurs cibles de commande.  Il s'agit là de décisions de conception que vous souhaiterez examiner lors de la création de votre infrastructure d'exécution de commande.  
  
<a name="Commane_Target"></a>   
### Cible de la commande  
 La cible de la commande est l'élément sur lequel la commande est exécutée.  Dans le cas d'une <xref:System.Windows.Input.RoutedCommand>, la cible de la commande est l'élément à partir duquel le routage de <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandManager.CanExecute> démarre.  Comme indiqué précédemment, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la propriété <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> de <xref:System.Windows.Input.ICommandSource> s'applique uniquement lorsque <xref:System.Windows.Input.ICommand> est une <xref:System.Windows.Input.RoutedCommand>.  Si <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> a la valeur <xref:System.Windows.Input.ICommandSource> et que la commande correspondante n'est pas une <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée.  
  
 La source de la commande peut explicitement définir la cible de la commande.  Si la cible de la commande n'est pas définie, l'élément avec le focus clavier sera utilisé comme cible de commande.  L'utilisation de l'élément avec le focus clavier comme cible de commande présente notamment l'avantage de permettre au développeur d'applications d'utiliser la même source de commande pour appeler une commande sur plusieurs cibles sans devoir suivre la cible de la commande.  Par exemple, si un <xref:System.Windows.Controls.MenuItem> appelle la commande **Coller** dans une application dotée d'un contrôle <xref:System.Windows.Controls.TextBox> et d'un contrôle <xref:System.Windows.Controls.PasswordBox>, la cible peut être <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.PasswordBox> selon le contrôle qui a le focus clavier.  
  
 L'exemple suivant indique comment définir explicitement la cible de la commande dans la balise et le code sous\-jacents.  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### CommandManager  
 <xref:System.Windows.Input.CommandManager> prend en charge plusieurs fonctions liées à des commandes.  Il fournit un jeu de méthodes statiques pour l'ajout et la suppression de gestionnaires d'événements <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute> et <xref:System.Windows.Input.CommandManager.CanExecute> dans un élément spécifique.  Il permet également d'enregistrer des objets <xref:System.Windows.Input.CommandBinding> et <xref:System.Windows.Input.InputBinding> dans une classe spécifique.  Le <xref:System.Windows.Input.CommandManager> permet en outre, grâce à l'événement <xref:System.Windows.Input.CommandManager.RequerySuggested>, de signaler à une commande qu'elle doit déclencher l'événement <xref:System.Windows.Input.ICommand.CanExecuteChanged>.  
  
 La méthode <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> force <xref:System.Windows.Input.CommandManager> à déclencher l'événement <xref:System.Windows.Input.CommandManager.RequerySuggested>.  Cela peut s'avérer utile pour les conditions qui doivent désactiver\/activer une commande mais qui ne sont pas reconnues par <xref:System.Windows.Input.CommandManager>.  
  
<a name="Command_Library"></a>   
## Bibliothèque de commandes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un jeu de commandes prédéfinies.  La bibliothèque de commandes se compose des classes suivantes : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands> et <xref:System.Windows.Input.ComponentCommands>.  Ces classes fournissent des commandes telles que <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> et <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A> et <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Nombre de ces commandes incluent un jeu de liaisons d'entrée par défaut.  Par exemple, si vous spécifiez que votre application gère la commande de copie, vous obtenez automatiquement la configuration de clavier « CTRL\+C ». Vous obtenez également des liaisons pour d'autres périphériques d'entrée, comme des mouvements de stylet [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] et des informations vocales.  
  
 Lorsque vous référencez des commandes dans les différentes bibliothèques de commandes à l'aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez habituellement omettre le nom de la classe de bibliothèque qui expose la propriété de commande statique.  En général, les noms de commande sont non équivoques comme chaînes, et les types propriétaires permettent de fournir un regroupement logique de commandes mais ne sont pas nécessaires pour éviter les ambiguïtés.  Par exemple, vous pouvez spécifier `Command="Cut"` plutôt que `Command="ApplicationCommands.Cut"`, plus prolixe.  Ce mécanisme pratique est intégré au processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour les commandes \(il s'agit plus précisément d'un comportement de convertisseur de type de <xref:System.Windows.Input.ICommand>, que le processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] référence au moment du chargement\).  
  
<a name="creating_commands"></a>   
## Création de commandes personnalisées  
 Si les commandes des classes de la bibliothèque de commandes ne répondent pas à vos besoins, vous pouvez créer vos propres commandes.  Vous pouvez créer des commandes personnalisées de deux manières différentes.  La première consiste à partir de zéro et à implémenter l'interface <xref:System.Windows.Input.ICommand>.  L'autre manière \(la plus fréquente\) consiste à créer une <xref:System.Windows.Input.RoutedCommand> ou une <xref:System.Windows.Input.RoutedUICommand>.  
  
 Pour obtenir un exemple de la création d'un <xref:System.Windows.Input.RoutedCommand> personnalisé, consultez [Créer un RoutedCommand personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159980)  
  
## Voir aussi  
 <xref:System.Windows.Input.RoutedCommand>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Input.InputBinding>   
 <xref:System.Windows.Input.CommandManager>   
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Implémenter ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)   
 [How to: Add a Command to a MenuItem](http://msdn.microsoft.com/fr-fr/013d68a0-5373-4a68-bd91-5de574307370)   
 [Créer un RoutedCommand personnalisé, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159980)