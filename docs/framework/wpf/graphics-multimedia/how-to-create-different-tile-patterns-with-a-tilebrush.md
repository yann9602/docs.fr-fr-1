---
title: "Comment&#160;: cr&#233;er diff&#233;rents mod&#232;les de mosa&#239;que avec un TileBrush | Microsoft Docs"
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
  - "créer, modèles de mosaïque avec TileBrush"
  - "modèles de mosaïque, créer"
  - "TileBrush, modèles de mosaïque"
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er diff&#233;rents mod&#232;les de mosa&#239;que avec un TileBrush
Cet exemple montre comment utiliser la propriété <xref:System.Windows.Media.TileBrush.TileMode%2A> d'un <xref:System.Windows.Media.TileBrush> pour créer un modèle.  
  
 La propriété <xref:System.Windows.Media.TileBrush.TileMode%2A> vous permet de spécifier la manière dont le contenu d'un <xref:System.Windows.Media.TileBrush> est répété, c'est\-à\-dire disposé en mosaïque pour remplir une zone de sortie.  Pour créer un modèle, le <xref:System.Windows.Media.TileBrush.TileMode%2A> doit avoir la valeur <xref:System.Windows.Media.TileMode>, <xref:System.Windows.Media.TileMode>, <xref:System.Windows.Media.TileMode> ou <xref:System.Windows.Media.TileMode>.  Vous devez également définir la <xref:System.Windows.Media.TileBrush.Viewport%2A> du <xref:System.Windows.Media.TileBrush> afin qu'elle soit plus petite que la zone que vous peignez ; sinon, une seule mosaïque est produite, quel que soit le paramètre <xref:System.Windows.Media.TileBrush.TileMode%2A> que vous utilisez.  
  
## Exemple  
 L'exemple suivant crée cinq objets <xref:System.Windows.Media.DrawingBrush>, puis donne à chacun un paramètre <xref:System.Windows.Media.TileBrush.TileMode%2A> différent et les utilise pour peindre cinq rectangles.  Bien que cet exemple utilise la classe <xref:System.Windows.Media.DrawingBrush> pour montrer le comportement <xref:System.Windows.Media.TileBrush.TileMode%2A>, la propriété <xref:System.Windows.Media.TileBrush.TileMode%2A> fonctionne de la même manière pour tous les objets <xref:System.Windows.Media.TileBrush>, c'est\-à\-dire pour <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush> et <xref:System.Windows.Media.DrawingBrush>.  
  
 L'illustration suivante montre la sortie produite par cet exemple.  
  
 ![Exemple de sortie en mosaïque de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm\_DrawingBrushTileModeExample")  
Modèles de mosaïque créés avec la propriété TileMode  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## Voir aussi  
 [Définir la taille de la mosaïque pour un TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)