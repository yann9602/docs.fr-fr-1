---
title: "Comment&#160;: effectuer une liaison &#224; une source de donn&#233;es ADO.NET | Microsoft Docs"
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
  - "sources de données ADO.NET, lier à"
  - "liaison, à des sources de données ADO.NET"
  - "liaison de données, lier à des sources de données ADO.NET"
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: effectuer une liaison &#224; une source de donn&#233;es ADO.NET
Cet exemple montre comment lier un contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> à un [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## Exemple  
 Dans cet exemple, un objet `OleDbConnection` est utilisé pour se connecter à la source de données qui est dans un fichier `Access MDB` spécifié dans la chaîne de connexion.  Une fois la connexion établie, un objet `OleDbDataAdpater` est créé.  L'objet `OleDbDataAdpater` exécute une instruction [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] Select pour récupérer le recordset dans la base de données.  Les résultats de la commande [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] sont stockés dans un `DataTable` du `DataSet` en appelant la méthode `Fill` du `OleDbDataAdapter`.  Dans cet exemple, le `DataTable` est nommé `BookTable`.  L'exemple affecte ensuite à la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.ListBox> l'objet `DataSet`.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Vous pouvez ensuite lier la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> du <xref:System.Windows.Controls.ListBox> au `BookTable` du`DataSet` :  
  
 [!code-xml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate` est le <xref:System.Windows.DataTemplate> qui définit comment apparaissent les données :  
  
 [!code-xml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 Le `IntColorConverter` convertit un `int` en une couleur.  En utilisant ce convertisseur, la couleur <xref:System.Windows.Controls.TextBlock.Background%2A> du troisième <xref:System.Windows.Controls.TextBlock> apparaît verte si la valeur du `NumPages` est inférieure à 350 et rouge dans le cas contraire.  L'implémentation du convertisseur est montrée ici.  
  
## Voir aussi  
 <xref:System.Windows.Data.BindingListCollectionView>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)