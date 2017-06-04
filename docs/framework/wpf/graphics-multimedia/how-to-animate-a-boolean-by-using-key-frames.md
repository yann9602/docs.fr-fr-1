---
title: "Comment&#160;: animer une valeur bool&#233;enne &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, valeurs booléennes avec des images clés"
  - "valeurs booléennes, animer avec des images clés"
  - "images clés, animer des valeurs booléennes avec"
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer une valeur bool&#233;enne &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment animer la valeur de propriété booléenne d'un contrôle <xref:System.Windows.Controls.Button> à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.UIElement.IsEnabled%2A> d'un contrôle <xref:System.Windows.Controls.Button>.  Toutes les images clés de cet exemple utilisent une instance de la classe <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>.  Les images clés discrètes comme <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> créent des sauts soudains entre les valeurs ; autrement dit, le mouvement de l'animation est saccadé.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>   
 <xref:System.Windows.UIElement.IsEnabled%2A>   
 <xref:System.Windows.Controls.Button>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)