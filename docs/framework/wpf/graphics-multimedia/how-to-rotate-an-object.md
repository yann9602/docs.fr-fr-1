---
title: "Comment : faire pivoter un objet"
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
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b356ef1782ec5bba4f7288644a0802f029456bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object"></a>Comment : faire pivoter un objet
Cet exemple montre comment faire pivoter un objet. L’exemple crée d’abord un <xref:System.Windows.Media.RotateTransform> puis spécifie son <xref:System.Windows.Media.RotateTransform.Angle%2A> en degrés.  
  
 L’exemple suivant fait pivoter un <xref:System.Windows.Shapes.Polyline> 45 degrés autour de son coin supérieur gauche de l’objet.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 Le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés de la <xref:System.Windows.Media.RotateTransform> spécifier le point de rotation sur lequel l’objet. Ce point central est exprimé dans l’espace de coordonnées de l’élément transformé. Par défaut, la rotation est appliquée à (0,0), qui correspond à l’angle supérieur gauche de l’objet à transformer.  
  
 L’exemple suivant fait pivoter un <xref:System.Windows.Shapes.Polyline> de 45 degrés dans le sens horaire sur le point (25,50) de l’objet.  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 L’illustration suivante montre les résultats de l’application un <xref:System.Windows.Media.Transform> aux deux objets.  
  
 ![rotations de 45 degrés par rapport à différents points centraux](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Deux objets en rotation de 45 degrés à partir de différents centres de rotation  
  
 Le <xref:System.Windows.Shapes.Polyline> dans les exemples précédents est un <xref:System.Windows.UIElement>. Lorsque vous appliquez un <xref:System.Windows.Media.Transform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété d’un <xref:System.Windows.UIElement>, que vous pouvez utiliser la <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriété pour spécifier une origine pour chaque <xref:System.Windows.Media.Transform> que vous appliquez à l’élément. Étant donné que le <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriété utilise des coordonnées relatives, vous pouvez appliquer une transformation au centre de l’élément, même si vous ne connaissez pas sa taille. Pour plus d’informations et pour obtenir un exemple, consultez [indiquer l’origine d’une transformation à l’aide des valeurs relatives](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Transform>  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
