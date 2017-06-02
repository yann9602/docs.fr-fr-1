---
title: "Comment&#160;: d&#233;finir la taille de la mosa&#239;que pour un TileBrush | Microsoft Docs"
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
  - "TileBrush, taille des mosaïques"
  - "Viewport (propriété de TileBrush)"
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir la taille de la mosa&#239;que pour un TileBrush
Cet exemple montre comment définir la taille de la mosaïque pour un <xref:System.Windows.Media.TileBrush>.  Par défaut, un <xref:System.Windows.Media.TileBrush> produit une seule mosaïque qui remplit complètement la zone que vous peignez.  Vous pouvez substituer ce comportement en définissant les propriétés <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>.  
  
 La propriété <xref:System.Windows.Media.TileBrush.Viewport%2A> spécifie la taille de la mosaïque pour un <xref:System.Windows.Media.TileBrush>.  Par défaut, la valeur de la propriété <xref:System.Windows.Media.TileBrush.Viewport%2A> est relative à la taille de la zone qui est peinte.  Pour que la propriété <xref:System.Windows.Media.TileBrush.Viewport%2A> spécifie une taille de mosaïque absolue, affectez à la propriété <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> la valeur <xref:System.Windows.Media.BrushMappingMode>.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.ImageBrush>, un type de <xref:System.Windows.Media.TileBrush>, pour peindre un rectangle avec des mosaïques.  L'exemple définit chaque mosaïque à 50 % par 50 % de la zone de sortie \(le rectangle\).  Par conséquent, le rectangle est peint avec quatre projections de l'image.  
  
 L'illustration suivante montre la sortie produite par l'exemple.  
  
 ![Exemple de mosaïque avec un pinceau image](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 L'exemple suivant crée un <xref:System.Windows.Media.ImageBrush>, affecte à son <xref:System.Windows.Media.TileBrush.Viewport%2A> la valeur `0,0,25,25` et à son <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> la valeur <xref:System.Windows.Media.BrushMappingMode>, et l'utilise pour peindre un autre rectangle.  Par conséquent, le pinceau produit des mosaïques d'une largeur de 25 [pixels](GTMT) et d'une hauteur de 25 [pixels](GTMT).  
  
 L'illustration suivante montre la sortie produite par l'exemple.  
  
 ![TileBrush en mosaïque avec fenêtre d'affichage de 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Les exemples précédents font partie d'un exemple plus complet.  Pour l'exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Bien que cet exemple utilise la classe <xref:System.Windows.Media.ImageBrush>, les propriétés <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> se comportent de la même façon pour les autres objets <xref:System.Windows.Media.TileBrush>, c'est\-à\-dire pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.  Pour plus d'informations sur <xref:System.Windows.Media.ImageBrush> et les autres objets <xref:System.Windows.Media.TileBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.TileBrush>   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Créer différents modèles de mosaïque avec un TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)