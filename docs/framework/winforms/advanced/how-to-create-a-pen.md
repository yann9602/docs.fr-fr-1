---
title: "Comment&#160;: cr&#233;er un objet Pen | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "graphiques, créer des stylets"
  - "Pen (objet)"
  - "stylets, créer"
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un objet Pen
Cet exemple crée un objet <xref:System.Drawing.Pen>.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## Programmation fiable  
 Lorsque vous avez terminé, appelez <xref:System.Drawing.Pen.Dispose%2A> sur les objets consommant des ressources système, tels que <xref:System.Drawing.Pen>.  
  
## Voir aussi  
 <xref:System.Drawing.Pen>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Stylets, lignes et rectangles dans GDI\+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)