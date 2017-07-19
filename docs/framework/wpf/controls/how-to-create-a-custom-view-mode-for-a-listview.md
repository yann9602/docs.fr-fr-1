---
title: "Comment&#160;: cr&#233;er un mode d&#39;affichage personnalis&#233; pour un ListView | Microsoft Docs"
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
  - "contrôles ListView, créer un mode Affichage personnalisé"
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un mode d&#39;affichage personnalis&#233; pour un ListView
Cet exemple indique comment créer un mode <xref:System.Windows.Controls.ListView.View%2A> personnalisé pour un contrôle <xref:System.Windows.Controls.ListView>.  
  
## Exemple  
 Vous devez utiliser la classe <xref:System.Windows.Controls.ViewBase> lorsque vous créez une vue personnalisée pour le contrôle <xref:System.Windows.Controls.ListView>.  L'exemple suivant illustre un mode d'affichage appelé `PlainView`, qui est dérivé de la classe <xref:System.Windows.Controls.ViewBase>.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Pour appliquer un style à la vue personnalisée, utilisez la classe <xref:System.Windows.Style>.  L'exemple suivant définit un <xref:System.Windows.Style> pour le mode d'affichage `PlainView`.  Dans l'exemple précédent, ce style est défini comme la valeur de la propriété <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> configurée pour `PlainView`.  
  
 [!code-xml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Pour définir la mise en page des données dans un mode d'affichage personnalisé, définissez un objet <xref:System.Windows.DataTemplate>.  L'exemple suivant définit un <xref:System.Windows.DataTemplate> qui peut être utilisé pour afficher des données en mode d'affichage `PlainView`.  
  
 [!code-xml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.ResourceKey> pour le mode d'affichage `PlainView` qui utilise le <xref:System.Windows.DataTemplate> défini dans l'exemple précédent.  
  
 [!code-xml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Un contrôle <xref:System.Windows.Controls.ListView> peut utiliser une vue personnalisée si vous affectez à la propriété <xref:System.Windows.Controls.ListView.View%2A> la clé de ressource.  L'exemple suivant indique comment spécifier `PlainView` comme mode d'affichage pour un <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Pour obtenir l'exemple complet, consultez [ListView avec plusieurs vues, exemple](http://go.microsoft.com/fwlink/?LinkID=160013)  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)