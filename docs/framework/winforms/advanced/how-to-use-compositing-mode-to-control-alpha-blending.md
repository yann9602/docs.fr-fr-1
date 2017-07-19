---
title: "Comment&#160;: utiliser le mode de composition pour commander la fusion alpha | Microsoft Docs"
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
  - "fusion alpha, composition"
  - "couleurs, mélanger"
  - "couleurs, contrôler la transparence"
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: utiliser le mode de composition pour commander la fusion alpha
Il convient parfois de créer une bitmap hors écran ayant les caractéristiques suivantes :  
  
-   Les couleurs ont des valeurs alpha inférieures à 255.  
  
-   Les couleurs ne font pas l'objet d'une fusion alpha entre elles lors de la création de la bitmap.  
  
-   Lorsque vous affichez la bitmap terminée, les couleurs dans la bitmap subissent une fusion alpha avec les couleurs d'arrière\-plan sur le périphérique d'affichage.  
  
 Pour créer une telle bitmap, construisez un objet <xref:System.Drawing.Bitmap> vide, puis un objet <xref:System.Drawing.Graphics> basé sur cette bitmap.  Pour l'objet <xref:System.Drawing.Graphics>, choisissez le mode de composition <xref:System.Drawing.Drawing2D.CompositingMode?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Drawing.Graphics> basé sur un objet <xref:System.Drawing.Bitmap>.  Le code utilise l'objet <xref:System.Drawing.Graphics> avec deux pinceaux translucides \(alpha \= 160\) pour peindre sur la bitmap.  Le code remplit une ellipse rouge et une ellipse verte en utilisant les pinceaux translucides.  L'ellipse verte chevauche l'ellipse rouge, mais le vert ne se fond pas au rouge parce que le mode de composition de l'objet <xref:System.Drawing.Graphics> correspond à <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 Le code dessine la bitmap à l'écran deux fois : une fois sur un arrière\-plan blanc, une autre sur un arrière\-plan multicolore.  Les pixels dans la bitmap qui font partie des deux ellipses ont un composant alpha de 160 et se fondent donc aux couleurs d'arrière\-plan sur l'écran.  
  
 L'illustration suivante montre la sortie de l'exemple de code.  Notez que les ellipses se fondent à l'arrière\-plan, mais ne se fondent pas entre elles.  
  
 ![Copie du code source](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 L'exemple de code contient cette instruction :  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Si vous souhaitez que les ellipses se fondent entre elles comme à l'arrière\-plan, changez cette instruction de la façon suivante :  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 L'illustration suivante montre la sortie du code modifié.  
  
 ![Vue d'ensemble du code source](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [Fusion alpha de lignes et de remplissages](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)