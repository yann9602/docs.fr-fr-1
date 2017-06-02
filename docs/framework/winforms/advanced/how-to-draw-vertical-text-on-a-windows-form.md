---
title: "Comment&#160;: dessiner du texte vertical dans un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StringFormat.FormatFlags"
  - "Graphics.DrawString"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "chaînes (Windows Forms), dessiner verticalement"
  - "texte (Windows Forms), dessiner"
  - "texte (Windows Forms), dessiner verticalement"
  - "texte (Windows Forms), texte vertical"
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: dessiner du texte vertical dans un Windows Form
L'exemple de code suivant indique comment dessiner un texte vertical sur un formulaire en utilisant la méthode <xref:System.Drawing.Graphics.DrawString%2A> de <xref:System.Drawing.Graphics>.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## Compilation du code  
 Vous ne pouvez pas appeler cette méthode dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou s'il est occulté par un autre formulaire.  Pour que votre contenu soit automatiquement repeint, vous devez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   La police Arial n'est pas installée.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.DrawString%2A>   
 <xref:System.Drawing.StringFormat.FormatFlags%2A>   
 <xref:System.Drawing.StringFormatFlags>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)