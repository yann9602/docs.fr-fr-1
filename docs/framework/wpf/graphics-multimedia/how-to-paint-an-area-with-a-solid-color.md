---
title: "Comment : peindre une zone avec une couleur unie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cde7f7df5089806ffb3235393eacc855d137ee51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Comment : peindre une zone avec une couleur unie
Pour peindre une zone avec une couleur unie, vous pouvez utiliser un pinceau système prédéfini, tel que <xref:System.Windows.Media.Brushes.Red%2A> ou <xref:System.Windows.Media.Brushes.Blue%2A>, ou vous pouvez créer un nouveau <xref:System.Windows.Media.SolidColorBrush> et décrire son <xref:System.Windows.Media.SolidColorBrush.Color%2A> à l’aide des valeurs alphanumériques, rouges, verts et bleus. En XAML, vous pouvez également peindre une zone avec une couleur unie à l’aide de la notation hexadécimale.  
  
 Les exemples suivants utilisent chacune de ces techniques pour peindre un <xref:System.Windows.Shapes.Rectangle> bleu.  
  
## <a name="example"></a>Exemple  
 **Utilisation d’un pinceau prédéfini**  
  
 Dans l’exemple suivant utilise le pinceau prédéfini <xref:System.Windows.Media.Brushes.Blue%2A> pour peindre un rectangle bleu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Utilisation de la notation hexadécimale**  
  
 L’exemple suivant utilise une notation hexadécimale à 8 chiffres pour peindre un rectangle en bleu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Utilisation de valeurs ARGB**  
  
 L’exemple suivant crée un <xref:System.Windows.Media.SolidColorBrush> et décrit ses <xref:System.Windows.Media.SolidColorBrush.Color%2A> à l’aide de l’ARVB valeurs pour la couleur bleue.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Pour d’autres façons de décrire la couleur, consultez la <xref:System.Windows.Media.Color> structure.  
  
 **Rubriques connexes**  
  
 Pour plus d’informations sur <xref:System.Windows.Media.SolidColorBrush> et obtenir des exemples supplémentaires, consultez le [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) vue d’ensemble.  
  
 Cet exemple de code fait partie d’un exemple plus complet fourni pour la <xref:System.Windows.Media.SolidColorBrush> classe. Pour l’exemple complet, consultez [Exemples de pinceaux](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Brushes>
