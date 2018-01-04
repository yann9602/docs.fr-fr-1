---
title: "Comment : incliner un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9da10e4eb6cf045c6c4936b76f847f21ea1495e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-skew-an-element"></a>Comment : incliner un élément
Cet exemple montre comment utiliser un <xref:System.Windows.Media.SkewTransform> pour incliner un élément. Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme. Une utilisation typique d’un <xref:System.Windows.Media.SkewTransform> est la simulation [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] profondeur dans [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objets.  
  
 Utilisez le <xref:System.Windows.Media.SkewTransform.CenterX%2A> et <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriétés pour spécifier le centre du point de la <xref:System.Windows.Media.SkewTransform>.  
  
 Utilisez le <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriétés pour spécifier l’angle d’inclinaison de l’axe des abscisses et l’axe des y et pour incliner le système de coordonnées actuel le long de ces axes.  
  
 Pour prévoir l’effet d’une transformation d’inclinaison, tenez compte des points <xref:System.Windows.Media.SkewTransform.AngleX%2A> inclinaisons de valeurs de l’axe x par rapport au repère d’origine. Par conséquent, pour un <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, l’axe y pivote de 30 degrés via l’origine et inclinaisons les valeurs x-de 30 degrés à partir de cette origine. De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 inclinaisons de valeurs y de la forme de 30 degrés à partir de l’origine. Notez que l’effet produit est différent de celui obtenu lorsque l’on déplace le système de coordonnées de 30 degrés sur l’axe des x ou l’axe des y.  
  
 L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central de (0,0).  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 L’exemple suivant applique une inclinaison verticale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 L’illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.  
  
 ![Exemples de SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Les trois exemples SkewTransform illustrés  
  
 Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
