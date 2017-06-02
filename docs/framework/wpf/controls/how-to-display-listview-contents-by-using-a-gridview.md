---
title: "Comment&#160;: afficher un contenu ListView &#224; l&#39;aide d&#39;un GridView | Microsoft Docs"
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
  - "GridView, afficher des contenus ListView"
  - "contrôles ListView, afficher des contenus avec GridView"
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: afficher un contenu ListView &#224; l&#39;aide d&#39;un GridView
Cet exemple indique comment définir un mode d'affichage <xref:System.Windows.Controls.GridView> pour un contrôle <xref:System.Windows.Controls.ListView>.  
  
## Exemple  
 Vous pouvez définir le mode d'affichage d'un <xref:System.Windows.Controls.GridView> en spécifiant des objets <xref:System.Windows.Controls.GridViewColumn>.  L'exemple suivant indique comment définir des objets <xref:System.Windows.Controls.GridViewColumn> qui créent une liaison avec le contenu des données spécifié pour le contrôle <xref:System.Windows.Controls.ListView>.  Cet exemple <xref:System.Windows.Controls.GridView> spécifie trois objets <xref:System.Windows.Controls.GridViewColumn> qui sont mappés aux champs `FirstName`, `LastName` et `EmployeeNumber` du `EmployeeInfoDataSource` défini comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> du contrôle <xref:System.Windows.Controls.ListView>.  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L'illustration suivante indique comment apparaît cet exemple.  
  
 ![Sortie de ListView avec GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)