---
title: "Comment&#160;: joindre des lignes | Microsoft Docs"
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
  - "biseau (style de ligne de jointure)"
  - "dessiner, joindre des lignes"
  - "graphiques, joindre des lignes"
  - "GraphicsPath (objet)"
  - "joindre des lignes"
  - "lignes, joindre"
  - "onglet (style de ligne de jointure)"
  - "Pen (classe)"
  - "arrondi (style de ligne de jointure)"
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: joindre des lignes
Une jonction de ligne est la zone commune formée par deux lignes dont les extrémités se rencontrent ou se chevauchent.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit trois styles de jonction de ligne : à angle aigu, en biseau et arrondie.  Le style de jonction de ligne est une propriété de la classe <xref:System.Drawing.Pen>.  Lorsque vous spécifiez un style de jonction de ligne pour un objet <xref:System.Drawing.Pen>, ce style de jonction sera appliqué à toutes les lignes connectées dans n'importe quel objet <xref:System.Drawing.Drawing2D.GraphicsPath> dessiné à l'aide de ce stylet.  
  
 L'illustration suivante montre les résultats de l'exemple de jonction de lignes biseautée.  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens5.png "pens5")  
  
## Exemple  
 Vous pouvez spécifier le style de jonction de ligne à l'aide de la propriété <xref:System.Drawing.Pen.LineJoin%2A> de la classe <xref:System.Drawing.Pen>.  L'exemple illustre une jonction de lignes biseautée entre une ligne horizontale et une ligne verticale.  Dans le code suivant, la valeur <xref:System.Drawing.Drawing2D.LineJoin> assignée à la propriété <xref:System.Drawing.Pen.LineJoin%2A> est un membre de l'énumération <xref:System.Drawing.Drawing2D.LineJoin>.  Les autres membres de l'énumération <xref:System.Drawing.Drawing2D.LineJoin> sont <xref:System.Drawing.Drawing2D.LineJoin> et <xref:System.Drawing.Drawing2D.LineJoin>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)