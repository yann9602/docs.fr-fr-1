---
title: "Comment&#160;: dessiner un rectangle rempli dans un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Graphics.FillRectangle"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "dessiner des rectangles"
  - "dessiner, rectangles"
  - "rectangles, dessiner"
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: dessiner un rectangle rempli dans un Windows Form
Cet exemple dessine un rectangle rempli dans un formulaire.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## Compilation du code  
 Vous ne pouvez pas appeler cette méthode dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou s'il est occulté par un autre formulaire.  Pour que votre contenu soit automatiquement repeint, vous devez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
## Programmation fiable  
 Veillez à toujours appeler <xref:System.IDisposable.Dispose%2A> sur les objets consommant des ressources système, tels que <xref:System.Drawing.Brush> et <xref:System.Drawing.Graphics>.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.FillRectangle%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Pinceaux et remplissage de formes dans GDI\+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)