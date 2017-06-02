---
title: "Comment&#160;: animer l&#39;&#233;paisseur d&#39;une bordure &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, épaisseur d'une bordure avec des images clés"
  - "épaisseur d'une bordure, animer avec des images clés"
  - "images clés, animer l'épaisseur d'une bordure avec"
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: animer l&#39;&#233;paisseur d&#39;une bordure &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment animer la propriété <xref:System.Windows.Controls.Control.BorderThickness%2A> d'un <xref:System.Windows.Controls.Border>.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Controls.Control.BorderThickness%2A> d'un <xref:System.Windows.Controls.Border>.  Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant la première demi\-seconde, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> pour augmenter progressivement l'épaisseur de la bordure.  L'exemple utilise <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> pour créer une augmentation linéaire fluide entre les valeurs.  
  
2.  Au bout de la demi\-seconde suivante, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> pour augmenter soudainement l'épaisseur de la bordure.  Les images clés discrètes comme celles dérivées de <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> créent des sauts soudains entre les valeurs ; autrement dit, le mouvement de l'animation est saccadé.  
  
3.  Pendant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> pour réduire l'épaisseur de la bordure.  Des images clé [Spline](GTMT) telles que celles dérivées de <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> créent une transition variable entre des valeurs en fonction des valeurs de la propriété <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>.  Dans cette image clé, l'animation commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
 [!code-xml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [Animer une valeur BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)