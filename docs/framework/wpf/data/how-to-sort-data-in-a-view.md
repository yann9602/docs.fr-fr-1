---
title: "Comment&#160;: trier des donn&#233;es dans une vue | Microsoft Docs"
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
  - "liaison de données, regrouper des données dans des vues"
  - "liaison de données, trier des données dans des vues"
  - "regrouper des données dans des vues"
  - "trier des données dans des vues"
  - "vues, regrouper des données"
  - "vues, trier les données"
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: trier des donn&#233;es dans une vue
Cet exemple décrit comment trier des données dans une vue.  
  
## Exemple  
 L'exemple suivant crée un <xref:System.Windows.Controls.ListBox> simple et un <xref:System.Windows.Controls.Button> :  
  
 [!code-xml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton contient la logique de tri des éléments dans le <xref:System.Windows.Controls.ListBox> dans l'ordre décroissant.  Vous pouvez effectuer cette opération parce qu'ajouter ainsi des éléments au <xref:System.Windows.Controls.ListBox> les ajoute à l'objet <xref:System.Windows.Controls.ItemCollection> du <xref:System.Windows.Controls.ListBox>, et que <xref:System.Windows.Controls.ItemCollection> dérive de la classe <xref:System.Windows.Data.CollectionView>.  Si vous liez votre <xref:System.Windows.Controls.ListBox> à une collection en utilisant la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, vous pouvez utiliser la même technique pour effectuer le tri.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Tant que vous avez une référence à l'objet de vue, vous pouvez utiliser la même technique pour trier le contenu d'autres vues de collection.  Pour obtenir un exemple sur la manière d'obtenir une vue, consultez [Obtenir la vue par défaut d'une collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  Pour obtenir un autre exemple, consultez [Trier une colonne GridView lors d'un clic sur un en\-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  Pour plus d'informations sur les vues, consultez la section relative aux liaisons de collections dans [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Pour obtenir un exemple sur la manière d'appliquer une logique de tri en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consultez [Trier et grouper des données à l'aide d'une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## Voir aussi  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>   
 [Trier une colonne GridView lors d'un clic sur un en\-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)