---
title: "Comment&#160;: dessiner une forme avec contour | Microsoft Docs"
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
  - "Graphics.DrawEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cercles"
  - "cercles, dessiner"
  - "formes circulaires"
  - "dessiner, formes circulaires"
  - "dessiner, formes"
  - "ellipses, dessiner"
  - "formulaires, dessiner des formes circulaires"
  - "formes avec contour, dessiner"
  - "formes avec contour, exemples"
  - "formes, dessiner"
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: dessiner une forme avec contour
Cet exemple dessine des ellipses et des rectangles avec contour dans un formulaire.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## Compilation du code  
 Vous ne pouvez pas appeler cette méthode dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou s'il est occulté par un autre formulaire.  Pour que votre contenu soit automatiquement repeint, vous devez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
## Programmation fiable  
 Veillez à toujours appeler <xref:System.IDisposable.Dispose%2A> sur les objets qui utilisent des ressources système, tels que les objets <xref:System.Drawing.Pen> et <xref:System.Drawing.Graphics>.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Graphics.DrawRectangle%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)