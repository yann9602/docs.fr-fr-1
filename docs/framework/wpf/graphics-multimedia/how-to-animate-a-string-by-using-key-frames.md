---
title: "Comment&#160;: animer une cha&#238;ne &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, chaînes avec des images clés"
  - "images clés, animer des chaînes avec"
  - "chaînes, animer avec des images clés"
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer une cha&#238;ne &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment animer une chaîne qui, dans cet exemple, est la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> d'un contrôle <xref:System.Windows.Controls.Button> à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> pour animer la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.Button>.  
  
 Toutes les images clés de cet exemple utilisent une instance de la classe <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> car une animation de chaîne créée avec des images clés peut uniquement utiliser des images clés discrètes.  Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> créent des sauts soudains entre les valeurs ; autrement dit, les modifications apportées à l'animation ne sont pas subtiles et se produisent rapidement.  
  
 [!code-xml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.ContentControl.Content%2A>   
 <xref:System.Windows.Controls.Button>   
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)