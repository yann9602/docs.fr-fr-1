---
title: "Polygones dans GDI+ | Microsoft Docs"
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
  - "dessiner, polygones"
  - "GDI+, polygones"
  - "polygones"
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Polygones dans GDI+
Un polygone est une forme fermée délimitée par trois segments de droite au moins.  Par exemple, un triangle est un polygone à trois côtés, un rectangle est un polygone à quatre côtés et un pentagone est un polygone à cinq côtés.  L'illustration suivante représente plusieurs polygones.  
  
 ![Polygones](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.png "Aboutgdip02\_art07")  
  
## Dessin d'un polygone  
 Pour dessiner un polygone, il vous faut un objet <xref:System.Drawing.Graphics>, un objet <xref:System.Drawing.Pen> et un tableau d'objets <xref:System.Drawing.Point> \(ou <xref:System.Drawing.PointF>\).  L'objet <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawPolygon%2A>.  L'objet <xref:System.Drawing.Pen> stocke les attributs \(largeur et couleur notamment\) de la ligne utilisée pour dessiner le polygone et le tableau d'objets <xref:System.Drawing.Point> stocke les points à relier par des lignes droites.  L'objet <xref:System.Drawing.Pen> et le tableau d'objets <xref:System.Drawing.Point> sont passés en tant qu'arguments à la méthode <xref:System.Drawing.Graphics.DrawPolygon%2A>.  L'exemple suivant dessine un polygone à trois côtés.  Notez que  `myPointArray` comprend seulement trois points : \(0, 0\), \(50, 30\) et \(30, 60\).  La méthode <xref:System.Drawing.Graphics.DrawPolygon%2A> ferme automatiquement le polygone en dessinant une ligne du point \(30, 60\) au point de départ \(0, 0\).  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 L'illustration suivante représente ce polygone.  
  
 ![Polygone](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.png "Aboutgdip02\_art08")  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Comment : créer un objet Pen](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)