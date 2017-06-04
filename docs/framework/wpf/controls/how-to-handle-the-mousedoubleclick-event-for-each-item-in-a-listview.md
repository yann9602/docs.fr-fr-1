---
title: "Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement MouseDoubleClick pour chaque &#233;l&#233;ment d&#39;un ListView | Microsoft Docs"
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
  - "contrôles ListView, MouseDoubleClick (événement)"
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement MouseDoubleClick pour chaque &#233;l&#233;ment d&#39;un ListView
Pour gérer un événement pour un élément dans un <xref:System.Windows.Controls.ListView>, vous devez ajouter un gestionnaire d'événements à chaque <xref:System.Windows.Controls.ListViewItem>.  Lorsqu'un <xref:System.Windows.Controls.ListView> est lié à une source de données, vous ne créez pas explicitement d'<xref:System.Windows.Controls.ListViewItem>, mais vous pouvez gérer l'événement pour chaque élément en ajoutant un <xref:System.Windows.EventSetter> à un style d'un <xref:System.Windows.Controls.ListViewItem>.  
  
## Exemple  
 L'exemple suivant crée un <xref:System.Windows.Controls.ListView> lié aux données et crée un <xref:System.Windows.Style> afin d'ajouter un gestionnaire d'événements à chaque <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 L'exemple suivant gère l'événement <xref:System.Windows.Controls.Control.MouseDoubleClick>.  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Bien que la procédure la plus courante consiste à lier un <xref:System.Windows.Controls.ListView> à une source de données, vous pouvez utiliser un style pour ajouter un gestionnaire d'événements à chaque <xref:System.Windows.Controls.ListViewItem> dans un <xref:System.Windows.Controls.ListView> non lié aux données, indépendamment du fait que vous créiez un <xref:System.Windows.Controls.ListViewItem> de manière explicite.  Pour plus d'information sur les contrôles <xref:System.Windows.Controls.ListViewItem> créés explicitement et implicitement, consultez <xref:System.Windows.Controls.ItemsControl>.  
  
## Voir aussi  
 <xref:System.Xml.XmlElement>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)