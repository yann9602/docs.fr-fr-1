---
title: "Comment : créer différents modèles de mosaïque avec un TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Comment : créer différents modèles de mosaïque avec un TileBrush
Cet exemple montre comment utiliser le <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété d’un <xref:System.Windows.Media.TileBrush> pour créer un modèle.  
  
 Le <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété vous permet de spécifier comment le contenu d’un <xref:System.Windows.Media.TileBrush> est répété, autrement dit, en mosaïque pour remplir une zone de sortie. Pour créer un modèle, vous définissez la <xref:System.Windows.Media.TileBrush.TileMode%2A> à <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, ou <xref:System.Windows.Media.TileMode.FlipXY>. Vous devez également définir le <xref:System.Windows.Media.TileBrush.Viewport%2A> de la <xref:System.Windows.Media.TileBrush> afin qu’elle soit inférieure à la zone qui vous sont en train de peindre ; sinon, uniquement une seule vignette est produite, quel que soit ce qui <xref:System.Windows.Media.TileBrush.TileMode%2A> paramètre que vous utilisez.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée cinq <xref:System.Windows.Media.DrawingBrush> des objets, chacun donne une autre <xref:System.Windows.Media.TileBrush.TileMode%2A> définition et les utilise pour peindre cinq rectangles. Bien que cet exemple utilise le <xref:System.Windows.Media.DrawingBrush> pour illustrer <xref:System.Windows.Media.TileBrush.TileMode%2A> comportement, le <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété fonctionne de manière identique pour tous les le <xref:System.Windows.Media.TileBrush> des objets, autrement dit, pour <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, et <xref:System.Windows.Media.DrawingBrush>.  
  
 L’illustration suivante montre la sortie que l’exemple génère.  
  
 ![Exemple de sortie de la mosaïque de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Modèles de mosaïque créés avec la propriété TileMode  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Voir aussi  
 [Définir la taille de la mosaïque pour un TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
