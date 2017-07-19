---
title: "Comment&#160;: animer la position ou la couleur d&#39;un point de d&#233;grad&#233; | Microsoft Docs"
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
  - "animation, couleur des objets GradientStop"
  - "animation, position des objets GradientStop"
  - "couleurs, animer"
  - "objets GradientStop, animer la couleur de"
  - "objets GradientStop, animer la position de"
  - "position, animer"
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: animer la position ou la couleur d&#39;un point de d&#233;grad&#233;
Cet exemple indique comment animer les <xref:System.Windows.Media.GradientStop.Color%2A> et <xref:System.Windows.Media.GradientStop.Offset%2A> d'objets <xref:System.Windows.Media.GradientStop>.  
  
## Exemple  
 L'exemple suivant anime trois points de dégradé dans <xref:System.Windows.Media.LinearGradientBrush>.  Cet exemple utilise trois animations, chacune animant un point de dégradé différent :  
  
-   La première animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, anime le <xref:System.Windows.Media.GradientStop.Offset%2A> du premier point de dégradé de 0.0 à 1.0, puis revient à 0.0.  Par conséquent, la première couleur du dégradé se décale de la gauche vers la droite du rectangle, puis revient sur la gauche.  
  
-   La deuxième animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, anime le <xref:System.Windows.Media.GradientStop.Color%2A> du deuxième point de dégradé de <xref:System.Windows.Media.Colors.Purple%2A> vers <xref:System.Windows.Media.Colors.Yellow%2A>, puis vice versa vers <xref:System.Windows.Media.Colors.Purple%2A> de nouveau.  En conséquence, la couleur au centre du dégradé passe de violet à jaune, puis de nouveau à violet.  
  
-   La troisième animation, un autre <xref:System.Windows.Media.Animation.ColorAnimation>, anime l'opacité du <xref:System.Windows.Media.GradientStop.Color%2A> du troisième point de dégradé de \-1, puis vice versa.  En conséquence, la troisième couleur dans les atténuations dégradées devient loin, puis encore opaque.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Media.LinearGradientBrush>, le processus est le même pour animer des objets <xref:System.Windows.Media.GradientStop> dans un <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Pour obtenir des exemples supplémentaires, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## Voir aussi  
 <xref:System.Windows.Media.GradientStop>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)