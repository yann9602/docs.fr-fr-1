---
title: "Comment&#160;: dessiner une forme ferm&#233;e &#224; l&#39;aide de l&#39;&#233;l&#233;ment Polygon | Microsoft Docs"
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
  - "formes fermées, dessiner avec des éléments Polygon"
  - "dessiner, formes fermées avec des éléments Polygon"
  - "graphiques, éléments Polygon"
  - "éléments Polygon"
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dessiner une forme ferm&#233;e &#224; l&#39;aide de l&#39;&#233;l&#233;ment Polygon
Cet exemple montre comment dessiner une forme fermée à l'aide de l'élément <xref:System.Windows.Shapes.Polygon>.  Pour dessiner une forme fermée, créez un élément <xref:System.Windows.Shapes.Polygon> et utilisez sa propriété <xref:System.Windows.Shapes.Polygon.Points%2A> pour spécifier les vertex d'une forme.  Une ligne qui associe les premiers et derniers points est automatiquement dessinée.  Enfin, spécifiez un <xref:System.Windows.Shapes.Shape.Fill%2A>, un <xref:System.Windows.Shapes.Shape.Stroke%2A>, ou les deux.  
  
## Exemple  
 En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour des points est une liste de paires de coordonnées x et y, séparées par des virgules, délimitée par des espaces.  
  
 [!code-xml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les polygones, vous pouvez utiliser des éléments polygones \(et toutes les autres formes\) avec n'importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).