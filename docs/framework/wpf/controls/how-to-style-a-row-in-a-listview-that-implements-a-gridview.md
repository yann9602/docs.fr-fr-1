---
title: "Comment&#160;: appliquer un style &#224; une ligne dans un ListView impl&#233;mentant un GridView | Microsoft Docs"
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
  - "Contrôles GridView, styles de lignes"
  - "appliquer un style à des lignes dans des ListViews en implémentant des GridViews"
  - "Contrôles ListView, styles des lignes avec GridViews"
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: appliquer un style &#224; une ligne dans un ListView impl&#233;mentant un GridView
Cet exemple montre comment appliquer un style une ligne dans un <xref:System.Windows.Controls.ListView> contrôle qui implémente un <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.  
  
## <a name="example"></a>Exemple  
 Vous pouvez appliquer un style une ligne dans un <xref:System.Windows.Controls.ListView> contrôle en définissant une <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> sur la <xref:System.Windows.Controls.ListView> contrôle. Définir le style pour ses éléments qui sont représentés en tant que <xref:System.Windows.Controls.ListViewItem> objets. Le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> références le <xref:System.Windows.Controls.ControlTemplate> les objets qui sont utilisés pour afficher le contenu de la ligne.  
  
 L’exemple complet, duquel sont extraits les exemples suivants, affiche une collection d’informations de chanson stockée dans une [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] base de données. Chaque chanson de la base de données a un champ d’évaluation et la valeur de ce champ spécifie comment afficher une ligne d’informations de chanson.  
  
 L’exemple suivant montre comment définir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour la <xref:System.Windows.Controls.ListViewItem> objets qui représentent les chansons de la collection de chansons. Le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> références <xref:System.Windows.Controls.ControlTemplate> objets qui spécifient comment afficher une ligne d’informations de chanson.  
  
 [!code-xml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 L’exemple suivant illustre un <xref:System.Windows.Controls.ControlTemplate> qui ajoute la chaîne de texte `"Strongly Recommended"` à la ligne. Ce modèle est référencé dans le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> et s’affiche lorsque l’évaluation de la chanson a la valeur 5 (cinq). Le <xref:System.Windows.Controls.ControlTemplate> inclut un <xref:System.Windows.Controls.GridViewRowPresenter> objet dispose le contenu de la ligne dans les colonnes comme défini par le <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
 [!code-xml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 L’exemple suivant définit <xref:System.Windows.Controls.GridView>.  
  
 [!code-xml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Rubriques "Comment"](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)