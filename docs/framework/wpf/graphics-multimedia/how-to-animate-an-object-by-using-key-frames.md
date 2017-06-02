---
title: "Comment&#160;: animer un objet &#224; l&#39;aide d&#39;images cl&#233;s | Microsoft Docs"
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
  - "animation, objets avec des images clés"
  - "images clés, animer des objets avec"
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: animer un objet &#224; l&#39;aide d&#39;images cl&#233;s
Cet exemple montre comment animer un objet qui, dans cet exemple, est la propriété <xref:System.Windows.Controls.Page.Background%2A> d'un contrôle <xref:System.Windows.Controls.Page>, à l'aide d'images clés.  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pour animer des modifications de couleur pour la propriété <xref:System.Windows.Controls.Page.Background%2A> d'un contrôle <xref:System.Windows.Controls.Page>.  L'exemple d'animation passe à un pinceau d'arrière\-plan différent à intervalles réguliers.  Cette animation utilise la classe <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> pour créer trois images clés différentes.  L'animation utilise des images clés de la manière suivante :  
  
1.  À la fin de la première seconde, anime une instance de la classe <xref:System.Windows.Media.LinearGradientBrush>.  Cette section de l'exemple applique un dégradé linéaire à la couleur d'arrière\-plan afin que la couleur passe du jaune au rouge en passant par le orange.  
  
2.  À la fin de la seconde suivante, anime une instance de la classe <xref:System.Windows.Media.RadialGradientBrush>.  Cette section de l'exemple applique un dégradé radial à la couleur d'arrière\-plan afin que la couleur passe du blanc au noir en passant par le bleu.  
  
3.  À la fin de la troisième seconde, anime une instance de la classe <xref:System.Windows.Media.DrawingBrush>.  Cette section de l'exemple applique un damier à l'arrière\-plan.  
  
4.  L'animation recommence et se répète indéfiniment.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> est le seul type d'image clé que vous pouvez utiliser avec la classe <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>.  Les images clés comme <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> créent des modifications soudaines dans les valeurs, c'est\-à\-dire que les modifications de couleur dans cet exemple se produisent soudainement.  
  
 [!code-xml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.Page.Background%2A>   
 <xref:System.Windows.Controls.Page>   
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>   
 <xref:System.Windows.Media.LinearGradientBrush>   
 <xref:System.Windows.Media.RadialGradientBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)