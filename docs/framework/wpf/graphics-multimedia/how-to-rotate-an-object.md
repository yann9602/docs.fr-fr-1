---
title: "Comment&#160;: faire pivoter un objet | Microsoft Docs"
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
  - "graphiques, faire pivoter des objets"
  - "faire pivoter des objets"
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: faire pivoter un objet
Cet exemple montre comment faire pivoter un objet.  L'exemple crée d'abord un <xref:System.Windows.Media.RotateTransform>, puis spécifie son <xref:System.Windows.Media.RotateTransform.Angle%2A> en degrés.  
  
 L'exemple suivant fait pivoter un objet <xref:System.Windows.Shapes.Polyline> à 45 degrés par rapport à son angle supérieur gauche.  
  
## Exemple  
 [!code-xml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 Les propriétés <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> du <xref:System.Windows.Media.RotateTransform> spécifient le point par rapport auquel l'objet pivote.  Ce point central est exprimé dans l'espace de coordonnées de l'élément qui est transformé.  Par défaut, la rotation est appliquée à \(0,0\), qui est l'angle supérieur gauche de l'objet à transformer.  
  
 L'exemple suivant fait pivoter un objet <xref:System.Windows.Shapes.Polyline> dans le sens des aiguilles d'une montre à 45 degrés par rapport au point \(25,50\).  
  
 [!code-xml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 L'illustration suivante montre les résultats de l'application d'un <xref:System.Windows.Media.Transform> aux deux objets.  
  
 ![Rotations de 45 degrés avec différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
Deux objets qui pivotent à 45 degrés à partir de centres de rotation différents  
  
 La <xref:System.Windows.Shapes.Polyline> des exemples précédents est un <xref:System.Windows.UIElement>.  Lorsque vous appliquez un <xref:System.Windows.Media.Transform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> d'un <xref:System.Windows.UIElement>, vous pouvez utiliser la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> pour spécifier une origine pour chaque <xref:System.Windows.Media.Transform> que vous appliquez à l'élément.  Étant donné que la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> utilise des coordonnées relatives, vous pouvez appliquer une transformation au centre de l'élément même si vous ne connaissez pas sa taille.  Pour plus d'informations et pour obtenir un exemple, consultez [Spécifier l'origine d'une transformation à l'aide de valeurs relatives](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Pour l'exemple complet, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)