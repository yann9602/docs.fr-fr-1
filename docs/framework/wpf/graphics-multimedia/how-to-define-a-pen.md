---
title: "Comment&#160;: d&#233;finir un stylet | Microsoft Docs"
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
  - "créer, stylets"
  - "stylets, définition"
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 2
---
# Comment&#160;: d&#233;finir un stylet
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Pen> pour esquisser une forme.  Pour créer un <xref:System.Windows.Media.Pen> simple, vous devez uniquement spécifier son <xref:System.Windows.Media.Pen.Thickness%2A> et son <xref:System.Windows.Media.Pen.Brush%2A>.  Vous pouvez créer un stylet plus complexe en spécifiant des objets <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A> et <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.Pen> pour esquisser une forme définie par un <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Contours produits à l'aide d'un stylet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.png "graphicsmm\_simple\_pen")  
GeometryDrawing