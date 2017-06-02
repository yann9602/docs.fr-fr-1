---
title: "Comment&#160;: utiliser les propri&#233;t&#233;s jointes d&#39;une zone de dessin pour positionner des &#233;l&#233;ments enfants | Microsoft Docs"
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
  - "propriétés jointes (Concepteur WPF)"
  - "Canvas (contrôle), propriétés jointes"
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: utiliser les propri&#233;t&#233;s jointes d&#39;une zone de dessin pour positionner des &#233;l&#233;ments enfants
Cet exemple montre comment utiliser les [propriétés attachées](GTMT) de <xref:System.Windows.Controls.Canvas> pour positionner des éléments enfants.  
  
## Exemple  
 L'exemple suivant ajoute quatre éléments <xref:System.Windows.Controls.Button> comme éléments enfants d'un <xref:System.Windows.Controls.Canvas> parent.  Chaque élément enfant représente une propriété attachée distincte de <xref:System.Windows.Controls.Canvas> : <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A> et <xref:System.Windows.Controls.Canvas.Top%2A>.  Chaque <xref:System.Windows.Controls.Button> est positionné par rapport au <xref:System.Windows.Controls.Canvas> parent et d'après sa valeur de propriété assignée.  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.Canvas.Bottom%2A>   
 <xref:System.Windows.Controls.Canvas.Left%2A>   
 <xref:System.Windows.Controls.Canvas.Right%2A>   
 <xref:System.Windows.Controls.Canvas.Top%2A>   
 <xref:System.Windows.Controls.Button>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)   
 [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)