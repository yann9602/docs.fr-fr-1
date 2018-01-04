---
title: "Comment : animer la position ou la couleur d'un point de dégradé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c5a72d5df9d7ff9cdd90d6e09a7dab574e2caaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Comment : animer la position ou la couleur d'un point de dégradé
Cet exemple montre comment animer la <xref:System.Windows.Media.GradientStop.Color%2A> et <xref:System.Windows.Media.GradientStop.Offset%2A> de <xref:System.Windows.Media.GradientStop> objets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant anime trois points de dégradé dans un <xref:System.Windows.Media.LinearGradientBrush>. L’exemple utilise trois animations, chacune d’elles réalise une animation d’un point de dégradé différent :  
  
-   La première animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, anime le premier point de dégradé <xref:System.Windows.Media.GradientStop.Offset%2A> de 0.0 à 1.0, puis revient à 0.0. Par conséquent, la première couleur du dégradé se décale à partir de la gauche vers le côté droit du rectangle et puis de nouveau sur le côté gauche.  
  
-   La deuxième animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, anime le deuxième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> de <xref:System.Windows.Media.Colors.Purple%2A> à <xref:System.Windows.Media.Colors.Yellow%2A> , puis revient à <xref:System.Windows.Media.Colors.Purple%2A>. Par conséquent, la couleur intermédiaire du dégradé passe de violet en jaune et en violet.  
  
-   La troisième animation, un autre <xref:System.Windows.Media.Animation.ColorAnimation>, anime l’opacité de la troisième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> par -1, puis à nouveau. Par conséquent, la troisième couleur dans le dégradé disparaît et devient alors opaque à nouveau.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Media.LinearGradientBrush>, le processus est le même pour animer <xref:System.Windows.Media.GradientStop> d’objets contenus dans un <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Pour obtenir des exemples supplémentaires, consultez le [pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.GradientStop>  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
