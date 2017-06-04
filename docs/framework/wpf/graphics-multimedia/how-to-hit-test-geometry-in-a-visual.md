---
title: "Comment&#160;: effectuer un test de positionnement avec Geometry dans un Visual | Microsoft Docs"
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
  - "objets Geometry, objets visuels englobant"
  - "tests de positionnement, sur des objets visuels englobant des objets Geometry"
  - "objets visuels, tests de positionnement sur"
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: effectuer un test de positionnement avec Geometry dans un Visual
Cet exemple montre comment effectuer un [test d'atteinte](GTMT) sur un objet visuel composé d'un ou plusieurs objets <xref:System.Windows.Media.Geometry>.  
  
## Exemple  
 L'exemple suivant montre comment récupérer le <xref:System.Windows.Media.DrawingGroup> d'un objet visuel qui utilise la méthode <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>.  Un test d'atteinte est ensuite effectué sur le contenu rendu de chaque dessin dans le <xref:System.Windows.Media.DrawingGroup> afin de déterminer la géométrie atteinte.  
  
> [!NOTE]
>  Dans la plupart des cas, vous utiliserez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour déterminer si un point croise un des contenus rendus d'un visuel.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 La méthode <xref:System.Windows.Media.Geometry.FillContains%2A> est une méthode surchargée qui vous permet d'effectuer un test d'atteinte à l'aide d'un <xref:System.Windows.Point> ou d'une <xref:System.Windows.Media.Geometry> spécifié.  Si une géométrie est rayée, le trait peut s'étendre en dehors des limites du remplissage.  Dans ce cas, vous pouvez appeler <xref:System.Windows.Media.Geometry.StrokeContains%2A> en plus de <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 Vous pouvez également fournir un <xref:System.Windows.Media.ToleranceType> utilisé pour les besoins de l'aplatissement de Bézier.  
  
> [!NOTE]
>  Cet exemple ne prend pas en compte les transformations ou découpages qui auraient été appliqués à la géométrie.  De plus, cet exemple n'utilise pas de contrôle auquel est appliqué un style, car aucun dessin ne lui est directement associé.  
  
## Voir aussi  
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [Effectuer un test de positionnement avec Geometry comme paramètre](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)