---
title: "Comment&#160;: animer une rotation 3D &#224; l&#39;aide d&#39;images cl&#233;s (QuaternionAnimationUsingKeyFrames) | Microsoft Docs"
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
  - "translations 3D, animer, avec des images clés (QuaternionAnimationUsingKeyFrames)"
  - "animation, translations 3D, avec des images clés (QuaternionAnimationUsingKeyFrames)"
  - "images clés, QuaternionAnimationUsingKeyFrames"
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: animer une rotation 3D &#224; l&#39;aide d&#39;images cl&#233;s (QuaternionAnimationUsingKeyFrames)
Dans l'exemple suivant, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> est utilisé pour faire pivoter un objet 3D.  Cette animation utilise les images clés suivantes :  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> est utilisé pour créer une interpolation linéaire fluide entre les valeurs.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> est utilisé pour créer des "sauts" soudains entre les valeurs \(aucune interpolation\).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> est utilisé pour créer une transition variable entre les valeurs en fonction de la propriété <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>.  Dans l'exemple ci\-dessous, cette partie de l'animation commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
## Exemple  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## Voir aussi  
 [Animer une rotation 3D à l'aide de storyboards](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [Animer une rotation 3D à l'aide de Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [Animer une rotation 3D à l'aide de quaternions](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)   
 [Animer une rotation 3D à l'aide d'images clés \(Rotation3DAnimationUsingKeyFrames\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)