---
title: "Comment&#160;: utiliser un stylet pour dessiner des lignes | Microsoft Docs"
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
  - "lignes, dessiner"
  - "stylets, tracer des lignes"
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: utiliser un stylet pour dessiner des lignes
Pour dessiner des lignes, il vous faut un objet <xref:System.Drawing.Graphics> et un objet <xref:System.Drawing.Pen>.  L'objet <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawLine%2A> et l'objet <xref:System.Drawing.Pen> stocke les fonctionnalités de la ligne, telles que la couleur et la largeur.  
  
## Exemple  
 L'exemple suivant dessine une ligne de \(20, 10\) à \(300, 100\).  La première instruction utilise le constructeur de classes <xref:System.Drawing.Pen.%23ctor%2A> pour créer un stylet noir.  L'argument  passé au constructeur <xref:System.Drawing.Pen.%23ctor%2A> est un objet <xref:System.Drawing.Color> créé avec la méthode <xref:System.Drawing.Color.FromArgb%2A>.  Les valeurs utilisées pour créer l'objet <xref:System.Drawing.Color> \(255, 0, 0, 0\) correspondent aux composants alpha, rouge, vert et bleu de la couleur.  Ces valeurs définissent un stylet noir opaque.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 <xref:System.Drawing.Pen>   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Stylets, lignes et rectangles dans GDI\+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)