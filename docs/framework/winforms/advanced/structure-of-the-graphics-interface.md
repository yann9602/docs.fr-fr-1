---
title: "Structure de l&#39;interface graphique | Microsoft Docs"
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
  - "GDI+, utiliser l'interface managée"
  - "graphiques, structure de classe"
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Structure de l&#39;interface graphique
L'interface de classe managée de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contient environ 60 classes, 50 énumérations et 8 structures.  La classe <xref:System.Drawing.Graphics> est au cœur des fonctionnalités [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ; il s'agit de la classe qui permet de dessiner des lignes, des courbes, des illustrations, des images et du texte.  
  
## Classes importantes  
 Beaucoup de classes fonctionnent en collaboration avec la classe <xref:System.Drawing.Graphics>.  Par exemple, la méthode <xref:System.Drawing.Graphics.DrawLine%2A> reçoit un objet <xref:System.Drawing.Pen>, qui contient les attributs \(couleur, largeur, style de ligne, etc.\) de la ligne à dessiner.  La méthode <xref:System.Drawing.Graphics.FillRectangle%2A> peut recevoir un pointeur vers un objet <xref:System.Drawing.Drawing2D.LinearGradientBrush>, qui fonctionne avec l'objet <xref:System.Drawing.Graphics> pour remplir un rectangle avec des changements de couleurs progressifs.  Les objets <xref:System.Drawing.Font> et <xref:System.Drawing.StringFormat> influencent la manière dont un objet <xref:System.Drawing.Graphics> dessine du texte.  Un objet <xref:System.Drawing.Drawing2D.Matrix> stocke et manipule la transformation universelle d'un objet <xref:System.Drawing.Graphics> qui permet de faire pivoter, de mettre à l'échelle et de retourner des images.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit plusieurs structures \(par exemple, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point> et <xref:System.Drawing.Size>\) pour l'organisation de données graphiques.  Par ailleurs, certaines classes sont essentiellement utilisées comme des types de données structurés.  Par exemple, la classe <xref:System.Drawing.Imaging.BitmapData> est une application d'assistance pour la classe <xref:System.Drawing.Bitmap>, et la classe <xref:System.Drawing.Drawing2D.PathData> est une application d'assistance pour la classe <xref:System.Drawing.Drawing2D.GraphicsPath>.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] définit plusieurs énumérations, qui sont des collections de constantes connexes.  Par exemple, l'énumération <xref:System.Drawing.Drawing2D.LineJoin> contient les éléments <xref:System.Drawing.Drawing2D.LineJoin>, <xref:System.Drawing.Drawing2D.LineJoin> et <xref:System.Drawing.Drawing2D.LineJoin>, qui spécifient les styles pouvant être utilisés pour joindre deux lignes.  
  
## Voir aussi  
 [Vue d'ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [À propos du code managé GDI\+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)