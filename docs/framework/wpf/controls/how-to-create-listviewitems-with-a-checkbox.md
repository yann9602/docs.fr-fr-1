---
title: "Comment&#160;: cr&#233;er des ListViewItems avec une case &#224; cocher | Microsoft Docs"
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
  - "contrôles ListView"
  - "contrôles de case à cocher"
  - "Contrôles ListView, contrôle de case à cocher"
  - "Contrôle CheckBox, contrôle ListView"
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er des ListViewItems avec une case &#224; cocher
Cet exemple montre comment afficher une colonne de <xref:System.Windows.Controls.CheckBox> des contrôles dans un <xref:System.Windows.Controls.ListView> contrôle qui utilise un <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Exemple  
 Pour créer une colonne qui contient <xref:System.Windows.Controls.CheckBox> des contrôles dans un <xref:System.Windows.Controls.ListView>, créer un <xref:System.Windows.DataTemplate> contenant un <xref:System.Windows.Controls.CheckBox>. Puis définissez la <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> d’un <xref:System.Windows.Controls.GridViewColumn> à la <xref:System.Windows.DataTemplate>.  
  
 L’exemple suivant illustre un <xref:System.Windows.DataTemplate> contenant un <xref:System.Windows.Controls.CheckBox>. L’exemple lie le <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriété du <xref:System.Windows.Controls.CheckBox> à la <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> valeur de propriété de la <xref:System.Windows.Controls.ListViewItem> qui le contient. Par conséquent, lorsque le <xref:System.Windows.Controls.ListViewItem> contenant le <xref:System.Windows.Controls.CheckBox> est sélectionnée, le <xref:System.Windows.Controls.CheckBox> est activée.  
  
 [!code-xml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 L’exemple suivant montre comment créer une colonne de <xref:System.Windows.Controls.CheckBox> contrôles. Modifier la colonne, l’exemple définit le <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriété de la <xref:System.Windows.Controls.GridViewColumn> à la <xref:System.Windows.DataTemplate>.  
  
 [!code-xml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Control>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Rubriques "Comment"](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d’ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)