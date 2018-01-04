---
title: "Comment : animer un point à l'aide d'images clés"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Comment : animer un point à l'aide d'images clés
Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe pour animer une <xref:System.Windows.Point>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace une ellipse sur un tracé triangulaire. L’exemple utilise le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété d’un <xref:System.Windows.Media.EllipseGeometry>. Cette animation utilise trois images clés de la manière suivante :  
  
1.  Pendant la première demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe pour déplacer l’ellipse le long d’un chemin d’accès à un taux stable à partir de sa position de départ. Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearPointKeyFrame> créent une interpolation linéaire fluide entre les valeurs.  
  
2.  À la fin de la prochaine demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> classe pour déplacer soudainement l’ellipse le long du chemin d’accès à la position suivante. Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> créer soudains entre les valeurs.  
  
3.  Pendant les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplinePointKeyFrame> classe pour ramener l’ellipse à sa position de départ. Les images clés spline comme <xref:System.Windows.Media.Animation.SplinePointKeyFrame> créer une transition entre des valeurs en fonction des valeurs de la <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> propriété. Dans cet exemple, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Par souci de cohérence avec d’autres exemples d’animation, les versions de code de cet exemple montre comment utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Toutefois, lorsque vous appliquez une animation unique dans le code, il est plus simple d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode au lieu d’utiliser un <xref:System.Windows.Media.Animation.Storyboard>. Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Guides pratiques relatifs aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
