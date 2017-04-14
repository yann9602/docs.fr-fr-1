---
title: "Comment&#160;: cr&#233;er des figures &#224; partir de lignes, de courbes et de formes | Microsoft Docs"
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
  - "figures, créer à partir de lignes"
  - "figures, créer à partir de formes"
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er des figures &#224; partir de lignes, de courbes et de formes
Pour créer une figure, construisez un <xref:System.Drawing.Drawing2D.GraphicsPath>, puis appelez des méthodes, telles que <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, pour ajouter des primitives au chemin d'accès.  
  
## Exemple  
 Les exemples de code suivants créent des chemins d'accès qui comportent des figures :  
  
-   Le premier exemple crée un tracé constitué d'une seule figure.  Celle\-ci comprend un seul arc.  L'arc a un angle de balayage de –180 degrés qui va dans le sens inverse des aiguilles d'une montre dans le système de coordonnées par défaut.  
  
-   Le deuxième exemple crée un tracé constitué de deux figures.  La première représente un arc suivi d'une ligne.  La seconde représente une ligne suivie d'une courbe elle‑même suivie d'une ligne.  La première figure reste ouverte et la seconde est fermée.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## Compilation du code  
 Les exemples précédents sont destinés à une utilisation avec Windows Forms et nécessitent <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [Génération et dessin de tracés](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)