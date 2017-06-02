---
title: "Comment&#160;: lire le m&#233;dia avec des animations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "lecture multimédia, avec des animations"
  - "lecture de médias, avec des animations"
  - "animation, la lecture du média avec"
  - "support, lecture avec des animations"
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: lire le m&#233;dia avec des animations
Cet exemple montre comment lire un média et des animations en même temps à l’aide de la <xref:System.Windows.Media.MediaTimeline> et <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes dans le même <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser un ou plusieurs <xref:System.Windows.Media.MediaTimeline> des objets dans une <xref:System.Windows.Media.Animation.Storyboard> ainsi que d’autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que des animations.  
  
 L’exemple suivant définit les <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> propriété de la <xref:System.Windows.Media.Animation.Storyboard> sur la valeur `Slip`, qui spécifie que l’animation ne progresse pas tant que la progression multimédia (vidéo dans cet exemple). Cette fonctionnalité peut être nécessaire si la lecture du média est retardée en raison du temps de chargement.  
  
 [!code-xml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>   
 [Rubriques "Comment"](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [Vue d’ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Vue d’ensemble des Animations d’image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)