---
title: "Comment&#160;: ajouter une valeur de sortie d&#39;animation &#224; une valeur de d&#233;part d&#39;animation | Microsoft Docs"
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
  - "animation"
  - "IsAdditive (propriété)"
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter une valeur de sortie d&#39;animation &#224; une valeur de d&#233;part d&#39;animation
Cet exemple indique comment ajouter une valeur de sortie d'animation à une valeur de départ d'animation.  
  
## Exemple  
 La propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> spécifie si vous souhaitez que la valeur de sortie d'une animation soit ajoutée à la valeur de départ \(valeur de base\) d'une propriété animée.  Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> avec la plupart des animations de base et des animations d'image clé.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 L'exemple suivant montre l'effet de l'utilisation de la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=fullName> avec <xref:System.Windows.Media.Animation.DoubleAnimation> et l'effet de l'utilisation de la propriété <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=fullName> avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## Voir aussi  
 [Accumuler des valeurs d'animation pendant des cycles de répétition](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)