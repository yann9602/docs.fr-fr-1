---
title: "Comment&#160;: aplanir un trac&#233; courb&#233; en une ligne | Microsoft Docs"
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
  - "courbes, aplatir"
  - "dessiner, aplanir des courbes"
  - "Flatten (méthode)"
  - "graphiques, aplanir des courbes en lignes"
  - "GraphicsPath (objet)"
  - "chemins d'accès, aplatir"
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: aplanir un trac&#233; courb&#233; en une ligne
Un objet <xref:System.Drawing.Drawing2D.GraphicsPath> stocke une séquence de lignes et de splines de Bézier.  Vous pouvez ajouter plusieurs types de courbes \(ellipses, arcs, splines cardinales\) à un tracé, mais chacune d'elles sera convertie en spline de Bézier avant d'être enregistrée dans le tracé.  L'aplatissement d'un tracé consiste à convertir chaque spline de Bézier du tracé en une séquence de lignes droites.  L'illustration suivante présente un tracé avant et après aplatissement.  
  
 ![Lignes droites et courbes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.png "AboutGdip02\_Art32A")  
  
### Pour aplatir un tracé  
  
-   Appelez la méthode <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> d'un objet <xref:System.Drawing.Drawing2D.GraphicsPath>.  La méthode <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> reçoit un argument d'aplatissement qui spécifie la distance maximum entre le tracé aplati et le tracé d'origine.  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Génération et dessin de tracés](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)