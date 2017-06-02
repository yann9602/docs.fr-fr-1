---
title: "Comment&#160;: utiliser un &#233;l&#233;ment mis en cache comme pinceau | Microsoft Docs"
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
  - "BitmapCache (WPF), utilisation"
  - "BitmapCacheBrush (WPF), utilisation"
  - "élément mis en cache (WPF), utiliser comme pinceau"
  - "CacheMode (WPF), utilisation"
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: utiliser un &#233;l&#233;ment mis en cache comme pinceau
Utilisez la classe <xref:System.Windows.Media.BitmapCacheBrush> pour réutiliser efficacement un élément mis en cache.  Pour mettre en cache un élément, créez une nouvelle instance de la classe <xref:System.Windows.Media.BitmapCache> et assignez\-la à la propriété <xref:System.Windows.UIElement.CacheMode%2A> de l'élément.  
  
## Exemple  
 L'exemple de code suivant indique comment réutiliser un élément mis en cache.  L'élément mis en cache est un contrôle <xref:System.Windows.Controls.Image> qui affiche une image de taille importante.  Le contrôle <xref:System.Windows.Controls.Image> est mis en cache en tant que bitmap à l'aide de la classe <xref:System.Windows.Media.BitmapCache>, et le cache est réutilisé en l'assignant à un <xref:System.Windows.Media.BitmapCacheBrush>.  Le pinceau est assigné à l'arrière\-plan de vingt\-cinq boutons pour une réutilisation efficace.  
  
 [!code-xml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## Voir aussi  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [Comment : améliorer les performances de rendu en mettant en cache un élément](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)