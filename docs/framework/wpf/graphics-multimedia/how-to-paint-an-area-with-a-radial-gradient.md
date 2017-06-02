---
title: "Comment&#160;: peindre une zone avec un d&#233;grad&#233; radial | Microsoft Docs"
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
  - "pinceaux, peindre avec des dégradés radiaux"
  - "peindre, avec des dégradés radiaux"
  - "dégradés radiaux, peindre avec"
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: peindre une zone avec un d&#233;grad&#233; radial
Cet exemple indique comment utiliser la classe <xref:System.Windows.Media.RadialGradientBrush> pour peindre une zone avec un dégradé radial.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.RadialGradientBrush> pour peindre un rectangle avec un gradient radial qui passe du jaune au rouge, au bleu, puis au vert citron.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 L'illustration suivante montre le gradient de l'exemple précédent.  Les points du dégradé sont mis en surbrillance.  
  
 ![Arrêts du dégradé dans un dégradé radial](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk\_graphicsmm\_4gradientstops\_rg")  
  
> [!NOTE]
>  Les exemples fournis dans cette rubrique utilisent le système de coordonnées par défaut pour définir des points de contrôle.  Le système de coordonnées par défaut est relatif par rapport à une zone englobante : 0 indique 0 % de la zone englobante et 1 indique 100 % de la zone englobante.  Vous pouvez modifier ce système de coordonnées en affectant à la propriété <xref:System.Windows.Media.GradientBrush.MappingMode%2A> la valeur <xref:System.Windows.Media.BrushMappingMode>.  Un système de coordonnées absolues n'est pas relatif par rapport à une zone englobante.  Les valeurs sont interprétées directement dans l'espace local.  
  
 Pour obtenir des exemples <xref:System.Windows.Media.RadialGradientBrush> supplémentaires, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  Pour plus d'informations sur les dégradés et sur d'autres types de pinceaux, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).