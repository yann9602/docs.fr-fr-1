---
title: "Comment&#160;: dessiner une ligne remplie d&#39;une texture | Microsoft Docs"
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
  - "tracer des lignes, texture"
  - "dessiner, lignes"
  - "lignes, texture"
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: dessiner une ligne remplie d&#39;une texture
Plutôt que de dessiner une ligne d'une couleur unie, vous pouvez dessiner une ligne avec une texture.  Pour dessiner des lignes et des courbes avec une texture, créez un objet <xref:System.Drawing.TextureBrush> et passez cet objet <xref:System.Drawing.TextureBrush> à un constructeur <xref:System.Drawing.Pen.%23ctor%2A>.  La bitmap associée au pinceau texturé est utilisée pour créer le plan en mosaïque \(de façon invisible\). Lorsque le stylet dessine une ligne ou une courbe, le trait du stylet révèle certains pixels de la texture en mosaïque.  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Drawing.Bitmap> à partir du fichier  `Texture1.jpg`.  Cette bitmap est utilisée pour construire un objet <xref:System.Drawing.TextureBrush>, et l'objet <xref:System.Drawing.TextureBrush> est employé pour construire un objet <xref:System.Drawing.Pen>.  L'appel à <xref:System.Drawing.Graphics.DrawImage%2A> dessine la bitmap en plaçant son coin supérieur gauche à \(0, 0\).  L'appel à <xref:System.Drawing.Graphics.DrawEllipse%2A> utilise l'objet <xref:System.Drawing.Pen> pour dessiner une ellipse texturée.  
  
 L'illustration suivante montre la bitmap et l'ellipse texturée.  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## Compilation du code  
 Créez un Windows Form et gérez l'événement <xref:System.Windows.Forms.Control.Paint> du formulaire.  Collez le code précédent dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Remplacez  `Texture.jpg` par une image valide sur votre système.  
  
## Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)