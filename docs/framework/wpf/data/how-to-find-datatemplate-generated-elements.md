---
title: "Comment&#160;: rechercher des &#233;l&#233;ments g&#233;n&#233;r&#233;s par DataTemplate | Microsoft Docs"
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
  - "DataTemplate"
  - "rechercher des éléments DataTemplate"
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: rechercher des &#233;l&#233;ments g&#233;n&#233;r&#233;s par DataTemplate
Cet exemple montre comment rechercher des éléments qui sont générés par <xref:System.Windows.DataTemplate>.  
  
## Exemple  
 Dans cet exemple, <xref:System.Windows.Controls.ListBox> est lié à des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> utilise le <xref:System.Windows.DataTemplate> suivant :  
  
 [!code-xml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Si vous souhaitez retrouver l'élément <xref:System.Windows.Controls.TextBlock> généré par le <xref:System.Windows.DataTemplate> d'un certain <xref:System.Windows.Controls.ListBoxItem>, vous devez obtenir le <xref:System.Windows.Controls.ListBoxItem>, trouver le <xref:System.Windows.Controls.ContentPresenter> dans ce <xref:System.Windows.Controls.ListBoxItem>, puis appeler <xref:System.Windows.FrameworkTemplate.FindName%2A> sur le <xref:System.Windows.DataTemplate> qui est défini sur ce <xref:System.Windows.Controls.ContentPresenter>.  L'exemple suivant montre comment exécuter ces étapes.  À des fins de démonstration, cette exemple crée un message qui affiche le contenu du bloc de texte généré par <xref:System.Windows.DataTemplate>.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 L'exemple suivant illustre l'implémentation de `FindVisualChild`, qui utilise les méthodes <xref:System.Windows.Media.VisualTreeHelper> :  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## Voir aussi  
 [Rechercher des éléments générés par ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Portées de nom XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)