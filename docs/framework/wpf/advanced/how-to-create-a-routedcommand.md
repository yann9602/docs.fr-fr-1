---
title: "Comment&#160;: cr&#233;er un RoutedCommand | Microsoft Docs"
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
  - "classes, RoutedCommand, créer"
  - "créer, RoutedCommand (classe)"
  - "RoutedCommand (classe), créer"
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er un RoutedCommand
Cet exemple montre comment créer une <xref:System.Windows.Input.RoutedCommand> personnalisée et l'implémenter en créant un <xref:System.Windows.Input.ExecutedRoutedEventHandler> et un <xref:System.Windows.Input.CanExecuteRoutedEventHandler> et en les joignant à une <xref:System.Windows.Input.CommandBinding>.  Pour plus d'informations sur l'exécution des commandes, consultez [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## Exemple  
 La première étape de la création d'une <xref:System.Windows.Input.RoutedCommand> consiste à définir la commande et à l'instancier.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Pour utiliser la commande dans une application, vous devez créer les gestionnaires d'événements qui définissent le rôle de cette commande.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Une <xref:System.Windows.Input.CommandBinding> associant la commande aux gestionnaires d'événements est ensuite créée.  La <xref:System.Windows.Input.CommandBinding> est créée sur un objet spécifique.  Cet objet définit la portée de la <xref:System.Windows.Input.CommandBinding> dans l'arborescence d'éléments  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 La dernière étape consiste à appeler la commande.  Pour ce faire, vous pouvez associer la commande à une <xref:System.Windows.Input.ICommandSource>, telle qu'un <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Lorsque vous cliquez sur le bouton, la méthode <xref:System.Windows.Input.RoutedCommand.Execute%2A> sur la <xref:System.Windows.Input.RoutedCommand> personnalisée est appelée.  La <xref:System.Windows.Input.RoutedCommand> déclenche les événements routés <xref:System.Windows.Input.CommandManager.PreviewExecuted> et <xref:System.Windows.Input.CommandManager.Executed>.  Ces événements parcourent l'arborescence d'éléments à la recherche d'une <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.  Si une <xref:System.Windows.Input.CommandBinding> est trouvée, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> associé à cette <xref:System.Windows.Input.CommandBinding> est appelé.  
  
## Voir aussi  
 <xref:System.Windows.Input.RoutedCommand>   
 [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)