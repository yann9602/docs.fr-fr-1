---
title: "Comment&#160;: traduire les couleurs d&#39;une image | Microsoft Docs"
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
  - "bitmaps (Windows Forms), modifier des couleurs"
  - "couleurs d'image (Windows Forms)"
  - "images (Windows Forms), modifier des couleurs"
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: traduire les couleurs d&#39;une image
Une traduction ajoute une valeur à un ou plusieurs des quatre composants.  Les entrées de la matrice de couleurs représentant les traductions sont présentées dans le tableau suivant.  
  
|Composant à traduire|Entrée de la matrice|  
|--------------------------|--------------------------|  
|Rouge|\[4\]\[0\]|  
|Vert|\[4\]\[1\]|  
|Bleu|\[4\]\[2\]|  
|Alpha|\[4\]\[3\]|  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Drawing.Image> à partir du fichier ColorBars.bmp.  Le code ajoute ensuite 0,75 au composant rouge de chaque pixel de l'image.  L'image d'origine est dessinée le long de l'image transformée.  
  
 L'illustration suivante montre l'image d'origine sur la gauche et l'image transformée sur la droite.  
  
 ![Traduction des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 Le tableau suivant répertorie les vecteurs de couleur correspondant aux quatre barres situées de part et d'autre de la traduction rouge.  La valeur maximale d'un composant de couleur est 1, le composant rouge de la seconde ligne ne change pas.  \(De même, la valeur minimale d'un composant de couleur est 0.\)  
  
|D'origine|Traduite|  
|---------------|--------------|  
|Noir \(0, 0, 0, 1\)|\(0.75, 0, 0, 1\)|  
|Rouge \(1, 0, 0, 1\)|\(1, 0, 0, 1\)|  
|Vert \(0, 1, 0, 1\)|\(0.75, 1, 0, 1\)|  
|Bleu \(0, 0, 1, 1\)|\(0.75, 0, 1, 1\)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Remplacez `ColorBars.bmp` par le nom et le chemin d'accès d'un fichier image valides sur votre système.  
  
## Voir aussi  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Recoloriage des images](../../../../docs/framework/winforms/advanced/recoloring-images.md)