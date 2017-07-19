---
title: "Comment&#160;: conserver les proportions d&#39;une image utilis&#233;e comme arri&#232;re-plan | Microsoft Docs"
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
  - "proportions des images d'arrière-plan, conserver"
  - "images d'arrière-plan, conserver les proportions"
  - "pinceaux, conserver les proportions des images d'arrière-plan"
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: conserver les proportions d&#39;une image utilis&#233;e comme arri&#232;re-plan
Cet exemple montre comment utiliser la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> d'un <xref:System.Windows.Media.ImageBrush> pour conserver les [proportions](GTMT) de l'image.  
  
 Par défaut, lorsque vous utilisez un <xref:System.Windows.Media.ImageBrush> pour peindre une zone, son contenu s'étire pour remplir complètement la zone de sortie.  Lorsque la zone de sortie et l'image ont des [proportions](GTMT) différentes, l'image est déformée par cet étirement.  
  
 Pour qu'un <xref:System.Windows.Media.ImageBrush> conserve les proportions de son image, affectez à la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> la valeur <xref:System.Windows.Media.Stretch> ou <xref:System.Windows.Media.Stretch>.  
  
## Exemple  
 L'exemple suivant utilise deux objets <xref:System.Windows.Media.ImageBrush> pour peindre deux rectangles.  Chaque rectangle fait 300 par 150 [pixels](GTMT) et chacun contient une image de 300 par 300 pixels.  La propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> du premier pinceau a la valeur <xref:System.Windows.Media.Stretch> et la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> du deuxième pinceau a la valeur <xref:System.Windows.Media.Stretch>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 L'illustration suivante montre la sortie du premier pinceau, dont le paramètre <xref:System.Windows.Media.TileBrush.Stretch%2A> a la valeur <xref:System.Windows.Media.Stretch>.  
  
 ![ImageBrush avec étirement Uniform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.png "graphicsmm\_ImageBrushUniformStretch")  
  
 L'illustration suivante montre la sortie du deuxième pinceau, dont le paramètre <xref:System.Windows.Media.TileBrush.Stretch%2A> a la valeur <xref:System.Windows.Media.Stretch>.  
  
 ![ImageBrush avec étirement UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.png "graphicsmm\_ImageBrushUniformToFillStretch")  
  
 Notez que la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> se comporte de la même manière pour les autres objets <xref:System.Windows.Media.TileBrush>, c'est\-à\-dire pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.  Pour plus d'informations sur <xref:System.Windows.Media.ImageBrush> et les autres objets <xref:System.Windows.Media.TileBrush>, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Notez également que, même si la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A> semble spécifier la façon dont le contenu <xref:System.Windows.Media.TileBrush> s'étire pour s'adapter à sa zone de sortie, elle spécifie en fait la façon dont le contenu <xref:System.Windows.Media.TileBrush> s'étire pour remplir sa mosaïque de base.  Pour plus d'informations, consultez <xref:System.Windows.Media.TileBrush>.  
  
 Cet exemple de code fait partie d'un exemple plus complet fourni pour la classe <xref:System.Windows.Media.ImageBrush>.  Pour l'exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## Voir aussi  
 <xref:System.Windows.Media.TileBrush>   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)