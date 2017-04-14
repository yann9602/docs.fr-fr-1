---
title: "Comment&#160;: construire des familles de polices et des polices | Microsoft Docs"
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
  - "familles de polices, construire"
  - "polices, construire"
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: construire des familles de polices et des polices
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] regroupe dans des familles de polices les polices de même type de caractère, mais de style différent.  Par exemple, la famille de polices Arial contient les polices suivantes :  
  
-   Arial Regular  
  
-   Arial Bold  
  
-   Arial Italic  
  
-   Arial Bold Italic  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] utilise quatre styles pour former des familles : normal, gras, italique et italique gras.  Les adjectifs, tels que *Narrow* et *Rounded*, ne sont pas considérés comme des styles ; ils font plutôt partie du nom de la famille.  Par exemple, Arial Narrow est une famille de polices composée des membres suivants :  
  
-   Arial Narrow Regular  
  
-   Arial Narrow Bold  
  
-   Arial Narrow Italic  
  
-   Arial Narrow Bold Italic  
  
 Pour pouvoir dessiner du texte avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous devez construire un objet <xref:System.Drawing.FontFamily> et un objet <xref:System.Drawing.Font>.  L'objet <xref:System.Drawing.FontFamily> spécifie le type de caractère \(par exemple, Arial\) et l'objet <xref:System.Drawing.Font> précise la taille, le style et les unités.  
  
## Exemple  
 L'exemple suivant génère une police Arial de style Regular d'une taille de 16 pixels.  Dans le code suivant, le premier argument passé au constructeur <xref:System.Drawing.Font.%23ctor%2A> est l'objet <xref:System.Drawing.FontFamily>.  Le deuxième argument spécifie la taille de la police mesurée en unités identifiées par le quatrième argument.  Le troisième argument identifie le style.  
  
 <xref:System.Drawing.GraphicsUnit> est un membre de l'énumération <xref:System.Drawing.GraphicsUnit> et <xref:System.Drawing.FontStyle> est un membre de l'énumération <xref:System.Drawing.FontStyle>.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)