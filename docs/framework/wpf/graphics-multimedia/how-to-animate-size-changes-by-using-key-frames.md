---
title: "Comment&#160;: animer des modifications de taille &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, modifications de taille avec des images clés"
  - "images clés, animer des modifications de taille avec"
  - "modifications de taille, animer avec des images clés"
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer des modifications de taille &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple indique comment animer des modifications de taille à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.ArcSegment.Size%2A> d'un <xref:System.Windows.Media.ArcSegment>.  Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant la première demi\-seconde de l'animation, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> pour augmenter progressivement la taille de l'arc.  Les images clés linéaires telles que <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> créent une transition linéaire fluide entre les valeurs.  
  
2.  Au bout de la demi\-seconde suivante, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> pour augmenter soudainement la taille de l'arc.  Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> créent des sauts soudains entre les valeurs, c'est\-à\-dire que les modifications de taille se produisent soudainement et ne sont pas subtiles.  
  
3.  Pendant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> pour augmenter la taille de l'arc.  Des images clé [spline](GTMT) telles que <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> créent une transition variable entre des valeurs en fonction des valeurs de la propriété <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>.  Dans cet exemple, la taille de l'arc augmente d'abord lentement, puis augmente de façon exponentielle vers la fin du segment temporel.  
  
 [!code-xml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.ArcSegment.Size%2A>   
 <xref:System.Windows.Media.ArcSegment>   
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)