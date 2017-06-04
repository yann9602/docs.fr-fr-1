---
title: "Comment&#160;: cr&#233;er un arc elliptique | Microsoft Docs"
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
  - "arcs, elliptiques"
  - "arcs elliptiques, créer"
  - "graphiques (WPF), arcs elliptiques"
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un arc elliptique
Cet exemple montre comment dessiner un arc elliptique.  Pour créer un arc elliptique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure> et <xref:System.Windows.Media.ArcSegment>.  
  
## Exemple  
 Dans les exemples suivants, un arc elliptique est tracé de \(10,100\) à \(200,100\).  L'arc a un <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 par 50 dip \(device independent pixels\), un <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 degrés, un paramètre <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true` et un <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection>.  
  
 \[xaml\]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d'attribut pour décrire un chemin d'accès.  
  
 [!code-xml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 \[xaml\]  
  
 \(Notez que cette syntaxe d'attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, version allégée d'un <xref:System.Windows.Media.PathGeometry>.  Pour plus d'informations, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).\)  
  
 En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner un arc elliptique en utilisant explicitement des balises d'objet.  Les éléments suivants sont équivalents au balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-xml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Cet exemple est extrait d'un exemple plus complet.  Pour obtenir l'exemple complet, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## Voir aussi  
 [Créer une courbe de Bézier quadratique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)   
 [Créer une courbe de Bézier cubique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)