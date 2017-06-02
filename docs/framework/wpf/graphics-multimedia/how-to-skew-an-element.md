---
title: "Comment&#160;: incliner un &#233;l&#233;ment | Microsoft Docs"
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
  - "classes, SkewTransform"
  - "graphiques, incliner des éléments"
  - "incliner des éléments"
  - "SkewTransform (classe)"
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: incliner un &#233;l&#233;ment
Cet exemple montre comment utiliser un <xref:System.Windows.Media.SkewTransform> pour incliner un élément.  Une [inclinaison](GTMT) est une transformation qui étire l'espace de coordonnées de façon non uniforme.  L'une des utilisations types d'un <xref:System.Windows.Media.SkewTransform> est la simulation d'une profondeur [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] dans des objets [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)].  
  
 Utilisez les propriétés <xref:System.Windows.Media.SkewTransform.CenterX%2A> et <xref:System.Windows.Media.SkewTransform.CenterY%2A> pour spécifier le point central du <xref:System.Windows.Media.SkewTransform>.  
  
 Utilisez les propriétés <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> pour spécifier l'angle d'inclinaison de l'axe x et de l'axe y, et pour incliner le système de coordonnées actuel le long de ces axes.  
  
 Pour prévoir l'effet d'une transformation d'inclinaison, considérez que l'<xref:System.Windows.Media.SkewTransform.AngleX%2A> incline les valeurs de l'axe x par rapport au système de coordonnées d'origine.  Par conséquent, pour un <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, l'axe y pivote de 30 degrés via l'origine et incline les valeurs x de 30 degrés par rapport à cette origine.  De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 incline les valeurs y de la forme de 30 degrés par rapport à l'origine.  Notez que l'effet n'est pas le même que pour un déplacement du système de coordonnées de 30 degrés en x ou y.  
  
 L'exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d'un point central \(0,0\).  
  
## Exemple  
 [!code-xml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 L'exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d'un point central \(25,25\).  
  
 [!code-xml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 L'exemple suivant applique une inclinaison verticale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d'un point central \(25,25\).  
  
 [!code-xml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 L'illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.  
  
 ![Exemples de SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.png "img\_wcpsdk\_graphicsmm\_skewtransformexample")  
Les trois exemples SkewTransform illustrés  
  
 Pour l'exemple complet, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.SkewTransform>   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)