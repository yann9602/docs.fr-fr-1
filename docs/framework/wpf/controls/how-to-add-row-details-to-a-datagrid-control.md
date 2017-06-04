---
title: "Comment&#160;: ajouter des d&#233;tails de ligne &#224; un contr&#244;le DataGrid | Microsoft Docs"
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
  - "DataGrid (WPF), détails de ligne"
  - "DataTemplate (WPF), DataGrid"
  - "détails de ligne (WPF), DataGrid"
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: ajouter des d&#233;tails de ligne &#224; un contr&#244;le DataGrid
Lorsque vous utilisez le contrôle <xref:System.Windows.Controls.DataGrid>, vous pouvez personnaliser la présentation des données en ajoutant une section de détails de ligne.  L'ajout d'une section de détails de ligne vous permet de grouper certaines données dans un modèle qui est éventuellement visible ou réduit.  Par exemple, vous pouvez ajouter des détails de ligne à un <xref:System.Windows.Controls.DataGrid> qui présente uniquement un résumé des données pour chaque ligne dans le <xref:System.Windows.Controls.DataGrid>, mais présente davantage de champs de données lorsque l'utilisateur sélectionne une ligne.  Vous définissez le modèle pour la section de détails de ligne dans la propriété <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.  L'illustration suivante montre un exemple d'une section de détails de ligne.  
  
 ![DataGrid affiché avec détails de la ligne](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP\_RowDetails")  
  
 Vous définissez le modèle de détails de ligne comme XAML inline ou comme une ressource.  Les deux options sont illustrées dans les procédures suivantes.  Un modèle de données ajouté en tant que ressource peut être utilisé dans tout le projet sans avoir à recréer le modèle.  Un modèle de données ajouté en tant que XAML inline est uniquement accessible à partir du contrôle où il est défini.  
  
### Pour afficher des détails de la ligne à l'aide de XAML inline  
  
1.  Créez un <xref:System.Windows.Controls.DataGrid> qui affiche des données à partir d'une source de données.  
  
2.  Dans l'élément <xref:System.Windows.Controls.DataGrid>, ajoutez un élément <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.  
  
3.  Créez un <xref:System.Windows.DataTemplate> qui définit l'apparence de la section de détails de ligne.  
  
     Le XAML suivant affiche le <xref:System.Windows.Controls.DataGrid> et comment définir le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.  Le <xref:System.Windows.Controls.DataGrid> affiche trois valeurs dans chaque ligne et trois valeurs en plus lorsque la ligne est sélectionnée.  
  
     [!code-xml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Le code suivant affiche la requête utilisée pour sélectionner les données affichées dans le <xref:System.Windows.Controls.DataGrid>.  Dans cet exemple, la requête sélectionne des données d'une entité qui contient les informations client.  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### Pour afficher des détails de la ligne à l'aide d'une ressource  
  
1.  Créez un <xref:System.Windows.Controls.DataGrid> qui affiche des données à partir d'une source de données.  
  
2.  Ajoutez un élément <xref:System.Windows.FrameworkElement.Resources%2A> à l'élément racine, tel qu'un contrôle <xref:System.Windows.Window> ou un contrôle <xref:System.Windows.Controls.Page> ou ajoutez un élément <xref:System.Windows.Application.Resources%2A> à la classe <xref:System.Windows.Application> dans le fichier App.xaml \(ou Application.xaml\).  
  
3.  Dans l'élément de ressources, créez un <xref:System.Windows.DataTemplate> qui définit l'apparence de la section de détails de ligne.  
  
     Le XAML suivant affiche le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> défini dans la classe <xref:System.Windows.Application>.  
  
     [!code-xml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  Sur le <xref:System.Windows.DataTemplate>, affectez au [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) une valeur qui identifie de manière unique le modèle de données.  
  
5.  Dans l'élément <xref:System.Windows.Controls.DataGrid>, affectez à la propriété <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> la ressource définie dans les étapes précédentes.  Assignez la ressource comme une ressource statique.  
  
     Le XAML suivant affiche la propriété <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> définie à l'aide de la ressource de l'exemple précédent.  
  
     [!code-xml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### Pour définir la visibilité et empêcher le défilement horizontal pour les détails de ligne  
  
1.  Si nécessaire, affectez à la propriété <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> une valeur <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>.  
  
     Par défaut, <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> est affecté à la valeur.  Vous pouvez lui affecter la valeur <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> pour indiquer les détails pour toutes les lignes ou <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> pour masquer les détails pour toutes les lignes.  
  
2.  Si nécessaire, affectez à la propriété <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> la valeur `true` pour empêcher la section de détails de ligne de défiler horizontalement.