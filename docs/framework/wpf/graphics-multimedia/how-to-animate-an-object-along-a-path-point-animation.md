---
title: "Comment&#160;: animer un objet sur un trac&#233; (animation de point) | Microsoft Docs"
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
  - "animation, des objets sur des tracés (animation de point)"
  - "animation de point"
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: animer un objet sur un trac&#233; (animation de point)
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.PointAnimationUsingPath> objet pour animer une <xref:System.Windows.Point> sur un tracé courbé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déplace un <xref:System.Windows.Media.EllipseGeometry> le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>. La géométrie d’ellipse <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété, qui prend un <xref:System.Windows.Point> valeur, spécifie sa position ; pour déplacer la géométrie d’ellipse, vous animer sa <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété. L’exemple utilise un <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer la <xref:System.Windows.Media.EllipseGeometry> l’objet <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété.  
  
 [!code-xml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Pour l’exemple complet, consultez la page [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 La version du code de l’exemple précédent utilisé un <xref:System.Windows.Media.Animation.Storyboard> pour animer la <xref:System.Windows.Media.EllipseGeometry>, bien qu’une animation a été appliquée. A <xref:System.Windows.Media.Animation.Storyboard> est souvent le moyen le plus simple d’appliquer plusieurs animations, car ces animations peuvent être contrôlées par le même <xref:System.Windows.Media.Animation.Storyboard>. Toutefois, un moyen plus simple pour appliquer une seule animation à une propriété lors de l’utilisation de code consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> (méthode). Pour obtenir un exemple, consultez [animer une propriété sans utiliser de Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Rubriques "Comment" Animation de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)