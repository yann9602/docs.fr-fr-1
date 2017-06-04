---
title: "Comment&#160;: animer une g&#233;om&#233;trie rectangle &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, objets RectangleGeometry avec des images clés"
  - "images clés, animer des objets RectangleGeometry avec"
  - "objets RectangleGeometry, animer avec des images clés"
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: animer une g&#233;om&#233;trie rectangle &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple indique comment animer la propriété <xref:System.Windows.Media.RectangleGeometry.Rect%2A> d'un <xref:System.Windows.Media.RectangleGeometry> à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.RectangleGeometry.Rect%2A> d'un <xref:System.Windows.Media.RectangleGeometry>.  Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant les deux premières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearRectKeyFrame> pour animer une modification graduelle de la position, de la largeur et de la hauteur d'un rectangle.  Les images clés linéaires telles que <xref:System.Windows.Media.Animation.LinearRectKeyFrame> créent une transition linéaire fluide entre les valeurs.  
  
2.  À la fin de la demi\-seconde suivante, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> pour diminuer soudainement la hauteur du rectangle.  Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> créent des modifications soudaines entre les valeurs, c'est\-à\-dire que la diminution de la hauteur se produit rapidement et n'est pas subtile.  
  
3.  Durant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplineRectKeyFrame> pour rétablir la taille et la position de départ du rectangle.  Des images clé [spline](GTMT) telles que <xref:System.Windows.Media.Animation.SplineRectKeyFrame> créent une transition variable entre des valeurs en fonction des valeurs de la propriété <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>.  Dans cet exemple, la modification commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.RectangleGeometry>   
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>   
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)