---
title: "Comment&#160;: animer un point &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, objets Point avec des images clés"
  - "images clés, animer des objets Points avec"
  - "Points, animer avec des images clés"
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: animer un point &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> pour animer un <xref:System.Windows.Point>.  
  
## Exemple  
 L'exemple suivant déplace une ellipse le long d'un tracé triangulaire.  L'exemple utilise la classe <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A> d'un <xref:System.Windows.Media.EllipseGeometry>.  Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant la première demi\-seconde, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearPointKeyFrame> pour déplacer l'ellipse le long d'un tracé , à une vitesse constante, depuis sa position de départ.  Les images clés linéaires comme <xref:System.Windows.Media.Animation.LinearPointKeyFrame> créent une interpolation linéaire fluide entre les valeurs.  
  
2.  À la fin de la demi\-seconde suivante, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> pour déplacer soudainement l'ellipse le long du tracé vers la position suivante.  Les images clés discrètes comme <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> créent des sauts soudains entre les valeurs.  
  
3.  Durant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplinePointKeyFrame> pour ramener l'ellipse à sa position de départ.  Des images clé [spline](GTMT) telles que <xref:System.Windows.Media.Animation.SplinePointKeyFrame> créent une transition variable entre des valeurs en fonction des valeurs de la propriété <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>.  Dans cet exemple, l'animation commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Pour des raisons de cohérence avec d'autres exemples d'animation, les versions de code de cet exemple utilisent un objet <xref:System.Windows.Media.Animation.Storyboard> pour appliquer <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.  Toutefois, lors de l'application d'une seule animation dans le code, il est plus simple d'utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> qu'un <xref:System.Windows.Media.Animation.Storyboard>.  Pour obtenir un exemple, consultez [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.EllipseGeometry>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)