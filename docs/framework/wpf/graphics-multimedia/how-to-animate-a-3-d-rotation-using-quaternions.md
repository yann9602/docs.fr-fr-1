---
title: "Comment&#160;: animer une rotation 3D &#224; l&#39;aide de quaternions | Microsoft Docs"
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
  - "translations 3D, animer, avec des quaternions"
  - "animation, translations 3D, avec des quaternions"
  - "quaternions"
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: animer une rotation 3D &#224; l&#39;aide de quaternions
Cet exemple montre comment animer une rotation d'objet 3D à l'aide de quaternions.  
  
 Dans le code suivant, <xref:System.Windows.Media.Media3D.QuaternionRotation3D> est utilisé comme valeur pour la propriété <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> d'un <xref:System.Windows.Media.Media3D.RotateTransform3D>.  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Ce <xref:System.Windows.Media.Media3D.QuaternionRotation3D> est animé à l'aide d'un <xref:System.Windows.Media.Animation.QuaternionAnimation> dans un <xref:System.Windows.Media.Animation.Storyboard> au moyen du code ci\-dessous.  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## Exemple  
 Le code suivant montre l'exemple complet.  
  
 [!code-xml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Animer une rotation 3D à l'aide de storyboards](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)   
 [Animer une rotation 3D à l'aide de Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)