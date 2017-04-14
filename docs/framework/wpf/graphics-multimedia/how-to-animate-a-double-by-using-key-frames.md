---
title: "Comment&#160;: animer un double &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, doubles avec des images clés"
  - "Doubles, animer avec des images clés"
  - "images clés, animer des doubles avec"
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: animer un double &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment animer la valeur d'une propriété qui accepte un <xref:System.Double> en utilisant des images clés.  
  
## Exemple  
 L'exemple suivant déplace un rectangle sur un écran.  L'exemple utilise la classe <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> d'un <xref:System.Windows.Media.TranslateTransform> appliqué à un <xref:System.Windows.Shapes.Rectangle>.  Cette animation, répétée indéfiniment, utilise trois images clés de la manière suivante :  
  
1.  Pendant les trois premières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> pour déplacer le rectangle le long d'un tracé, à une vitesse constante, de sa position de départ à la position 500.  Les images clés linéaires comme <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> créent une transition linéaire fluide entre les valeurs.  
  
2.  Au bout de la quatrième seconde, utilise une instance de la classe <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> pour déplacer soudainement le rectangle à la position suivante.  Les images clés discrètes comme <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> créent des sauts soudains entre les valeurs.  Dans cet exemple, le rectangle est à la position de départ, puis apparaît soudainement à la position 500.  
  
3.  Durant les deux dernières secondes, utilise une instance de la classe <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> pour ramener le rectangle à sa position de départ.  Des images clé [spline](GTMT) comme <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> créent une transition variable entre des valeurs en fonction de la valeur de la propriété <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>.  Dans cet exemple, le rectangle commence par se déplacer lentement, puis accélère de façon exponentielle vers la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Pour des raisons de cohérence avec d'autres exemples d'animation, les versions de code de cet exemple utilisent un objet <xref:System.Windows.Media.Animation.Storyboard> pour appliquer les <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  Autrement, lors de l'application d'une seule animation dans le code, il est plus simple d'utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> qu'un <xref:System.Windows.Media.Animation.Storyboard>.  Pour obtenir un exemple, consultez [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Shapes.Rectangle>   
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)