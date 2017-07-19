---
title: "Comment&#160;: dessiner une ligne avec des embouts de ligne | Microsoft Docs"
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
  - "tracer des lignes, embouts de ligne"
  - "dessiner, lignes"
  - "lignes, dessiner"
  - "stylets, tracer des lignes"
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: dessiner une ligne avec des embouts de ligne
Vous pouvez dessiner le début ou la fin d'une ligne avec l'une des différentes formes appelées extrémités de ligne.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] prend en charge plusieurs extrémités de ligne, telles que rond, carré, losange et pointe de flèche.  
  
## Exemple  
 Vous pouvez spécifier des embouts de ligne pour le début d'une ligne \(embout de début\), la fin d'une ligne \(embout de fin\), ou les pointillés d'une ligne discontinue \(embout pointillé\).  
  
 L'exemple suivant dessine une ligne avec une pointe de flèche à une extrémité et un embout rond à l'autre extrémité.  L'illustration montre la ligne résultante :  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens4.png "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## Compilation du code  
  
-   Créez un Windows Form et gérez l'événement <xref:System.Windows.Forms.Control.Paint> du formulaire.  Collez l'exemple de code dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint> en passant `e` en tant que <xref:System.Windows.Forms.PaintEventArgs>.  
  
## Voir aussi  
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=fullName>   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)