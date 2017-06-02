---
title: "Comment&#160;: faire pivoter un objet &#224; l&#39;aide d&#39;un trac&#233; g&#233;om&#233;trique (animation de matrice) | Microsoft Docs"
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
  - "animation de matrice"
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: faire pivoter un objet &#224; l&#39;aide d&#39;un trac&#233; g&#233;om&#233;trique (animation de matrice)
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et un <xref:System.Windows.Media.MatrixTransform> pour pivoter un objet sur un tracé géométrique défini par un <xref:System.Windows.Media.PathGeometry> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet à animer le <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform>. Le <xref:System.Windows.Media.MatrixTransform> est appliqué à un bouton et permet de déplacer sur un tracé courbé. Étant donné que la <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> est définie sur `true`, le rectangle pivote sur la tangente du chemin d’accès.  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Pour l’exemple complet, consultez la page [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 La version du code de l’exemple précédent utilisé un <xref:System.Windows.Media.Animation.Storyboard> pour animer la <xref:System.Windows.Media.EllipseGeometry>, bien qu’une animation a été appliquée. Un moyen plus simple pour appliquer une seule animation à une propriété dans le code est d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> (méthode). Pour obtenir un exemple, consultez [animer une propriété sans utiliser de Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Rubriques "Comment" Animation de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)   
 [Exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028)