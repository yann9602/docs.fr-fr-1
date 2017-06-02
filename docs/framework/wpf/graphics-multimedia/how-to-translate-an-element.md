---
title: "Comment&#160;: traduire un &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes, TranslateTransform"
  - "graphiques, translations"
  - "TranslateTransform (classe)"
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: traduire un &#233;l&#233;ment
Cet exemple montre comment traduire \(déplacer\) un élément en utilisant un <xref:System.Windows.Media.TranslateTransform>.  
  
 La classe <xref:System.Windows.Media.TranslateTransform> est particulièrement utile pour déplacer des éléments à l'intérieur des panneaux qui ne prennent pas en charge le positionnement absolu.  Par exemple, vous pouvez déplacer un élément dans un <xref:System.Windows.Controls.StackPanel> ou un <xref:System.Windows.Controls.DockPanel> en appliquant un <xref:System.Windows.Media.TranslateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> d'un élément.  
  
 Utilisez la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> du <xref:System.Windows.Media.TranslateTransform> pour spécifier la quantité, en [pixels](GTMT), pour déplacer l'élément le long de l'axe x.  Utilisez la propriété <xref:System.Windows.Media.TranslateTransform.Y%2A> pour spécifier la quantité, en pixels, pour déplacer l'élément le long de l'axe y.  Enfin, appliquez le <xref:System.Windows.Media.TranslateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de l'élément.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.TranslateTransform> pour déplacer un élément de 50 [pixels](GTMT) vers la droite et de 50 pixels vers le bas.  
  
## Exemple  
 [!code-xml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Pour l'exemple complet, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## Voir aussi  
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)