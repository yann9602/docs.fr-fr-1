---
title: "Comment&#160;: faire pivoter, refl&#233;ter et incliner des images | Microsoft Docs"
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
  - "images (Windows Forms), refléter"
  - "images (Windows Forms), faire pivoter"
  - "images (Windows Forms), incliner"
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: faire pivoter, refl&#233;ter et incliner des images
Vous pouvez appliquer une rotation, une réflexion et une inclinaison à une image en spécifiant des points de destination pour les coins supérieur gauche, supérieur droit et inférieur gauche de l'image d'origine.  Les trois points de destination déterminent une transformation affine qui mappe l'image rectangulaire d'origine à un parallélogramme.  
  
## Exemple  
 Par exemple, supposons que l'image d'origine soit un rectangle dont le coin supérieur gauche se trouve en \(0, 0\), le coin supérieur droit en \(100, 0\) et le coin inférieur gauche en \(0, 50\).  Supposons maintenant que vous mappiez ces trois points aux points de destination indiqués ci\-dessous.  
  
|Point d'origine|Point de destination|  
|---------------------|--------------------------|  
|Supérieur gauche \(0, 0\)|\(200, 20\)|  
|Supérieur droit \(100, 0\)|\(110, 100\)|  
|Inférieur gauche \(0, 50\)|\(250, 30\)|  
  
 L'illustration suivante montre l'image d'origine et l'image mappée au parallélogramme.  L'image d'origine a subi une inclinaison, une réflexion, une rotation et une translation.  L'axe des x le long du bord supérieur de l'image d'origine est mappé à la ligne traversant \(200, 20\) et \(110, 100\).  L'axe des y le long du bord gauche de l'image d'origine est mappé à la ligne traversant \(200, 20\) et \(250, 30\).  
  
 ![Rayures](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 L'illustration suivante présente une transformation similaire appliquée à une image photographique.  
  
 ![Climber transformé](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 L'illustration suivante présente une transformation similaire appliquée à un métafichier.  
  
 ![Métafichier transformé](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 L'exemple suivant produit les images présentées dans la première illustration.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Veillez à remplacer `Stripes.bmp` par le chemin d'accès à une image qui est valide sur votre système.  
  
## Voir aussi  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)