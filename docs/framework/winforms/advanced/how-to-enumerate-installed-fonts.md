---
title: "Comment&#160;: &#233;num&#233;rer les polices install&#233;es | Microsoft Docs"
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
  - "exemples (Windows Forms), polices"
  - "polices, énumération installée"
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: &#233;num&#233;rer les polices install&#233;es
La classe <xref:System.Drawing.Text.InstalledFontCollection> hérite de la classe de base abstraite <xref:System.Drawing.Text.FontCollection>.  Vous pouvez utiliser un objet <xref:System.Drawing.Text.InstalledFontCollection> pour énumérer les polices installées sur l'ordinateur.  La propriété <xref:System.Drawing.Text.FontCollection.Families%2A> d'un objet <xref:System.Drawing.Text.InstalledFontCollection> représente un tableau d'objets <xref:System.Drawing.FontFamily>.  
  
## Exemple  
 L'exemple suivant répertorie les noms de toutes les familles de polices installées sur l'ordinateur.  Le code récupère la propriété <xref:System.Drawing.FontFamily.Name%2A> de chaque objet <xref:System.Drawing.FontFamily> dans le tableau retourné par la propriété <xref:System.Drawing.Text.FontCollection.Families%2A>.  Lorsque les noms de famille sont récupérés, ils sont concaténés pour former une liste avec la virgule comme séparateur.  Ensuite, la méthode <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics> dessine la liste séparée par des virgules dans un rectangle.  
  
 Si vous exécutez l'exemple de code, la sortie sera analogue à celle présentée dans l'illustration suivante.  
  
 ![Polices installées](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  Vous devez également importer l'espace de noms <xref:System.Drawing.Text>.  
  
## Voir aussi  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)