---
title: "Comment&#160;: animer une matrice &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, propriétés Matrix avec des images clés"
  - "images clés, animer des propriétés Matrix avec"
  - "propriétés Matrix, animer avec des images clés"
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: animer une matrice &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple indique comment animer la propriété <xref:System.Windows.Media.MatrixTransform.Matrix%2A> d'un <xref:System.Windows.Media.MatrixTransform> à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Media.MatrixTransform.Matrix%2A> d'un <xref:System.Windows.Media.MatrixTransform>.  L'exemple utilise l'objet <xref:System.Windows.Media.MatrixTransform> pour transformer l'apparence et la position d'un <xref:System.Windows.Controls.Button>.  
  
 Cette animation utilise la classe <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> pour créer deux images clés et effectue les opérations suivantes avec elles :  
  
1.  Anime la première <xref:System.Windows.Media.Matrix> pendant les 0,2 premières secondes.  L'exemple modifie les propriétés <xref:System.Windows.Media.Matrix.M11%2A> et <xref:System.Windows.Media.Matrix.M12%2A> de la <xref:System.Windows.Media.Matrix>.  À la suite de cette modification, le bouton s'étire et s'incline.  L'exemple modifie également les propriétés <xref:System.Windows.Media.Matrix.OffsetX%2A> et <xref:System.Windows.Media.Matrix.OffsetY%2A> afin que le bouton change de position.  
  
2.  Anime la deuxième <xref:System.Windows.Media.Matrix> à 1,0 seconde.  Le bouton se déplace à une autre position et n'est plus incliné ni étiré.  
  
3.  Répète l'animation indéfiniment.  
  
> [!NOTE]
>  Les images clés qui dérivent de l'objet <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> créent des sauts soudains entre les valeurs ; autrement dit, le mouvement de l'animation est saccadé.  
  
 [!code-xml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>   
 <xref:System.Windows.Media.MatrixTransform>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)