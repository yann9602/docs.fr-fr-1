---
title: "Comment&#160;: animer une rotation 3D &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "translations 3D, animer, avec des images clés (Rotation3DAnimation)"
  - "animation, translations 3D, avec des images clés (Rotation3DAnimation)"
  - "images clés, Rotation3DAnimation"
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: animer une rotation 3D &#224; l&#39;aide d&#39;images cl&#233;s
Dans l'exemple suivant, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> est utilisé pour faire pivoter un objet en 3D pendant que son axe de rotation s'anime en créant une "déviation".  Cette animation utilise les images clés suivantes :  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> est utilisé pour créer une interpolation linéaire fluide entre les valeurs.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> est utilisé pour créer des "sauts" soudains entre les valeurs \(aucune interpolation\).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> est utilisé pour créer une transition variable entre les valeurs en fonction de la propriété <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A>.  Dans l'exemple ci\-dessous, cette partie de l'animation commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
## Exemple  
 [!code-xml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## Voir aussi  
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Animer une rotation 3D à l'aide de storyboards](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [Animer une rotation 3D à l'aide de Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [Animer une rotation 3D à l'aide de quaternions](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)   
 [Animer une rotation 3D à l'aide d'images clés \(QuaternionAnimationUsingKeyFrames\)](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)