---
title: "Comment&#160;: animer une propri&#233;t&#233; &#224; l&#39;aide d&#39;un AnimationClock | Microsoft Docs"
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
  - "animation, propriétés, avec AnimationClocks"
  - "AnimationClocks"
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: animer une propri&#233;t&#233; &#224; l&#39;aide d&#39;un AnimationClock
Cet exemple indique comment utiliser des objets <xref:System.Windows.Media.Animation.Clock> pour animer une propriété.  
  
 Il existe trois façons d'animer une [propriété de dépendance](GTMT) :  
  
-   Créez un <xref:System.Windows.Media.Animation.AnimationTimeline> et associez\-le à cette propriété en utilisant un <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> de l'objet pour appliquer un <xref:System.Windows.Media.Animation.AnimationTimeline> unique à une propriété cible.  
  
-   Créez un <xref:System.Windows.Media.Animation.AnimationClock> à partir d'un <xref:System.Windows.Media.Animation.AnimationTimeline> et appliquez\-le à une propriété.  
  
 Les objets <xref:System.Windows.Media.Animation.Storyboard> et la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> vous permettent d'animer des propriétés sans créer et distribuer directement des horloges \(pour obtenir des exemples, consultez [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) et [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)\). Les horloges sont créées et distribuées automatiquement pour vous.  
  
## Exemple  
 L'exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.AnimationClock> et l'appliquer à deux propriétés similaires.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Pour obtenir un exemple qui indique comment contrôler un <xref:System.Windows.Media.Animation.Clock> interactivement après son démarrage, consultez [Contrôler une horloge de façon interactive](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## Voir aussi  
 [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)