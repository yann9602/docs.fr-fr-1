---
title: "Comment&#160;: peindre une zone avec un d&#233;grad&#233; lin&#233;aire | Microsoft Docs"
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
  - "pinceaux, peindre avec un dégradé linéaire"
  - "dégradés linéaires, peindre avec"
  - "peindre, avec des dégradés linéaires"
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: peindre une zone avec un d&#233;grad&#233; lin&#233;aire
Cet exemple indique comment utiliser la classe <xref:System.Windows.Media.LinearGradientBrush> pour peindre une zone avec un dégradé linéaire.  Dans l'exemple suivant, le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire diagonal qui passe du jaune au rouge au bleu au citron vert.  
  
## Exemple  
 [!code-xml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 L'illustration suivante montre le dégradé créé dans l'exemple précédent.  
  
 ![Dégradé linéaire en diagonale](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.png "graphicsmm\_DiagonalLGB")  
  
 Pour créer un dégradé linéaire horizontal, modifiez le <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et le <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du <xref:System.Windows.Media.LinearGradientBrush> en \(0,0.5\) et \(1,0.5\).  Dans l'exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire horizontal.  
  
 [!code-xml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 L'illustration suivante montre le dégradé créé dans l'exemple précédent.  
  
 ![Dégradé linéaire horizontal](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.png "graphicsmm\_HorizontalLGB")  
  
 Pour créer un dégradé linéaire vertical, modifiez le <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et le <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du <xref:System.Windows.Media.LinearGradientBrush> en \(0.5,0\) et \(0.5,1\).  Dans l'exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire vertical.  
  
 [!code-xml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 L'illustration suivante montre le dégradé créé dans l'exemple précédent.  
  
 ![Dégradé linéaire vertical](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.png "graphicsmm\_VerticalLGB")  
  
> [!NOTE]
>  Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour définir les points de départ et de terminaison.  Le système de coordonnées par défaut est relatif par rapport à une zone englobante : 0 indique 0 % de la zone englobante et 1 indique 100 % de la zone englobante.  Vous pouvez modifier ce système de coordonnées en affectant la valeur <xref:System.Windows.Media.BrushMappingMode?displayProperty=fullName> à la propriété <xref:System.Windows.Media.GradientBrush.MappingMode%2A>.  Un système de coordonnées absolues n'est pas relatif par rapport à une zone englobante.  Les valeurs sont interprétées directement dans l'espace local.  
  
 Pour obtenir des exemples supplémentaires, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  Pour plus d'informations sur les dégradés et sur d'autres types de pinceaux, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).