---
title: "Comment&#160;: remplir une forme avec un motif hachur&#233; | Microsoft Docs"
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
  - "pinceaux, utiliser les pinceaux à hachures"
  - "modèles, ajouter aux formes"
  - "formes, remplir avec des modèles"
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: remplir une forme avec un motif hachur&#233;
Un motif hachuré est composé de deux couleurs : une première pour l'arrière\-plan, une autre pour les lignes qui forment le motif recouvrant l'arrière\-plan.  Pour remplir une forme fermée avec un motif hachuré, utilisez un objet <xref:System.Drawing.Drawing2D.HatchBrush>.  L'exemple suivant montre comment remplir une ellipse avec un motif hachuré :  
  
## Exemple  
 Le constructeur <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> prend trois arguments : le style de hachure, la couleur de la ligne de hachure et la couleur d'arrière\-plan.  L'argument de style de hachure peut correspondre à n'importe quelle valeur de l'énumération <xref:System.Drawing.Drawing2D.HatchStyle>.  L'énumération <xref:System.Drawing.Drawing2D.HatchStyle> comporte plus de cinquante éléments dont quelques\-uns sont indiqués dans la liste suivante :  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
 L'illustration suivante montre l'ellipse remplie.  
  
 ![Motif hachuré](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)