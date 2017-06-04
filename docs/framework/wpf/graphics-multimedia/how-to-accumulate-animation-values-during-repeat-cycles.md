---
title: "Comment&#160;: accumuler des valeurs d&#39;animation pendant des cycles de r&#233;p&#233;tition | Microsoft Docs"
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
  - "accumuler des valeurs d'animation pendant des cycles de répétition"
  - "animation, accumuler des valeurs pendant des cycles de répétition"
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: accumuler des valeurs d&#39;animation pendant des cycles de r&#233;p&#233;tition
Cet exemple montre comment utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> pour accumuler des valeurs d'animation sur des cycles de répétition.  
  
## Exemple  
 Utilisez la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> pour accumuler les valeurs de base d'une animation sur des cycles de répétition.  Par exemple, si vous définissez une animation de sorte qu'elle soit répétée 9 fois \(<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> \= « 9x »\) et que vous définissez l'animation de la propriété entre 10 et 15 \(De \= 10 À \= 15\), la propriété s'anime de 10 à 15 pendant le premier cycle, de 15 à 20 pendant le deuxième cycle, de 20 à 25 pendant le troisième cycle, et ainsi de suite.  De ce fait, chaque cycle d'animation utilise comme valeur de base la valeur finale de l'animation du cycle d'animation précédent.  
  
 Vous pouvez utiliser la propriété `IsCumulative` avec la plupart des animations de base et des animations d'image clé.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 L'exemple suivant présente ce comportement en animant la largeur de quatre rectangles.  L'exemple :  
  
-   anime le premier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> la valeur `true` ;  
  
-   anime le deuxième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> la valeur par défaut `false` ;  
  
-   anime le troisième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> la valeur `true` ;  
  
-   anime le dernier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> la valeur `false`.  
  
 [!code-xml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## Voir aussi  
 [Ajouter une valeur de sortie d'animation à une valeur de départ d'animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)   
 [Répéter une animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)