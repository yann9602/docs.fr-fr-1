---
title: "Comment&#160;: utiliser des d&#233;clencheurs pour appliquer un style aux &#233;l&#233;ments s&#233;lectionn&#233;s d&#39;un ListView | Microsoft Docs"
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
  - "Contrôles ListView, styles"
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: utiliser des d&#233;clencheurs pour appliquer un style aux &#233;l&#233;ments s&#233;lectionn&#233;s d&#39;un ListView
Cet exemple montre comment définir <xref:System.Windows.Style.Triggers%2A> pour un <xref:System.Windows.Controls.ListViewItem> contrôle afin que lorsqu’une valeur de propriété d’un <xref:System.Windows.Controls.ListViewItem> modifications, la <xref:System.Windows.Style> de la <xref:System.Windows.Controls.ListViewItem> change en fonction.  
  
## <a name="example"></a>Exemple  
 Si vous souhaitez que le <xref:System.Windows.Style> d’un <xref:System.Windows.Controls.ListViewItem> pour modifier en réponse aux modifications de propriété, définissez <xref:System.Windows.Style.Triggers%2A> pour la <xref:System.Windows.Style> modifier.  
  
 L’exemple suivant définit un <xref:System.Windows.Trigger> qui définit le <xref:System.Windows.Controls.Control.Foreground%2A> propriété <xref:System.Windows.Media.Brushes.Blue%2A> et modifie le <xref:System.Windows.FrameworkElement.Cursor%2A> pour afficher un <xref:System.Windows.Input.CursorType> lors de la <xref:System.Windows.UIElement.IsMouseOver%2A> modifications apportées aux propriétés `true`.  
  
 [!code-xml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 L’exemple suivant définit un <xref:System.Windows.MultiTrigger> qui définit le <xref:System.Windows.Controls.Control.Foreground%2A> propriété d’un <xref:System.Windows.Controls.ListViewItem> à <xref:System.Windows.Media.Brushes.Yellow%2A> lorsque le <xref:System.Windows.Controls.ListViewItem> est l’élément sélectionné et a le focus clavier.  
  
 [!code-xml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Control>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Rubriques "Comment"](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d’ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)