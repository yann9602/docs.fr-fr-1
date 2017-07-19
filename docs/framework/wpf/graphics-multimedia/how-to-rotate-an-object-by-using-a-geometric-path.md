---
title: "Comment&#160;: faire pivoter un objet &#224; l&#39;aide d&#39;un trac&#233; g&#233;om&#233;trique | Microsoft Docs"
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
  - "tracés géométriques, faire pivoter des objets par"
  - "faire pivoter des objets par tracés géométriques"
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: faire pivoter un objet &#224; l&#39;aide d&#39;un trac&#233; g&#233;om&#233;trique
Cet exemple montre comment pivoter un objet sur un tracé géométrique défini par un <xref:System.Windows.Media.PathGeometry> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise trois <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objets pour déplacer un rectangle sur un tracé géométrique.  
  
-   La première <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime un <xref:System.Windows.Media.RotateTransform> qui est appliqué au rectangle. L’animation génère des valeurs d’angle. Ainsi, le rectangle pivoter sur les contours du tracé.  
  
-   Les deux autres objets animent les <xref:System.Windows.Media.TranslateTransform.X%2A> et <xref:System.Windows.Media.TranslateTransform.Y%2A> valeurs d’une <xref:System.Windows.Media.TranslateTransform> qui est appliqué au rectangle. Ils déplacent le rectangle horizontalement et verticalement le long du tracé.  
  
 [!code-xml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Une autre façon de faire pivoter un objet à l’aide d’un tracé géométrique consiste à utiliser un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et définissez son <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriété `true`. Pour plus d’informations et un exemple, consultez [faire pivoter un objet à l’aide d’un tracé géométrique (Animation de matrice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Pour l’exemple complet, consultez la page [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [Rubriques "Comment" Animation de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)