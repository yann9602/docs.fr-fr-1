---
title: "Comment&#160;: animer un objet sur un trac&#233; (animation de matrice avec accumulation d&#39;offsets) | Microsoft Docs"
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
  - "accumulation d'offsets"
  - "animation, des objets sur des tracés (animation de matrice avec accumulation d’offsets)"
  - "animation de matrice avec accumulation d'offsets"
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: animer un objet sur un trac&#233; (animation de matrice avec accumulation d&#39;offsets)
Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pour animer un objet sur un chemin d’accès et de faire en sorte que cette animation accumule son décalage valeurs lorsqu’elle est répétée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet à animer le <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform> appliqué à un bouton. Par conséquent, un bouton est déplacé sur un tracé courbé.  
  
 En outre, l’exemple définit le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriété `true`, ce qui entraîne le décalage de la matrice animée à s’accumuler lorsque l’animation se répète. Étant donné que l’accumulation, le bouton se trouve plus loin sur l’écran lorsque l’animation se répète, plutôt que la réinitialisation de la position de départ.  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Notez que, bien que le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriété entraîne des valeurs offset s’accumuler au fil des répétitions, elle n’entraîne pas d’accumuler des valeurs de rotation. Pour rendre les valeurs de rotation s’accumuler, valeur de l’animation <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> et <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> propriétés `true`.  
  
 Pour l’exemple complet, consultez la page [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028). Pour obtenir un exemple indiquant comment animer une <xref:System.Windows.Media.Matrix> valeur sur un chemin sans accumulation d’offsets, consultez [animer un objet le long d’un chemin d’accès (Animation de matrice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Rubriques "Comment" Animation de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)