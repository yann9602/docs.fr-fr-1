---
title: "Comment&#160;: contr&#244;ler le minutage d&#39;une animation d&#39;image cl&#233; | Microsoft Docs"
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
  - "images clés (WPF), minutage"
  - "calculer le minutage de l'animation des images clés"
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: contr&#244;ler le minutage d&#39;une animation d&#39;image cl&#233;
Cet exemple montre comment contrôler le minutage des images clés d'une animation d'image clé.  Comme les autres animations, les animations d'image clé ont une propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  En plus de spécifier la durée d'une animation, vous devez spécifier la partie de cette durée qui sera allouée à chacune de ses images clés.  Pour allouer du temps, spécifiez un <xref:System.Windows.Media.Animation.KeyTime> pour chaque image clé de l'animation.  
  
 Le <xref:System.Windows.Media.Animation.KeyTime> de chaque image clé spécifie la fin d'une image clé \(il ne spécifie pas la durée de lecture d'une image clé\).  Vous pouvez spécifier un <xref:System.Windows.Media.Animation.KeyTime> comme une valeur <xref:System.TimeSpan>, un pourcentage, ou bien la valeur spéciale <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pour animer un rectangle sur l'écran.  Les temps clés des images clés sont définis avec les valeurs <xref:System.TimeSpan>.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 L'illustration suivante montre le moment où la valeur de chaque image clé est atteinte.  
  
 ![Valeurs de clés atteintes à 3, 4 et 10 secondes](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm\_keyframe\_keytime1\_timespan")  
  
 L'exemple suivant montre une animation identique, mais dont les temps clés des images clés sont définis avec des valeurs exprimées en pourcentage.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 L'illustration suivante montre le moment où la valeur de chaque image clé est atteinte.  
  
 ![Valeurs de clés atteintes à 3, 4 et 10 secondes](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm\_keyframe\_keytime2\_percentage")  
  
 L'exemple suivant utilise des valeurs de temps clé <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 L'illustration suivante montre le moment où la valeur de chaque image clé est atteinte.  
  
 ![Valeurs de clés atteintes à 3,3, 6,6 et 9,9 secondes](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm\_keyframe\_keytime3\_uniform")  
  
 Le dernier exemple utilise des valeurs de temps clé <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 L'illustration suivante montre le moment où la valeur de chaque image clé est atteinte.  
  
 ![Valeurs de clés atteintes à 0, 5 et 10 secondes](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm\_keyframe\_keytime4\_paced")  
  
 Par souci de simplicité, les versions de code de cet exemple utilisent des animations locales, et non des storyboards, car on applique une seule animation par propriété. Toutefois, les exemples peuvent être modifiés pour utiliser plutôt des storyboards.  Pour obtenir un exemple sur la manière de déclarer un storyboard dans le code, consultez [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Pour obtenir l'exemple complet, consultez [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  Pour plus d'informations sur les animations d'image clé, consultez [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)