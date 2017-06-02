---
title: "Comment&#160;: peindre une zone avec une vid&#233;o | Microsoft Docs"
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
  - "pinceaux, peindre avec une vidéo"
  - "peindre avec une vidéo"
  - "vidéo, peindre avec"
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: peindre une zone avec une vid&#233;o
Cet exemple montre comment peindre une zone avec un média.  Pour peindre une zone avec un média, vous pouvez par exemple utiliser un <xref:System.Windows.Controls.MediaElement> avec un <xref:System.Windows.Media.VisualBrush>.  Utilisez le <xref:System.Windows.Controls.MediaElement> pour charger et lancer le média, puis utilisez\-le pour définir la propriété <xref:System.Windows.Media.VisualBrush.Visual%2A> du <xref:System.Windows.Media.VisualBrush>.  Vous pouvez ensuite utiliser le <xref:System.Windows.Media.VisualBrush> pour peindre une zone avec le média chargé.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Controls.MediaElement> et un <xref:System.Windows.Media.VisualBrush> pour peindre le <xref:System.Windows.Controls.TextBlock.Foreground%2A> d'un contrôle <xref:System.Windows.Controls.TextBlock> avec une vidéo.  Cet exemple affecte `true` à la propriété <xref:System.Windows.Controls.MediaElement.IsMuted%2A> du <xref:System.Windows.Controls.MediaElement> pour qu'il ne produise aucun son.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## Exemple  
 Étant donné que <xref:System.Windows.Media.VisualBrush> hérite de la classe <xref:System.Windows.Media.TileBrush>, il fournit plusieurs modes de mosaïque.  En affectant <xref:System.Windows.Media.TileMode> à la propriété <xref:System.Windows.Media.TileBrush.TileMode%2A> d'un <xref:System.Windows.Media.VisualBrush> et en affectant à sa propriété <xref:System.Windows.Media.TileBrush.Viewport%2A> une valeur inférieure à la zone que vous peignez, vous pouvez créer un modèle en mosaïque.  
  
 L'exemple suivant est identique à l'exemple précédent, mais le <xref:System.Windows.Media.VisualBrush> génère un modèle à partir de la vidéo.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Pour plus d'informations sur l'ajout d'un fichier de contenu, tel qu'un fichier multimédia, à votre application, consultez [Fichiers de ressources, de contenu et de données d'une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  Lorsque vous ajoutez un fichier multimédia, vous devez l'ajouter comme un fichier de contenu, pas comme un fichier de ressources.  
  
## Voir aussi  
 <xref:System.Windows.Media.VisualBrush>   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [Vue d'ensemble du multimédia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)