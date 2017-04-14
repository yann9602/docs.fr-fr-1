---
title: "Comment&#160;: dessiner une ligne | Microsoft Docs"
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
  - "dessiner, lignes"
  - "graphiques (WPF), lignes"
  - "lignes, dessiner"
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dessiner une ligne
Cet exemple montre comment dessiner des lignes à l'aide de l'élément <xref:System.Windows.Shapes.Line>.  
  
 Pour dessiner une ligne, créez un élément <xref:System.Windows.Shapes.Line>.  Utilisez ses propriétés <xref:System.Windows.Shapes.Line.X1%2A> et <xref:System.Windows.Shapes.Line.Y1%2A> pour définir son point de départ et utilisez ses propriétés <xref:System.Windows.Shapes.Line.X2%2A> et <xref:System.Windows.Shapes.Line.Y2%2A> pour définir son point de terminaison.  Enfin, définissez <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, car une ligne sans trait est invisible.  
  
 La définition de l'élément <xref:System.Windows.Shapes.Shape.Fill%2A> pour une ligne n'a aucun effet, car une ligne n'a pas d'intérieur.  
  
 L'exemple suivant dessine trois lignes dans un élément <xref:System.Windows.Controls.Canvas>.  
  
## Exemple  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Line>