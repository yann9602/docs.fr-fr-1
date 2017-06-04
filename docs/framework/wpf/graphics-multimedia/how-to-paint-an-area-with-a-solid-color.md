---
title: "Comment&#160;: peindre une zone avec une couleur unie | Microsoft Docs"
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
  - "pinceaux, peindre avec des couleurs unies"
  - "peindre, avec des couleurs unies"
  - "couleurs unies, peindre avec"
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: peindre une zone avec une couleur unie
Pour peindre une zone dans une couleur unie, vous pouvez utiliser un pinceau système prédéfini, tel que <xref:System.Windows.Media.Brushes.Red%2A> ou <xref:System.Windows.Media.Brushes.Blue%2A>, ou vous pouvez créer un <xref:System.Windows.Media.SolidColorBrush> et décrire son <xref:System.Windows.Media.SolidColorBrush.Color%2A> à l'aide des valeurs alpha, rouges, vertes et bleues.  En XAML, vous pouvez peindre également une zone dans une couleur unie à l'aide de la notation hexadécimale.  
  
 Les exemples suivants utilisent chacune de ces techniques pour peindre un <xref:System.Windows.Shapes.Rectangle> en bleu.  
  
## Exemple  
 **Utilisation d'un pinceau prédéfini**  
  
 L'exemple suivant utilise le pinceau <xref:System.Windows.Media.Brushes.Blue%2A> prédéfini pour peindre un rectangle en bleu.  
  
 [!code-xml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Utilisation de la notation hexadécimale**  
  
 L'exemple suivant utilise la notation hexadécimale à 8 chiffres pour peindre un rectangle en bleu.  
  
 [!code-xml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Utilisation de valeurs ARGB**  
  
 L'exemple suivant crée un <xref:System.Windows.Media.SolidColorBrush> et décrit son <xref:System.Windows.Media.SolidColorBrush.Color%2A> à l'aide des valeurs ARGB pour la couleur bleue.  
  
 [!code-xml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Pour découvrir d'autres manières de décrire la couleur, consultez la structure <xref:System.Windows.Media.Color>.  
  
 **Rubriques connexes**  
  
 Pour plus d'informations sur <xref:System.Windows.Media.SolidColorBrush> et pour obtenir des exemples supplémentaires, consultez la vue d'ensemble [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
 Cet exemple de code fait partie d'un exemple plus complet fourni pour la classe <xref:System.Windows.Media.SolidColorBrush>.  Pour obtenir l'exemple complet, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## Voir aussi  
 <xref:System.Windows.Media.Brushes>