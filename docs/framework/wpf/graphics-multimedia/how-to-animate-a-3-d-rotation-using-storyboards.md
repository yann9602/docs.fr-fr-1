---
title: "Comment&#160;: animer une rotation 3D &#224; l&#39;aide de storyboards | Microsoft Docs"
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
  - "translations 3D, animer, avec des storyboards"
  - "animation, translations 3D, avec des storyboards"
  - "Animations"
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: animer une rotation 3D &#224; l&#39;aide de storyboards
L'exemple suivant indique comment faire pivoter un objet 3D pendant une déviation en animant les propriétés <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> et <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> d'un objet <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>.  Cet objet <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> spécifie la transformation de rotation de l'objet 3D et en animant ainsi ses propriétés, crée l'effet de rotation souhaité.  Dans la table de montage séquentiel, <xref:System.Windows.Media.Animation.DoubleAnimation> est utilisé pour animer la propriété <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> pendant que <xref:System.Windows.Media.Animation.Vector3DAnimation> est utilisé pour animer la propriété <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>.  
  
## Exemple  
 [!code-xml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## Voir aussi  
 [Animer une rotation 3D à l'aide de Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)   
 [Animer une rotation 3D à l'aide d'images clés \(Rotation3DAnimationUsingKeyFrames\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)