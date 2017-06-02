---
title: "Comment&#160;: impl&#233;menter ICommandSource | Microsoft Docs"
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
  - "interfaces ICommandSource, implémenter"
  - "interfaces, ICommandSource, implémenter"
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: impl&#233;menter ICommandSource
Cet exemple indique comment créer une source de commande en implémentant <xref:System.Windows.Input.ICommandSource>.  Une source de commande est un objet qui sait comment appeler une commande.  L'interface <xref:System.Windows.Input.ICommandSource> expose trois membres : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> et <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> est la commande qui sera invoquée.  <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> est un type de données défini par l'utilisateur qui est transmis de la source de commande à la méthode qui gère la commande.  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est l'objet sur lequel est exécutée la commande.  
  
 Dans cet exemple, une classe qui sous\-classe le contrôle <xref:System.Windows.Controls.Slider> et implémente <xref:System.Windows.Input.ICommandSource> est créée.  
  
## Exemple  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs classes qui implémentent <xref:System.Windows.Input.ICommandSource>, comme <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem> et <xref:System.Windows.Controls.ListBoxItem>.  Une source de commande définit comment appeler une commande.  <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.MenuItem> invoquent une commande lorsque vous cliquez dessus.  <xref:System.Windows.Controls.ListBoxItem> appelle une commande lorsque l'utilisateur double\-clique dessus.  Ces classes ne deviennent une source de commande que lorsque leur propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est définie.  
  
 Dans cet exemple, nous appellerons la commande lorsque le curseur sera déplacé, ou plus précisément lorsque la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> sera modifiée.  
  
 Les éléments suivants composent la définition de classe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 L'étape suivante consiste à implémenter les membres <xref:System.Windows.Input.ICommandSource>.  Dans cet exemple, les propriétés sont implémentées en tant qu'objets <xref:System.Windows.DependencyProperty>.  Cela permet aux propriétés d'utiliser la liaison de données.  Pour plus d'informations sur la classe <xref:System.Windows.DependencyProperty>, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour plus d'informations sur la liaison de données, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Seule la propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est illustrée ici.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Les éléments suivants représentent le rappel de changement <xref:System.Windows.DependencyProperty>.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 L'étape suivante consiste à ajouter et supprimer la commande associée à la source de commande.  La propriété <xref:System.Windows.Input.ICommandSource.Command%2A> ne peut pas être remplacée simplement à l'ajout d'une nouvelle commande car les gestionnaires d'événements éventuellement associés à la commande précédente doivent être supprimés en premier.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 La dernière étape consiste à créer la logique du gestionnaire <xref:System.Windows.Input.ICommand.CanExecuteChanged> et la méthode <xref:System.Windows.Input.ICommand.Execute%2A>.  
  
 L'événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> informe la source de commande que la possibilité d'exécuter la commande sur la cible de commande actuelle a peut\-être changé.  Lorsqu'une source de commande reçoit cet événement, elle appelle généralement la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A> sur la commande.  Si la commande ne peut pas s'exécuter sur la cible de la commande actuelle, la source de commande se désactivera d'elle\-même en règle générale.  Si la commande peut s'exécuter sur la cible, la source de commande s'activera d'elle\-même en règle générale.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 La dernière étape consiste en la méthode <xref:System.Windows.Input.ICommand.Execute%2A>.  Si la commande est un <xref:System.Windows.Input.RoutedCommand>, la méthode <xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand.Execute%2A> est appelée ; sinon, la méthode <xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A> est appelée.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## Voir aussi  
 <xref:System.Windows.Input.ICommandSource>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.Input.RoutedCommand>   
 [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)