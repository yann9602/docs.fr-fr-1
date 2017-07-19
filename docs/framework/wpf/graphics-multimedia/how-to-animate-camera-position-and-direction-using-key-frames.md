---
title: "Comment&#160;: animer la position et la direction d&#39;une cam&#233;ra &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, direction d'une caméra avec des images clés"
  - "animation, position d'une caméra avec des images clés"
  - "direction d'une caméra, animer avec des images clés"
  - "position d'une caméra, animer avec des images clés"
  - "images clés, animer la direction d'une caméra"
  - "images clés, animer la position d'une caméra"
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: animer la position et la direction d&#39;une cam&#233;ra &#224; l&#39;aide d&#39;images cl&#233;s
Dans l'exemple suivant, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> est utilisé pour animer la position d'une <xref:System.Windows.Media.Media3D.PerspectiveCamera> dans une scène 3D.  De plus, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> est utilisé pour animer la direction sur laquelle pointe la caméra dans la scène 3D.  Ces deux animations utilisent plusieurs images clés qui créent une série d'effets d'animation :  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> et <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> sont utilisés pour créer une interpolation linéaire fluide entre les valeurs.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> et <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> sont utilisés pour créer des "sauts" soudains entre les valeurs \(aucune interpolation\).  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> et <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> sont utilisés pour créer une transition variable entre les valeurs en fonction de la propriété <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>.  Dans l'exemple ci\-dessous, l'animation commence lentement et accélère de façon exponentielle vers la fin du segment temporel.  
  
## Exemple  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## Voir aussi  
 [Animer la position et la direction d'une caméra dans une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)