---
title: "Comment&#160;: cr&#233;er un &#233;l&#233;ment Panel personnalis&#233; | Microsoft Docs"
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
  - "éléments Panel personnalisés"
  - "Panel (contrôle)"
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un &#233;l&#233;ment Panel personnalis&#233;
## Exemple  
 Cet exemple montre comment substituer le comportement de disposition par défaut de l'élément <xref:System.Windows.Controls.Panel> et créer des éléments de disposition personnalisés dérivés de <xref:System.Windows.Controls.Panel>.  
  
 L'exemple définit un élément <xref:System.Windows.Controls.Panel> personnalisé simple appelé `PlotPanel` qui positionne les éléments enfants d'après deux coordonnées x et y codées en dur.  Dans cet exemple, `x` et `y` ont tous les deux la valeur `50` ; par conséquent, tous les éléments enfants sont positionnés à cet emplacement sur les axes x et y.  
  
 Pour implémenter des comportements <xref:System.Windows.Controls.Panel> personnalisés, l'exemple utilise les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  Chaque méthode retourne les données <xref:System.Windows.Size> qui sont nécessaires pour positionner et restituer les éléments enfants.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Panel>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Créer un panneau d'habillage du contenu personnalisé, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159979)