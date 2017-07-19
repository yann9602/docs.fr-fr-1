---
title: "Comment&#160;: utiliser une table de remappage des couleurs | Microsoft Docs"
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
  - "tables de remappage des couleurs, utilisation"
  - "tables de couleurs, remapper les couleurs avec"
  - "couleurs personnalisées, créer avec la table de remappage des couleurs"
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: utiliser une table de remappage des couleurs
Le remappage est le processus de conversion des couleurs dans une image selon une table de remappage des couleurs.  La table de remappage des couleurs est un tableau d'objets <xref:System.Drawing.Imaging.ColorMap>.  Chaque objet <xref:System.Drawing.Imaging.ColorMap> du tableau possède une propriété <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> et une propriété <xref:System.Drawing.Imaging.ColorMap.NewColor%2A>.  
  
 Lorsque [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dessine une image, chaque pixel de cette image est comparé au tableau des anciennes couleurs.  Si une couleur d'un pixel correspond à une ancienne couleur, celle\-ci est modifiée dans la nouvelle couleur correspondante.  Les couleurs sont modifiées uniquement à des fins de restitution : les valeurs de couleur de l'image elle\-même \(stockées dans un objet <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap>\) restent inchangées.  
  
 Pour dessiner une image remappée, initialisez un tableau d'objets <xref:System.Drawing.Imaging.ColorMap>.  Passez ce tableau à la méthode <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> d'un objet <xref:System.Drawing.Imaging.ImageAttributes>, puis passez l'objet <xref:System.Drawing.Imaging.ImageAttributes> à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d'un objet <xref:System.Drawing.Graphics>.  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Drawing.Image> à partir du fichier RemapInput.bmp.  Le code crée une table de remappage des couleurs qui se compose d'un objet <xref:System.Drawing.Imaging.ColorMap> unique.  La propriété <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> de l'objet `ColorRemap`  est rouge, et la propriété <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> est bleue.  L'image est dessinée une fois sans le remappage et une fois avec le remappage.  Le processus de remappage modifie tous les pixels rouges en pixels bleus.  
  
 L'illustration suivante montre l'image d'origine sur la gauche et l'image remappée sur la droite.  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Recoloriage des images](../../../../docs/framework/winforms/advanced/recoloring-images.md)   
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)