---
title: "Comment&#160;: mettre &#224; l&#39;&#233;chelle un &#233;l&#233;ment | Microsoft Docs"
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
  - "classes, ScaleTransform"
  - "graphiques, mettre à l'échelle des éléments"
  - "ScaleTransform (classe)"
  - "mettre à l'échelle, éléments"
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: mettre &#224; l&#39;&#233;chelle un &#233;l&#233;ment
Cet exemple montre comment utiliser un <xref:System.Windows.Media.ScaleTransform> pour mettre à l'échelle un élément.  
  
 Utilisez les propriétés <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> pour redimensionner l'élément selon le facteur spécifié.  Par exemple, une valeur <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> de 1.5 étire l'élément à 150 % de sa largeur d'origine.  Une valeur <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> de 0.5 diminue la hauteur d'un élément de 50 %.  
  
 Utilisez les propriétés <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A> pour spécifier le point correspondant au centre de l'opération de mise à l'échelle.  Par défaut, un <xref:System.Windows.Media.ScaleTransform> est centré au point \(0,0\), c'est\-à\-dire à l'angle supérieur gauche du rectangle.  L'élément est ainsi déplacé et paraît plus grand, car lorsque vous appliquez un <xref:System.Windows.Media.Transform>, vous modifiez l'espace de coordonnées dans lequel l'objet réside.  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.ScaleTransform> pour doubler la taille d'un <xref:System.Windows.Shapes.Rectangle> de 50 par 50.  Le <xref:System.Windows.Media.ScaleTransform> a une valeur de 0 \(la valeur par défaut\) pour <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## Exemple  
 [!code-xml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 En général, vous définissez <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A> sur le centre de l'objet mis à l'échelle : \(<xref:System.Windows.FrameworkElement.Width%2A>\/2, <xref:System.Windows.FrameworkElement.Height%2A>\/2\).  
  
 L'exemple suivant affiche un autre <xref:System.Windows.Shapes.Rectangle> dont la taille est doublée. Toutefois, ce <xref:System.Windows.Media.ScaleTransform> a une valeur de 25 pour <xref:System.Windows.Media.ScaleTransform.CenterX%2A> et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, ce qui correspond au centre du rectangle.  
  
 [!code-xml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 L'illustration suivante montre la différence entre les deux opérations <xref:System.Windows.Media.ScaleTransform>.  La ligne en pointillés affiche la taille et la position du rectangle avant la mise à l'échelle.  
  
 ![Échelles de 2x avec différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.png "wcpsdk\_graphicsmm\_scalecenter")  
Deux opérations ScaleTransform avec valeurs ScaleX et ScaleY identiques, mais centres différents  
  
 Pour l'exemple complet, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)