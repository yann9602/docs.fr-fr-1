---
title: "Comment&#160;: d&#233;finir la couleur d&#39;un stylet | Microsoft Docs"
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
  - "stylets de couleur"
  - "stylets, définir la couleur"
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir la couleur d&#39;un stylet
Cet exemple modifie la couleur d'un objet <xref:System.Drawing.Pen> existant.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un objet <xref:System.Drawing.Pen> nommé `myPen`.  
  
## Programmation fiable  
 Lorsque vous avez terminé, appelez <xref:System.Drawing.Pen.Dispose%2A> sur les objets consommant des ressources système, tels que <xref:System.Drawing.Pen>.  
  
## Voir aussi  
 <xref:System.Drawing.Pen>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Comment : créer un objet Pen](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Stylets, lignes et rectangles dans GDI\+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)