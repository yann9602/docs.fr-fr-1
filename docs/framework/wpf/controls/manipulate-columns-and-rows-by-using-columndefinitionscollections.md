---
title: "Comment : manipuler des colonnes et des lignes à l'aide de ColumnDefinitionsCollections et RowDefinitionsCollections"
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
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e87c5001a676bcda331d289c286cf6b3e87c136f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Comment : manipuler des colonnes et des lignes à l'aide de ColumnDefinitionsCollections et RowDefinitionsCollections
Cet exemple montre comment utiliser les méthodes dans les <xref:System.Windows.Controls.ColumnDefinitionCollection> et <xref:System.Windows.Controls.RowDefinitionCollection> classes pour effectuer des actions telles que l’ajout, effacer ou compter le contenu de lignes ou colonnes. Par exemple, vous pouvez <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, ou <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> les éléments qui sont inclus dans un <xref:System.Windows.Controls.ColumnDefinition> ou <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Windows.Controls.Grid> élément avec un <xref:System.Windows.FrameworkElement.Name%2A> de `grid1`. Le <xref:System.Windows.Controls.Grid> contient un <xref:System.Windows.Controls.StackPanel> contenant <xref:System.Windows.Controls.Button> éléments, chacun étant contrôlé par une méthode de collection différente. Lorsque vous cliquez sur un <xref:System.Windows.Controls.Button>, il active un appel de méthode dans le fichier code-behind.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Cet exemple définit une série de méthodes personnalisées, correspondant chacune à un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier. Vous pouvez modifier le nombre de colonnes et de lignes dans la <xref:System.Windows.Controls.Grid> de plusieurs façons, qui comprend l’ajout ou suppression de lignes et colonnes ; et en comptant le nombre total de lignes et de colonnes. Pour empêcher <xref:System.ArgumentOutOfRangeException> et <xref:System.ArgumentException> des exceptions, vous pouvez utiliser la fonctionnalité de vérification des erreurs qui le <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> fournit de la méthode.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
