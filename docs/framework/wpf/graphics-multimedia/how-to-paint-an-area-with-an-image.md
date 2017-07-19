---
title: "Comment&#160;: peindre une zone avec une image | Microsoft Docs"
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
  - "pinceaux, peindre avec des images"
  - "images, peindre avec"
  - "peindre, avec des images"
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: peindre une zone avec une image
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.ImageBrush> pour peindre une zone avec une image.  Un <xref:System.Windows.Media.ImageBrush> affiche une seule image qui est spécifiée par sa propriété <xref:System.Windows.Media.ImageBrush.ImageSource%2A>.  
  
## Exemple  
 L'exemple suivant peint le <xref:System.Windows.Controls.Control.Background%2A> d'un bouton en utilisant un <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Par défaut, un <xref:System.Windows.Media.ImageBrush> étire son image pour remplir complètement la zone que vous peignez.  Dans l'exemple précédent, l'image est étirée pour remplir le bouton, en déformant éventuellement l'image.  Vous pouvez contrôler ce comportement en affectant à la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> de <xref:System.Windows.Media.TileBrush> la valeur <xref:System.Windows.Media.Stretch> ou <xref:System.Windows.Media.Stretch>, ce qui permet au pinceau de conserver les [proportions](GTMT) de l'image.  
  
 Si vous définissez les propriétés <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.TileMode%2A> d'un <xref:System.Windows.Media.ImageBrush>, vous pouvez créer un modèle répété.  L'exemple suivant peint un bouton en utilisant un modèle créé à partir d'une image.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Pour plus d'informations sur la classe <xref:System.Windows.Media.ImageBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Cet exemple de code fait partie d'un exemple plus complet fourni pour la classe <xref:System.Windows.Media.ImageBrush>.  Pour l'exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## Voir aussi  
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)