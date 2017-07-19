---
title: "Comment&#160;: sp&#233;cifier l&#39;origine d&#39;une transformation &#224; l&#39;aide de valeurs relatives | Microsoft Docs"
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
  - "graphiques, origines d'objets Transform"
  - "origines d'objets Transform"
  - "Transformations, origines de"
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: sp&#233;cifier l&#39;origine d&#39;une transformation &#224; l&#39;aide de valeurs relatives
Cet exemple montre comment utiliser des valeurs relatives pour spécifier l'origine d'un <xref:System.Windows.UIElement.RenderTransform%2A> appliqué à un <xref:System.Windows.FrameworkElement>.  
  
 Lorsque vous faites pivoter, mettez à l'échelle ou [inclinez](GTMT) un <xref:System.Windows.FrameworkElement> en utilisant la propriété <xref:System.Windows.UIElement.RenderTransform%2A>, le paramètre par défaut applique la transformation à l'angle supérieur gauche de l'élément.  Si vous souhaitez faire pivoter, mettre à l'échelle ou appliquer une inclinaison à partir du centre de l'élément, vous pouvez compenser en affectant au centre de la transformation le centre de l'élément.  Toutefois, cette solution requiert que vous connaissiez la taille de l'élément.  Une façon plus simple d'appliquer une transformation au centre d'un élément consiste à affecter à sa propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> les valeurs \(0.5, 0.5\), au lieu de définir une valeur de centre sur la transformation elle\-même.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un <xref:System.Windows.Controls.Button> à 45 degrés dans le sens des aiguilles d'une montre.  Étant donné que l'exemple ne spécifie pas de centre, le bouton pivote par rapport au point \(0, 0\), qui est son angle supérieur gauche.  Le <xref:System.Windows.Media.RotateTransform> est appliqué à la propriété <xref:System.Windows.UIElement.RenderTransform%2A>.  
  
 L'illustration suivante montre le résultat de la transformation pour l'exemple qui suit.  
  
 ![Bouton transformé à l'aide de RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
Rotation de 45 degrés dans le sens des aiguilles d'une montre à l'aide de la propriété RenderTransform  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 L'exemple suivant utilise également un <xref:System.Windows.Media.RotateTransform> pour faire pivoter un <xref:System.Windows.Controls.Button> de 45 degrés dans le sens des aiguilles d'une montre. Toutefois, cet exemple affecte au <xref:System.Windows.UIElement.RenderTransformOrigin%2A> du bouton les valeurs \(0.5, 0.5\).  Par conséquent, la rotation est appliquée au centre du bouton, plutôt qu'à l'angle supérieur gauche.  
  
 L'illustration suivante montre le résultat de la transformation pour l'exemple qui suit.  
  
 ![Bouton transformé autour de son centre](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
Rotation de 45 degrés à l'aide de la propriété RenderTransform avec un RenderTransformOrigin de \(0.5, 0.5\)  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Pour plus d'informations sur la transformation d'objets <xref:System.Windows.FrameworkElement>, consultez [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)