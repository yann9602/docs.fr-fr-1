---
title: "Comment&#160;: dessiner du texte dans un Windows Form | Microsoft Docs"
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
  - "formulaires, dessiner du texte"
  - "texte, dessiner"
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: dessiner du texte dans un Windows Form
L'exemple de code suivant montre comment utiliser la méthode <xref:System.Drawing.Graphics.DrawString%2A> de <xref:System.Drawing.Graphics> pour dessiner du texte sur un formulaire.  Vous pouvez également utiliser <xref:System.Windows.Forms.TextRenderer> pour dessiner le texte sur un formulaire.  Pour plus d'informations, consultez [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## Compilation du code  
 Vous ne pouvez pas appeler la méthode <xref:System.Drawing.Graphics.DrawString%2A> dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou s'il est occulté par un autre formulaire.  Pour que votre contenu soit automatiquement repeint, vous devez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   La police Arial n'est pas installée.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.DrawString%2A>   
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>   
 <xref:System.Drawing.StringFormat.FormatFlags%2A>   
 <xref:System.Drawing.StringFormatFlags>   
 <xref:System.Windows.Forms.TextFormatFlags>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)