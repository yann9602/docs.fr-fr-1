---
title: "Comment&#160;: alt&#233;rer des couleurs | Microsoft Docs"
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
  - "couleurs, inclinaison"
  - "couleurs, transformer avec les matrices des couleurs"
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: alt&#233;rer des couleurs
L'inclinaison augmente ou diminue une composante de couleur par un montant proportionnel à une autre composante de couleur.  Par exemple, imaginez une transformation où la composante rouge serait augmentée de la moitié de la valeur de la composante bleu.  Avec une transformation de ce style, la couleur \(0,2, 0,5, 1\) deviendrait \(0,7, 0,5, 1\).  La nouvelle composante rouge est 0,2 \+ \(1\/2\)\(1\) \= 0,7.  
  
## Exemple  
 L'exemple suivant construit un objet <xref:System.Drawing.Image> à partir du fichier ColorBars4.bmp.  Ensuite, le code applique la transformation d'inclinaison décrite dans le paragraphe précédent à chaque pixel de l'image.  
  
 L'illustration suivante montre l'image d'origine sur la gauche et l'image inclinée sur la droite.  
  
 ![Cisaillement des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 Le tableau suivant répertorie les vecteurs de couleur correspondant aux quatre barres situées de part et d'autre de la transformation d'inclinaison.  
  
|D'origine|Incliné|  
|---------------|-------------|  
|\(0, 0, 1, 1\)|\(0.5, 0, 1, 1\)|  
|\(0.5, 1, 0.5, 1\)|\(0.75, 1, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(1, 1, 0, 1\)|  
|\(0.4, 0.4, 0.4, 1\)|\(0.6, 0.4, 0.4, 1\)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Remplacez `ColorBars.bmp` par le nom et le chemin d'accès d'une image valides sur votre système.  
  
## Voir aussi  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Recoloriage des images](../../../../docs/framework/winforms/advanced/recoloring-images.md)