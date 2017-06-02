---
title: "Comment&#160;: arrondir les angles d&#39;un RectangleGeometry | Microsoft Docs"
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
  - "angles, arrondir"
  - "graphiques, arrondir les angles d'objets RectangleGeometry"
  - "RectangleGeometry (classe), arrondir les angles"
  - "arrondir les angles d'objets RectangleGeometry"
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: arrondir les angles d&#39;un RectangleGeometry
Pour arrondir les angles d'un <xref:System.Windows.Media.RectangleGeometry>, affectez une valeur supérieure à zéro à ses propriétés <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> et <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>.  Plus les valeurs sont grandes, plus les angles du rectangle sont arrondis.  
  
## Exemple  
 L'exemple suivant montre plusieurs objets <xref:System.Windows.Media.RectangleGeometry> avec des paramètres <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> et <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> différents.  Les objets <xref:System.Windows.Media.RectangleGeometry> sont affichés à l'aide d'éléments <xref:System.Windows.Shapes.Path>.  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Rectangles avec différents paramètres RadiusX&#47;RadiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm\_rounded")  
Rectangles à angles arrondis  
  
## Voir aussi  
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)