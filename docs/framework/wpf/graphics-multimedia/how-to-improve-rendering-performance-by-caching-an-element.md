---
title: "Comment : améliorer les performances de rendu en mettant en cache un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd12b811ae4dd89c645ada1f4f70b06f73b9b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Comment : améliorer les performances de rendu en mettant en cache un élément
Utilisez le <xref:System.Windows.Media.BitmapCache> classe pour améliorer les performances de rendu d’un type complexe <xref:System.Windows.UIElement>. Pour mettre en cache un élément, créer une nouvelle instance de la <xref:System.Windows.Media.BitmapCache> de classe et l’affecter à l’élément <xref:System.Windows.UIElement.CacheMode%2A> propriété. Vous pouvez réutiliser un <xref:System.Windows.Media.BitmapCache> efficacement dans un <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment créer un élément complexe et de mettre en cache sous forme de bitmap, ce qui améliore les performances lors de l’élément est animé. L’élément est une zone qui contient les géométries de forme avec un grand nombre de sommets. A <xref:System.Windows.Media.BitmapCache> avec la valeur par défaut des valeurs est attribué à la <xref:System.Windows.UIElement.CacheMode%2A> de la zone de dessin, et une animation montre l’évolution en douceur de l’image bitmap mise en cache.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Guide pratique pour utiliser un élément mis en cache comme pinceau](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
