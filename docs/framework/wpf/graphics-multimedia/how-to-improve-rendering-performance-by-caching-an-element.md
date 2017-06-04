---
title: "Comment&#160;: am&#233;liorer les performances de rendu en mettant en cache un &#233;l&#233;ment | Microsoft Docs"
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
  - "BitmapCache (WPF), améliorer les performances de rendu"
  - "CacheMode (WPF), améliorer les performances de rendu"
  - "performance (WPF), mettre en cache un élément"
  - "performances de rendu (WPF), mettre en cache un élément"
  - "UIElement (WPF), mettre en cache"
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: am&#233;liorer les performances de rendu en mettant en cache un &#233;l&#233;ment
Utilisez la classe <xref:System.Windows.Media.BitmapCache> pour améliorer les performances de rendu d'un <xref:System.Windows.UIElement> complexe.  Pour mettre en cache un élément, créez une nouvelle instance de la classe <xref:System.Windows.Media.BitmapCache> et assignez\-la à la propriété <xref:System.Windows.UIElement.CacheMode%2A> de l'élément.  Vous pouvez réutiliser efficacement un <xref:System.Windows.Media.BitmapCache> dans un <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## Exemple  
 L'exemple de code suivant indique comment créer un élément complexe et le mettre en cache en tant que bitmap, afin d'améliorer les performances lorsque l'élément est animé.  L'élément est une zone de dessin contenant des formes géométriques avec de nombreux vertex.  Un <xref:System.Windows.Media.BitmapCache> avec les valeurs par défaut est assigné au <xref:System.Windows.UIElement.CacheMode%2A> de la zone de dessin et une animation montre la mise à l'échelle progressive de la bitmap mise en cache.  
  
 [!code-xml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## Voir aussi  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [Comment : utiliser un élément mis en cache comme pinceau](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)