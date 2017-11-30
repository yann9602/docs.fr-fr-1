---
title: "Comment : conserver les proportions d'une image utilisée comme arrière-plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a34377403a55ba42d9d3f2946ef26ea48982f5d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Comment : conserver les proportions d'une image utilisée comme arrière-plan
Cet exemple montre comment utiliser le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété d’un <xref:System.Windows.Media.ImageBrush> afin de conserver les proportions de l’image.  
  
 Par défaut, lorsque vous utilisez un <xref:System.Windows.Media.ImageBrush> pour peindre une zone, son contenu s’étire pour remplir complètement la zone de sortie. Lorsque la zone de sortie et l’image ont des proportions différentes, l’image est déformée par cet étirement.  
  
 Pour rendre un <xref:System.Windows.Media.ImageBrush> conserve les proportions de son image, affectez le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise deux <xref:System.Windows.Media.ImageBrush> objets pour peindre deux rectangles. Chaque rectangle est de 300 par 150 pixels et chacun contient une image de 300 par 300 pixels. Le <xref:System.Windows.Media.TileBrush.Stretch%2A> du premier pinceau est définie sur <xref:System.Windows.Media.Stretch.Uniform>et le <xref:System.Windows.Media.TileBrush.Stretch%2A> du deuxième pinceau est définie sur <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 L’illustration suivante montre la sortie du premier pinceau, ce qui a un <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètre <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush avec étirement Uniform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 L’illustration suivante montre la sortie du deuxième pinceau, ce qui a un <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètre <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![ImageBrush avec étirement UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Notez que la <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété se comporte comme pour les autres <xref:System.Windows.Media.TileBrush> des objets, autrement dit, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>. Pour plus d’informations sur <xref:System.Windows.Media.ImageBrush> et l’autre <xref:System.Windows.Media.TileBrush> , consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Notez également que, bien que le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété s’affiche, indiquez comment la <xref:System.Windows.Media.TileBrush> contenu s’étire pour s’ajuster à sa zone de sortie, elle spécifie en fait la <xref:System.Windows.Media.TileBrush> contenu s’étire pour remplir sa mosaïque de base. Pour plus d'informations, consultez <xref:System.Windows.Media.TileBrush>.  
  
 Cet exemple de code fait partie d’un exemple plus complet fourni pour la <xref:System.Windows.Media.ImageBrush> classe. Pour obtenir un exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.TileBrush>  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
