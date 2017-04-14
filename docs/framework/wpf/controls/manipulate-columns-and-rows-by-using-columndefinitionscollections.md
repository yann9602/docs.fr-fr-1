---
title: "Comment&#160;: manipuler des colonnes et des lignes &#224; l&#39;aide de ColumnDefinitionsCollections et RowDefinitionsCollections | Microsoft Docs"
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
  - "classes, ColumnDefinitionCollection"
  - "classes, RowDefinitionCollection"
  - "ColumnDefinitionCollection (classe)"
  - "contrôles, Grid (classe)"
  - "Grid (contrôle), ColumnDefinitionCollection (classe)"
  - "Grid (contrôle), RowDefinitionCollection (classe)"
  - "RowDefinitionCollection (classe)"
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: manipuler des colonnes et des lignes &#224; l&#39;aide de ColumnDefinitionsCollections et RowDefinitionsCollections
Cet exemple montre comment utiliser les méthodes dans les classes <xref:System.Windows.Controls.ColumnDefinitionCollection> et <xref:System.Windows.Controls.RowDefinitionCollection> pour exécuter des actions, par exemple ajouter, effacer ou compter le contenu de lignes ou de colonnes.  Par exemple, vous pouvez <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A> ou <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> les éléments qui sont inclus dans <xref:System.Windows.Controls.ColumnDefinition> ou <xref:System.Windows.Controls.RowDefinition>.  
  
## Exemple  
 L'exemple suivant crée un élément <xref:System.Windows.Controls.Grid> avec le <xref:System.Windows.FrameworkElement.Name%2A> `grid1`.  La <xref:System.Windows.Controls.Grid> contient un <xref:System.Windows.Controls.StackPanel> qui maintient les éléments <xref:System.Windows.Controls.Button>, chacun étant contrôlé par une méthode de collection différente.  Lorsque vous cliquez sur un <xref:System.Windows.Controls.Button>, il active un appel de méthode dans le fichier code\-behind.  
  
 [!code-xml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Cet exemple définit une série de méthodes personnalisées, correspondant chacune à un événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dans le fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Vous pouvez modifier le nombre de colonnes et de lignes de plusieurs façons dans la <xref:System.Windows.Controls.Grid>, ce qui inclut l'ajout ou la suppression de lignes et de colonnes et le comptage du nombre total de lignes et de colonnes.  Pour éviter les exceptions <xref:System.ArgumentOutOfRangeException> et <xref:System.ArgumentException>, vous pouvez utiliser la fonctionnalité de vérification des erreurs fournie par la méthode <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A>.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.ColumnDefinitionCollection>   
 <xref:System.Windows.Controls.RowDefinitionCollection>