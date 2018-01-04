---
title: "Comment : implémenter ICommandSource"
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
helpviewer_keywords: ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d82a211f59fbdecdc932b7e57b242274e91cd5b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-icommandsource"></a>Comment : implémenter ICommandSource
Cet exemple montre comment créer une source de commande en implémentant <xref:System.Windows.Input.ICommandSource>.  Une source de commande est un objet qui sait comment appeler une commande.  Le <xref:System.Windows.Input.ICommandSource> interface expose trois membres : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, et <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A>est la commande qui sera invoquée. Le <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> est un type de données défini par l’utilisateur qui est passé à partir de la source de commande à la méthode qui gère la commande. Le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est l’objet qui est en cours d’exécution sur la commande.  
  
 Dans cet exemple, une classe est créée qui sous-classe le <xref:System.Windows.Controls.Slider> contrôle et met en œuvre <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un certain nombre de classes qui implémentent <xref:System.Windows.Input.ICommandSource>, tel que <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, et <xref:System.Windows.Controls.ListBoxItem>.  Une source de commande définit comment appeler une commande.   <xref:System.Windows.Controls.Button>et <xref:System.Windows.Controls.MenuItem> appeler une commande lorsque vous cliquiez dessus.  A <xref:System.Windows.Controls.ListBoxItem> appelle une commande lorsque le double-clic sur. Ces classes ne deviennent une commande source quand leur <xref:System.Windows.Input.ICommandSource.Command%2A> est définie.  
  
 Pour cet exemple, nous appellerons la commande lorsque le curseur est déplacé, ou plus précisément, lorsque le <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété est modifiée.  
  
 Voici la définition de classe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 L’étape suivante consiste à implémenter le <xref:System.Windows.Input.ICommandSource> membres.  Dans cet exemple, les propriétés sont implémentées en tant que <xref:System.Windows.DependencyProperty> objets.  Ainsi, les propriétés à utiliser la liaison de données.  Pour plus d’informations sur la <xref:System.Windows.DependencyProperty> de classe, consultez la [vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour plus d’informations sur la liaison de données, consultez la [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Uniquement les <xref:System.Windows.Input.ICommandSource.Command%2A> propriété est illustrée ici.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Voici le <xref:System.Windows.DependencyProperty> modifier le rappel.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 L’étape suivante consiste à ajouter et supprimer la commande qui est associée à la source de commande.  Le <xref:System.Windows.Input.ICommandSource.Command%2A> propriété ne peut pas être remplacée simplement une nouvelle commande est ajoutée, car les gestionnaires d’événements associés à la commande précédente, doivent être supprimés en premier.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 La dernière étape consiste à créer la logique pour le <xref:System.Windows.Input.ICommand.CanExecuteChanged> gestionnaire et <xref:System.Windows.Input.ICommand.Execute%2A> (méthode).  
  
 Le <xref:System.Windows.Input.ICommand.CanExecuteChanged> événements informe la source de commande que la capacité de la commande à exécuter sur la cible de commande actuelle a peut-être changé.  Lorsqu’une source de commande reçoit cet événement, elle appelle généralement la <xref:System.Windows.Input.ICommand.CanExecute%2A> méthode sur la commande.  Si la commande ne peut pas s’exécuter sur la cible de commande actuelle, la source de commande est généralement désactivée.  Si la commande peut s’exécuter sur la cible de commande actuelle, la source de commande activera généralement lui-même.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 La dernière étape est la <xref:System.Windows.Input.ICommand.Execute%2A> (méthode).  Si la commande est un <xref:System.Windows.Input.RoutedCommand>, le <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> méthode est appelée ; sinon, le <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> méthode est appelée.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [Vue d’ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)
