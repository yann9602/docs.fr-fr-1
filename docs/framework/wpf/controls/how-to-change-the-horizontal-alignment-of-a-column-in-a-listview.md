---
title: "Comment&#160;: modifier l&#39;alignement horizontal d&#39;une colonne dans un ListView | Microsoft Docs"
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
  - "contrôles ListView, alignement horizontal"
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: modifier l&#39;alignement horizontal d&#39;une colonne dans un ListView
Par défaut, le contenu de chaque colonne d'un <xref:System.Windows.Controls.ListViewItem> est aligné à gauche.  Vous pouvez modifier l'alignement de chaque colonne en fournissant un <xref:System.Windows.DataTemplate> et en définissant la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> sur l'élément dans le <xref:System.Windows.DataTemplate>.  Cette rubrique montre comment un <xref:System.Windows.Controls.ListView> aligne son contenu par défaut et comment modifier l'alignement d'une colonne dans un <xref:System.Windows.Controls.ListView>.  
  
## Exemple  
 Dans l'exemple suivant, les données des colonnes `Title` et `ISBN` sont alignées à gauche.  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Pour modifier l'alignement de la colonne `ISBN`, vous devez spécifier que la propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> de chaque <xref:System.Windows.Controls.ListViewItem> est <xref:System.Windows.HorizontalAlignment>, afin que les éléments de chaque <xref:System.Windows.Controls.ListViewItem> puissent couvrir ou être positionnés sur toute la largeur de chaque colonne.  Comme le <xref:System.Windows.Controls.ListView> est lié à une source de données, vous devez créer un style qui définit l'<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.  Vous devez ensuite utiliser un <xref:System.Windows.DataTemplate> pour afficher le contenu au lieu d'utiliser la propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>.  Pour afficher l'`ISBN` de chaque modèle, le <xref:System.Windows.DataTemplate> peut uniquement contenir un <xref:System.Windows.Controls.TextBlock> dont la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a la valeur <xref:System.Windows.HorizontalAlignment>.  
  
 L'exemple suivant définit le style et le <xref:System.Windows.DataTemplate> nécessaires pour aligner le contenu de la colonne `ISBN` à droite et modifie la <xref:System.Windows.Controls.GridViewColumn> pour référencer le <xref:System.Windows.DataTemplate>.  
  
 [!code-xml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)