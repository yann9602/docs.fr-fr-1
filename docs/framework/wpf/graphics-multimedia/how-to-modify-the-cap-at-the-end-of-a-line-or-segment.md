---
title: "Comment&#160;: modifier l&#39;embout &#224; la fin d&#39;une ligne ou d&#39;un segment | Microsoft Docs"
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
  - "graphiques, Shape (embouts de)"
  - "éléments Shape, embouts"
  - "éléments Shape, extrémités"
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: modifier l&#39;embout &#224; la fin d&#39;une ligne ou d&#39;un segment
Cet exemple montre comment modifier la forme au début ou à la fin d'un élément <xref:System.Windows.Shapes.Shape> ouvert.  Pour modifier l'embout au début d'une <xref:System.Windows.Shapes.Shape> ouverte, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>.  Pour modifier l'embout à la fin d'une <xref:System.Windows.Shapes.Shape> ouverte, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>.  Pour afficher les embouts de ligne disponibles, consultez l'énumération <xref:System.Windows.Media.PenLineCap>.  
  
> [!NOTE]
>  Cette propriété affecte uniquement une forme ouverte, telle qu'une <xref:System.Windows.Shapes.Line>, une <xref:System.Windows.Shapes.Polyline> ou un élément <xref:System.Windows.Shapes.Path> ouvert.  
  
 L'exemple suivant dessine quatre éléments <xref:System.Windows.Shapes.Polyline> et utilise un jeu de formes différent à la fin de chacun.  
  
## Exemple  
 [!code-xml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Media.PenLineCap>