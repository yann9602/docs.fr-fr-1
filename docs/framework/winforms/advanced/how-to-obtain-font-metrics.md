---
title: "Comment&#160;: obtenir la m&#233;trique des polices | Microsoft Docs"
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
  - "métriques des polices, obtenir"
  - "polices, obtenir les métriques"
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: obtenir la m&#233;trique des polices
La classe <xref:System.Drawing.FontFamily> fournit les méthodes suivantes qui récupèrent diverses métriques pour une combinaison famille\/style particulière :  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>\(FontStyle\)  
  
 Les nombres retournés par ces méthodes sont exprimés en unités de design de police, et sont donc indépendants de la taille et des unités d'un objet <xref:System.Drawing.Font> particulier.  
  
 L'illustration suivante présente les diverses métriques.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## Exemple  
 L'exemple suivant affiche la métrique du style Regular de la famille de polices Arial.  Le code crée également un objet <xref:System.Drawing.Font> \(basé sur la famille Arial\) d'une taille de 16 pixels et affiche la métrique \(en pixels\) de cet objet <xref:System.Drawing.Font> particulier.  
  
 L'illustration suivante montre la sortie de l'exemple de code.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 Notez les deux premières lignes de la sortie présentée dans l'illustration précédente.  L'objet <xref:System.Drawing.Font> retourne la taille 16 et l'objet <xref:System.Drawing.FontFamily> la hauteur 2 048.  Ces deux nombres \(16 et 2 048\) constituent les éléments clés de la conversion entre les unités de design de police et les unités \(dans ce cas des pixels\) de l'objet <xref:System.Drawing.Font>.  
  
 Par exemple, vous pouvez convertir la hampe d'unités de design en pixels de la façon suivante :  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 Le code suivant positionne le texte verticalement en définissant les données membres <xref:System.Drawing.PointF.Y%2A> d'un objet <xref:System.Drawing.PointF>.  La coordonnée y augmente de `font.Height` pour chaque ligne de texte.  La propriété <xref:System.Drawing.Font.Height%2A> d'un objet <xref:System.Drawing.Font> retourne l'interligne \(en pixels\) pour cet objet <xref:System.Drawing.Font> particulier.  Dans cet exemple, le nombre retourné par <xref:System.Drawing.Font.Height%2A> est 19.  Notez que ce nombre \(arrondi à un entier\) est identique à celui qui est obtenu en convertissant la métrique d'interligne en pixels.  
  
 Notez que la hauteur exprimée en em \(appelée également taille ou taille exprimée en em\) n'est pas la somme du jambage ascendant et du jambage descendant.  La somme du jambage ascendant et du jambage descendant s'appelle la hauteur de cellule.  La hauteur de cellule moins l'espacement interne est égale à la hauteur exprimée en em.  La hauteur de cellule plus l'espacement externe est égale à l'interligne.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)