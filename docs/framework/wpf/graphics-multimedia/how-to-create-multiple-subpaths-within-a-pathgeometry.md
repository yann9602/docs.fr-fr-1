---
title: "Comment&#160;: cr&#233;er plusieurs sous-chemins dans un PathGeometry | Microsoft Docs"
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
  - "classes, PathGeometry"
  - "graphiques (WPF), sous-chemins"
  - "sous-chemins multiples"
  - "PathGeometry (classe)"
  - "sous-chemins"
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er plusieurs sous-chemins dans un PathGeometry
Cet exemple montre comment créer plusieurs sous\-chemins dans un <xref:System.Windows.Media.PathGeometry>.  Pour créer plusieurs sous\-chemins, vous créez un <xref:System.Windows.Media.PathFigure> pour chaque sous\-chemin.  
  
## Exemple  
 L'exemple suivant crée deux sous\-chemins, chacun un triangle.  
  
 [!code-xml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 L'exemple suivant montre comment créer plusieurs sous\-chemins à l'aide d'une syntaxe d'attribut <xref:System.Windows.Shapes.Path> et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Chaque `M` crée un sous\-chemin de sorte que l'exemple crée deux sous\-chemins qui dessinent chacun un triangle.  
  
 [!code-xml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 \(Notez que cette syntaxe d'attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, version allégée d'un <xref:System.Windows.Media.PathGeometry>.  Pour plus d'informations, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).\)  
  
## Voir aussi  
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)