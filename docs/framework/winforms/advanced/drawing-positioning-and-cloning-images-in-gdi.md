---
title: "Dessin, positionnement et clonage d&#39;images dans GDI+ | Microsoft Docs"
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
  - "dessiner, images"
  - "dessiner, images raster"
  - "GDI+, cloner les images"
  - "GDI+, dessiner des images"
  - "GDI+, positionner les images"
  - "images (Windows Forms), cloner"
  - "images (Windows Forms), dessiner"
  - "images (Windows Forms), positionner"
  - "images raster"
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Dessin, positionnement et clonage d&#39;images dans GDI+
Vous pouvez utiliser la classe <xref:System.Drawing.Bitmap> pour charger et afficher des images raster et la classe <xref:System.Drawing.Imaging.Metafile> pour charger et afficher des images vectorielles.  Les classes <xref:System.Drawing.Bitmap> et <xref:System.Drawing.Imaging.Metafile> héritent de la classe <xref:System.Drawing.Image>.  Pour afficher une image vectorielle, vous avez besoin d'une instance de la classe <xref:System.Drawing.Graphics> et d'un objet <xref:System.Drawing.Imaging.Metafile>.  Pour afficher une image raster, vous avez besoin d'une instance de la classe <xref:System.Drawing.Graphics> et d'un objet <xref:System.Drawing.Bitmap>.  L'instance de la classe <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawImage%2A> qui reçoit l'objet <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> en tant qu'argument.  
  
## Types de fichiers et clonage  
 L'exemple de code suivant montre comment construire un objet <xref:System.Drawing.Bitmap> à partir du fichier Climber.jpg et affiche la bitmap.  Le point de destination du coin supérieur gauche de l'image, \(10, 10\), est spécifié par les deuxième et troisième paramètres.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 L'illustration suivante représente l'image.  
  
 ![Exemple d'image](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.png "AboutGdip03\_Art04")  
  
 Vous pouvez construire des objets <xref:System.Drawing.Bitmap> à partir de plusieurs formats de fichier graphique : BMP, GIF, JPEG, EXIF, PNG, TIFF et ICON.  
  
 L'exemple de code suivant montre comment construire des objets <xref:System.Drawing.Bitmap> à partir de plusieurs types de fichiers, puis affiche les bitmaps.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 La classe <xref:System.Drawing.Bitmap> fournit une méthode <xref:System.Drawing.Bitmap.Clone%2A> qui permet de créer une copie d'un objet <xref:System.Drawing.Bitmap> existant.  La méthode <xref:System.Drawing.Bitmap.Clone%2A> admet comme paramètre un rectangle source qui vous permet de spécifier la portion de la bitmap d'origine à copier.  L'exemple de code suivant montre comment créer un objet <xref:System.Drawing.Bitmap> en clonant la moitié supérieure d'un objet <xref:System.Drawing.Bitmap> existant.  Il dessine ensuite les deux images.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 L'illustration suivante représente ces deux images.  
  
 ![Rognage](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.png "AboutGdip03\_Art05")  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)