---
title: "Comment&#160;: &#233;crire du texte avec GDI | Microsoft Docs"
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
  - "dessiner, texte"
  - "GDI, dessiner du texte (Windows Forms)"
  - "texte, dessiner avec TextRenderer"
  - "Windows Forms, ajouter du texte avec GDI"
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: &#233;crire du texte avec GDI
Avec la méthode <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de la classe <xref:System.Windows.Forms.TextRenderer>, vous pouvez accéder aux fonctionnalités [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] de dessin de texte sur un formulaire ou un contrôle.  Le rendu de texte [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] offre en général de meilleures performances et une mesure de texte plus exacte que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  Les méthodes <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de la classe <xref:System.Windows.Forms.TextRenderer> ne sont pas prises en charge pour l'impression.  Lorsque vous imprimez, utilisez toujours les méthodes <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics>.  
  
## Exemple  
 L'exemple de code suivant montre comment dessiner du texte sur plusieurs lignes dans un rectangle à l'aide de la méthode <xref:System.Windows.Forms.TextRenderer.DrawText%2A>.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Pour restituer le texte avec la classe <xref:System.Windows.Forms.TextRenderer>, vous avez besoin d'un <xref:System.Drawing.IDeviceContext>, tel qu'un <xref:System.Drawing.Graphics> et une <xref:System.Drawing.Font>, un emplacement pour dessiner le texte, et la couleur dans laquelle il doit être dessiné.  Vous pouvez également spécifier la mise en forme du texte à l'aide de l'énumération <xref:System.Windows.Forms.TextFormatFlags>.  
  
 Pour plus d'informations sur l'obtention d'un <xref:System.Drawing.Graphics>, consultez [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  Pour plus d'informations sur la construction d'un <xref:System.Drawing.Font>, consultez [Comment : construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## Compilation du code  
 L'exemple de code précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextRenderer>   
 <xref:System.Drawing.Font>   
 <xref:System.Drawing.Color>   
 <xref:System.Drawing.Color>   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)