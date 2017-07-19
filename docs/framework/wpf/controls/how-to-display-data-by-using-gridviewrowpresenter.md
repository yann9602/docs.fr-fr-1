---
title: "Comment&#160;: afficher des donn&#233;es &#224; l&#39;aide de GridViewRowPresenter | Microsoft Docs"
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
  - "afficher des données à l'aide de GridViewRowPresenter"
  - "GridViewRowPresenter"
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: afficher des donn&#233;es &#224; l&#39;aide de GridViewRowPresenter
Cet exemple montre comment utiliser les objets <xref:System.Windows.Controls.GridViewRowPresenter> et <xref:System.Windows.Controls.GridViewHeaderRowPresenter> pour afficher des données dans les colonnes.  
  
## Exemple  
 L'exemple suivant indique comment spécifier une <xref:System.Windows.Controls.GridViewColumnCollection> qui affiche le <xref:System.DateTime.DayOfWeek%2A> et le <xref:System.DateTime.Year%2A> d'un objet <xref:System.DateTime> à l'aide des objets <xref:System.Windows.Controls.GridViewRowPresenter> et <xref:System.Windows.Controls.GridViewHeaderRowPresenter>.  L'exemple définit également un <xref:System.Windows.Style> pour l'<xref:System.Windows.Controls.GridViewColumn.Header%2A> d'une <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewColumnCollection>   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)