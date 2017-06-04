---
title: "Comment&#160;: cr&#233;er une g&#233;om&#233;trie combin&#233;e | Microsoft Docs"
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
  - "combiner des géométries"
  - "géométries, combiner"
  - "graphiques, combiner des géométries"
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er une g&#233;om&#233;trie combin&#233;e
Cet exemple indique comment combiner des géométries.  Pour combiner deux géométries, utilisez un objet <xref:System.Windows.Media.CombinedGeometry>.  Définissez ses propriétés <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> avec les deux géométries à combiner, et attribuez à la propriété <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>, qui détermine la manière dont les géométries seront combinées ensemble, la valeur `Union`, `Intersect`, `Exclude` ou `Xor`.  
  
 Pour créer une géométrie composite à partir de deux géométries au moins, utilisez un <xref:System.Windows.Media.GeometryGroup>.  
  
## Exemple  
 Dans l'exemple suivant, un <xref:System.Windows.Media.CombinedGeometry> est renseigné par le mode de géométrie combinée `Exclude`.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis tous les deux comme des cercles de même rayon mais avec des centres décalés de 50.  
  
 [!code-xml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Résultats du mode de combinaison Exclure](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.png "mil\_task\_combined\_geometry\_exclude")  
Géométrie combinée Exclude  
  
 Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est renseigné par le mode de géométrie combinée `Intersect`.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis tous les deux comme des cercles de même rayon mais avec des centres décalés de 50.  
  
 [!code-xml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Résultats du mode de combinaison Intersection](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.png "mil\_task\_combined\_geometry\_intersect")  
Géométrie combinée Intersect  
  
 Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est renseigné par le mode de géométrie combinée `Union`.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis tous les deux comme des cercles de même rayon mais avec des centres décalés de 50.  
  
 [!code-xml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Résultats du mode de combinaison Union](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.png "mil\_task\_combined\_geometry\_union")  
Géométrie combinée Union  
  
 Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est renseigné par le mode de géométrie combinée `Xor`.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définis tous les deux comme des cercles de même rayon mais avec des centres décalés de 50.  
  
 [!code-xml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Résultats du mode de combinaison Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.png "mil\_task\_combined\_geometry\_xor")  
Géométrie combinée Xor