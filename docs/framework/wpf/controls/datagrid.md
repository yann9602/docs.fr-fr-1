---
title: "DataGrid | Microsoft Docs"
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
  - "contrôles (WPF), DataGrid"
  - "DataGrid (WPF), tâches courantes pour"
  - "DataGrid (WPF), personnaliser l'apparence de"
  - "types de colonnes du DataGrid (WPF)"
  - "colonnes du DataGrid (WPF), utilisation"
  - "DataGrid (contrôle WPF)"
  - "scénarios du DataGrid (WPF)"
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DataGrid
Le contrôle <xref:System.Windows.Controls.DataGrid> vous permet d'afficher et de modifier des données à partir de nombreuses sources différentes, telles qu'une base de données SQL, une requête LINQ ou toute autre source de données pouvant être liée.  Pour plus d'informations, consultez [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Les colonnes peuvent afficher du texte, des contrôles, tels qu'un <xref:System.Windows.Controls.ComboBox>, ou tout autre contenu WPF, tel que des images, des boutons ou n'importe quel contenu d'un modèle.  Vous pouvez utiliser un <xref:System.Windows.Controls.DataGridTemplateColumn> pour afficher des données définies dans un modèle.  Le tableau suivant répertorie les types de colonnes fournis par défaut.  
  
|Type de colonne généré|Type de données|  
|----------------------------|---------------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 L'apparence de <xref:System.Windows.Controls.DataGrid> \(telle que la police, la couleur et la taille de la cellule\) peut être personnalisée.  <xref:System.Windows.Controls.DataGrid> prend en charge toutes les fonctionnalités de création de styles et de modèles d'autres contrôles WPF.  <xref:System.Windows.Controls.DataGrid> inclut également des comportements par défaut et personnalisables pour la modification, le tri et la validation.  
  
 Le tableau suivant répertorie certaines tâches courantes pour <xref:System.Windows.Controls.DataGrid> et comment les accomplir.  En affichant l'API connexe, vous pouvez obtenir davantage d'informations et des exemples de code.  
  
|Scénario|Approche|  
|--------------|--------------|  
|Alternance des couleurs d'arrière\-plan|Affectez à la propriété <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> une valeur supérieure ou égale à 2, puis assignez un <xref:System.Windows.Media.Brush> aux propriétés <xref:System.Windows.Controls.DataGrid.RowBackground%2A> et <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>.|  
|Définir le mode de sélection de la cellule et de la ligne|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> et <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personnaliser l'apparence visuelle des en\-têtes, des cellules et des lignes|Appliquez un nouveau <xref:System.Windows.Style> aux propriétés <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A> ou <xref:System.Windows.Controls.DataGrid.RowStyle%2A>.|  
|Définir les options de dimensionnement|Définissez les propriétés <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A> ou <xref:System.Windows.FrameworkElement.MinWidth%2A>.  Pour plus d'informations, consultez [Options de dimensionnement dans le contrôle DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Accéder aux éléments sélectionnés|Vérifiez la propriété <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> pour obtenir les cellules sélectionnées et la propriété <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> pour obtenir les lignes sélectionnées.  Pour plus d'informations, consultez <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personnaliser des interactions d'utilisateur final|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> et <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>.|  
|Annuler ou modifier les colonnes générées automatiquement|Gérer l'événement <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>.|  
|Figer une colonne|Affectez à la propriété <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> la valeur 1 et placez la colonne à l'extrême gauche en affectant à la propriété <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> la valeur 0.|  
|Utiliser des données XML comme source de données|Liez la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.DataGrid> à la requête XPath qui représente la collection d'éléments.  Créez chaque colonne de <xref:System.Windows.Controls.DataGrid>.  Liez chaque colonne en définissant le XPath de la liaison à la requête qui obtient la propriété de la source d'élément.  Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : affichage de données d'une base de données SQL Server dans un contrôle DataGrid](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Explique comment configurer un nouveau projet WPF, ajouter un élément Entity Framework, définir la source et afficher les données dans <xref:System.Windows.Controls.DataGrid>.|  
|[Comment : ajouter des détails de ligne à un contrôle DataGrid](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Explique comment créer des détails de ligne pour <xref:System.Windows.Controls.DataGrid>|  
|[Comment : implémenter la validation avec le contrôle DataGrid](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Explique comment valider des valeurs dans des cellules et lignes de <xref:System.Windows.Controls.DataGrid> et afficher les commentaires de validation.|  
|[Comportement par défaut du clavier et de la souris dans le contrôle DataGrid](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Explique comment interagir avec le contrôle <xref:System.Windows.Controls.DataGrid> à l'aide du clavier et de la souris.|  
|[Comment : grouper, trier et filtrer des données dans le contrôle DataGrid](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Explique comment pour afficher des données dans <xref:System.Windows.Controls.DataGrid> de différentes façons, en regroupant, triant et filtrant les données.|  
|[Options de dimensionnement dans le contrôle DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Indique comment contrôler le dimensionnement absolu et automatique dans le <xref:System.Windows.Controls.DataGrid>.|  
  
## Voir aussi  
 <xref:System.Windows.Controls.DataGrid>   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Contrôles](../../../../docs/framework/wpf/controls/index.md)   
 [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)