---
title: "Comment&#160;: animer une couleur &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, couleurs avec des images clés"
  - "couleurs, animer avec des images clés"
  - "images clés, animer les couleurs avec"
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: animer une couleur &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple indique comment animer la <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush>.  Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant les deux premières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearColorKeyFrame> pour modifier progressivement la couleur du vert au rouge.  Les images clés linéaires telles que <xref:System.Windows.Media.Animation.LinearColorKeyFrame> créent une transition linéaire fluide entre les valeurs.  
  
2.  À la fin de la demi\-seconde suivante, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> pour modifier rapidement la couleur du rouge au jaune.  Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> créent des modifications soudaines entre les valeurs, c'est\-à\-dire que la modification de couleur dans cette partie de l'animation se produit rapidement et n'est pas subtile.  
  
3.  Pendant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplineColorKeyFrame> pour modifier à nouveau la couleur — du jaune au vert, cette fois\-ci.  Des images clé [spline](GTMT) telles que <xref:System.Windows.Media.Animation.SplineColorKeyFrame> créent une transition variable entre des valeurs en fonction des valeurs de la propriété <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>.  Dans cet exemple, la modification de couleur commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>   
 <xref:System.Windows.Media.SolidColorBrush>   
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)