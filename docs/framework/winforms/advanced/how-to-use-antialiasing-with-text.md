---
title: "Comment&#160;: utiliser l&#39;anticr&#233;nelage avec du texte | Microsoft Docs"
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
  - "anticrénelage, utiliser avec le texte"
  - "chaînes (Windows Forms), anticrénelage lors du dessin"
  - "chaînes (Windows Forms), lissage du dessin"
  - "texte (Windows Forms), anticrénelage"
  - "texte (Windows Forms), lisser"
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: utiliser l&#39;anticr&#233;nelage avec du texte
L'*anticrénelage* fait référence au lissage de bords en escalier de texte et de graphiques dessinés pour améliorer leur apparence ou lisibilité.  Avec les classes managées [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez restituer du texte non crénelé de qualité supérieure, ainsi que du texte de qualité inférieure.  En règle générale, un rendu de meilleure qualité nécessite plus de temps de traitement qu'un rendu de qualité inférieure.  Pour définir le niveau de la qualité du texte, affectez à la propriété <xref:System.Drawing.Graphics.TextRenderingHint%2A> d'un <xref:System.Drawing.Graphics> l'un des éléments de l'énumération <xref:System.Drawing.Text.TextRenderingHint>  
  
## Exemple  
 L'exemple de code suivant dessine du texte avec deux paramètres de qualité différents.  
  
 L'illustration suivante montre la sortie de l'exemple de code.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## Compilation du code  
 L'exemple de code précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)