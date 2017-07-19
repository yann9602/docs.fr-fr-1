---
title: "Comment&#160;: cr&#233;er une courbe de B&#233;zier quadratique | Microsoft Docs"
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
  - "courbes de Bézier, créer"
  - "graphiques (WPF), courbes de Bézier quadratiques"
  - "courbes de Bézier quadratiques, créer"
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er une courbe de B&#233;zier quadratique
Cet exemple montre comment créer une courbe de Bézier quadratique.  Pour créer une courbe de Bézier quadratique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure> et <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
## Exemple  
 Dans les exemples suivants, une courbe de Bézier quadratique est tracée de \(10,100\) à \(300,100\).  La courbe a un point de contrôle de \(200,200\).  
  
 \[xaml\]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d'attribut pour décrire un chemin d'accès.  
  
 [!code-xml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 \[xaml\]  
  
 \(Notez que cette syntaxe d'attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, version allégée d'un <xref:System.Windows.Media.PathGeometry>.  Pour plus d'informations, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).\)  
  
 En langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner une courbe de Bézier quadratique à l'aide de la syntaxe d'élément objet.  L'exemple suivant est équivalent à l'exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-xml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## Voir aussi  
 [Créer un arc elliptique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)   
 [Créer une courbe de Bézier cubique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)