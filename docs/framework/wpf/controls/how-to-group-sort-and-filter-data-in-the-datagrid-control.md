---
title: "Comment&#160;: grouper, trier et filtrer des donn&#233;es dans le contr&#244;le DataGrid | Microsoft Docs"
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
  - "DataGrid (WPF), filtre"
  - "DataGrid (WPF), groupe"
  - "DataGrid (WPF), tri"
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: grouper, trier et filtrer des donn&#233;es dans le contr&#244;le DataGrid
Il est souvent utile de consulter des données de différentes façons dans un <xref:System.Windows.Controls.DataGrid> en les regroupant, les triant et les filtrant.  Pour regrouper, trier et filtrer les données d'un <xref:System.Windows.Controls.DataGrid>, vous devez les lier à un <xref:System.Windows.Data.CollectionView> prenant en charge ces fonctions.  Vous pouvez ensuite utiliser les données de <xref:System.Windows.Data.CollectionView> sans avoir à assigner les données source sous\-jacentes.  Les modifications dans la vue de collection sont répercutées dans l'interface utilisateur <xref:System.Windows.Controls.DataGrid>.  
  
 La classe <xref:System.Windows.Data.CollectionView> fournit les fonctionnalités de regroupement et de tri pour une source de données qui implémente l'interface <xref:System.Collections.IEnumerable>.  La classe <xref:System.Windows.Data.CollectionViewSource> vous permet de définir les propriétés<xref:System.Windows.Data.CollectionView> à partir du code XAML.  
  
 Dans cet exemple, une collection d'objets `Task` est liée à une <xref:System.Windows.Data.CollectionViewSource>.  Le <xref:System.Windows.Data.CollectionViewSource> est utilisé en tant que <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid>.  Le regroupement, le tri et le filtrage sont exécutés sur le <xref:System.Windows.Data.CollectionViewSource> et sont affichés dans l'interface utilisateur <xref:System.Windows.Controls.DataGrid>.  
  
 ![Données groupées dans un DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF\_DataGridGroups")  
Données regroupées dans une grille de données  
  
## Utilisation de CollectionViewSource en tant que ItemsSource  
 Pour regrouper, trier et filtrer les données d'un contrôle <xref:System.Windows.Controls.DataGrid>, vous devez lier le <xref:System.Windows.Controls.DataGrid> à un <xref:System.Windows.Data.CollectionView> prenant en charge ces fonctions.  Dans cet exemple, le <xref:System.Windows.Controls.DataGrid> est lié à un <xref:System.Windows.Data.CollectionViewSource> qui fournit ces fonctions pour un <xref:System.Collections.Generic.List%601> d'objets `Task`.  
  
#### Pour lier un DataGrid à un CollectionViewSource  
  
1.  Créez une collection de données qui implémente l'interface <xref:System.Collections.IEnumerable>.  
  
     Si vous utilisez <xref:System.Collections.Generic.List%601> pour créer votre collection, vous devez créer une nouvelle classe qui hérite de <xref:System.Collections.Generic.List%601> au lieu d'instancier une instance de <xref:System.Collections.Generic.List%601>.  Cela vous permet de lier les données à la collection en XAML.  
  
    > [!NOTE]
    >  Les objets dans la collection doivent implémenter l'interface modifiée <xref:System.ComponentModel.INotifyPropertyChanged> et l'interface <xref:System.ComponentModel.IEditableObject> afin que le <xref:System.Windows.Controls.DataGrid> réponde correctement aux modifications et éditions de propriété.  Pour plus d'informations, consultez [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  En XAML, créez une instance de la classe de collection et définissez la [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md).  
  
3.  En XAML, créez une instance de la classe <xref:System.Windows.Data.CollectionViewSource>, définissez la [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md), puis définissez l'instance de votre classe de collection en tant que <xref:System.Windows.Data.CollectionViewSource.Source%2A>.  
  
     [!code-xml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  Créez une instance de la classe <xref:System.Windows.Controls.DataGrid>, puis affectez à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la valeur <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-xml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  Pour accéder à <xref:System.Windows.Data.CollectionViewSource> depuis votre code, utilisez la méthode <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> pour obtenir une référence à <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## Regroupement d'éléments dans un DataGrid  
 Pour spécifier la façon dont les éléments sont regroupés dans un <xref:System.Windows.Controls.DataGrid>, vous utilisez le type <xref:System.Windows.Data.PropertyGroupDescription> pour regrouper les éléments en mode Source.  
  
#### Pour grouper des éléments dans une grille de données à l'aide du langage XAML  
  
1.  Créez un <xref:System.Windows.Data.PropertyGroupDescription> qui spécifie la propriété à utiliser pour le regroupement.  Vous pouvez spécifier la propriété en XAML ou dans le code.  
  
    1.  En XAML, affectez à <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> le nom de la propriété à l'aide de laquelle effectuer le regroupement.  
  
    2.  Dans le code, passez au constructeur le nom de la propriété à l'aide de laquelle effectuer le regroupement.  
  
2.  Ajoutez le <xref:System.Windows.Data.PropertyGroupDescription> à la  collection <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=fullName>.  
  
3.  Ajoutez des instances supplémentaires de <xref:System.Windows.Data.PropertyGroupDescription> à la collection <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> pour ajouter d'autres niveaux de regroupement.  
  
     [!code-xml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  Pour supprimer un groupe, supprimez le <xref:System.Windows.Data.PropertyGroupDescription> de la collection <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.  
  
5.  Pour supprimer tous les groupes, appelez la méthode <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> de la collection <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 Lorsque les éléments sont regroupés dans <xref:System.Windows.Controls.DataGrid>, vous pouvez définir un <xref:System.Windows.Controls.GroupStyle> qui spécifie l'apparence de chaque groupe.  Vous appliquez le <xref:System.Windows.Controls.GroupStyle> en l'ajoutant à la collection <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> de la grille de données.  Si vous avez plusieurs niveaux de regroupement, vous pouvez appliquer des styles différents à chaque niveau de groupe.  Les styles sont appliqués dans l'ordre dans lequel ils sont définis.  Par exemple, si vous définissez deux styles, les premiers s'appliqueront aux groupes de lignes de niveau supérieur.  Le deuxième style sera appliqué à tous les groupes de lignes au deuxième niveau et au niveau inférieur.  Le <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.GroupStyle> est le <xref:System.Windows.Data.CollectionViewGroup> que le groupe représente.  
  
#### Pour modifier l'apparence des en\-têtes de groupe de lignes  
  
1.  Créez un <xref:System.Windows.Controls.GroupStyle> qui définisse l'apparence du groupe de lignes.  
  
2.  Placez <xref:System.Windows.Controls.GroupStyle> à l'intérieur des balises `<DataGrid.GroupStyle>`.  
  
     [!code-xml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## Tri d'éléments dans un DataGrid  
 Pour spécifier la façon dont les éléments sont triés dans un <xref:System.Windows.Controls.DataGrid>, vous utilisez le type <xref:System.ComponentModel.SortDescription> pour trier les éléments en mode Source.  
  
#### Pour trier des éléments dans un DataGrid  
  
1.  Créez un <xref:System.ComponentModel.SortDescription> qui spécifie la propriété à l'aide de laquelle effectuer le regroupement.  Vous pouvez spécifier la propriété en XAML ou dans le code.  
  
    1.  En XAML, affectez à <xref:System.ComponentModel.SortDescription.PropertyName%2A> le nom de la propriété à l'aide de laquelle effectuer le tri.  
  
    2.  Dans le code, passez au constructeur le nom de la propriété à l'aide de laquelle effectuer le tri, ainsi que le <xref:System.ComponentModel.ListSortDirection>.  
  
2.  Ajoutez le <xref:System.ComponentModel.SortDescription> à la collection <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=fullName>.  
  
3.  Ajoutez des instances supplémentaires de <xref:System.ComponentModel.SortDescription> à la collection <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> pour trier par propriétés supplémentaires.  
  
     [!code-xml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## Filtrage d'éléments dans un DataGrid  
 Pour filtrer des éléments d'un <xref:System.Windows.Controls.DataGrid> à l'aide d'un <xref:System.Windows.Data.CollectionViewSource>, fournissez la logique de filtrage du gestionnaire pour l'événement <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=fullName>.  
  
#### Pour filtrer des éléments dans un DataGrid  
  
1.  Ajoutez un gestionnaire pour l'événement <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=fullName>.  
  
2.  Dans le gestionnaire d'événements <xref:System.Windows.Data.CollectionViewSource.Filter>, définissez la logique de filtrage.  
  
     Le filtre est appliqué à chaque fois que la vue est actualisée.  
  
     [!code-xml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 Vous pouvez également filtrer les éléments d'un <xref:System.Windows.Controls.DataGrid> en créant une méthode qui fournisse la logique de filtrage, et en définissant la propriété <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=fullName> pour appliquer le filtre.  Pour voir un exemple de cette méthode, consultez [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
## Exemple  
 L'exemple suivant montre comment regrouper, trier et filtrer les données `Task` dans une <xref:System.Windows.Data.CollectionViewSource> et comment ensuite afficher ces données `Task` dans un <xref:System.Windows.Controls.DataGrid>.  Le <xref:System.Windows.Data.CollectionViewSource> est utilisé en tant que <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid>.  Le regroupement, le tri et le filtrage sont exécutés sur le <xref:System.Windows.Data.CollectionViewSource> et sont affichés dans l'interface utilisateur <xref:System.Windows.Controls.DataGrid>.  
  
 Pour tester cet exemple, vous devrez ajuster le nom de DGGroupSortFilterExample pour qu'il corresponde au nom de votre projet.  Si vous utilisez Visual Basic, vous devrez modifier le nom de la classe de <xref:System.Windows.Window> comme indiqué ci\-dessous.  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## Compilation du code  
  
## Programmation fiable  
  
## Sécurité .NET Framework  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Créer et effectuer une liaison à un ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)   
 [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [Trier et grouper des données à l'aide d'une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)