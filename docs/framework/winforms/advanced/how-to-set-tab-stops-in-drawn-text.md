---
title: "Comment&#160;: d&#233;finir des taquets de tabulation dans du texte dessin&#233; | Microsoft Docs"
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
  - "onglets, texte dessiné"
  - "texte, dessiner avec des taquets de tabulation"
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir des taquets de tabulation dans du texte dessin&#233;
Vous pouvez définir des taquets de tabulation pour le texte en appelant la méthode <xref:System.Drawing.StringFormat.SetTabStops%2A> d'un objet <xref:System.Drawing.StringFormat> et en passant ensuite cet objet <xref:System.Drawing.StringFormat> à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics>.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.TextRenderer?displayProperty=fullName> ne prend pas en charge l'ajout de taquets de tabulation au texte dessiné, bien que vous puissiez développer les taquets de tabulation existants à l'aide de l'indicateur <xref:System.Windows.Forms.TextFormatFlags?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant définit des taquets de tabulation à 150, 250 et 350.  Le code affiche ensuite une liste d'onglets de noms et de notes d'examens.  
  
 L'illustration suivante montre le texte tabulé.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 Le code suivant passe deux arguments à la méthode <xref:System.Drawing.StringFormat.SetTabStops%2A>.  Le deuxième argument est un tableau qui contient les offsets de tabulation.  Le premier argument passé à <xref:System.Drawing.StringFormat.SetTabStops%2A> est 0, ce qui indique que le premier offset dans le tableau est mesuré à partir de la position 0, le bord gauche du rectangle englobant.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## Compilation du code  
  
-   L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)