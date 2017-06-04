---
title: "Comment&#160;: remplir des figures ouvertes | Microsoft Docs"
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
  - "figures, remplir"
  - "figures ouvertes, remplir"
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: remplir des figures ouvertes
Vous pouvez remplir un tracé en passant un objet <xref:System.Drawing.Drawing2D.GraphicsPath> à la méthode <xref:System.Drawing.Graphics.FillPath%2A>.  La méthode <xref:System.Drawing.Graphics.FillPath%2A> remplit le tracé conformément au mode de remplissage \(de substitution ou par balayage\) qui est alors défini pour le tracé.  Si le chemin d'accès contient des figures ouvertes, le chemin d'accès est rempli comme si ces figures étaient fermées.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ferme une figure en dessinant une ligne droite de son point de fin à son point de départ.  
  
## Exemple  
 L'exemple suivant crée un tracé ayant une figure ouverte \(un arc\) et une figure fermée \(une ellipse\).  La méthode <xref:System.Drawing.Graphics.FillPath%2A> remplit le tracé conformément au mode de remplissage par défaut qui est <xref:System.Drawing.Drawing2D.FillMode>.  
  
 L'illustration suivante montre la sortie de l'exemple de code.  Notez que le tracé est rempli \(conformément à <xref:System.Drawing.Drawing2D.FillMode>\) comme si la figure ouverte était fermée par une ligne droite reliant son point d'arrivée à son point de départ.  
  
 ![Remplir le tracé ouvert](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [Tracés graphiques dans GDI\+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)