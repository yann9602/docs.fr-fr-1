---
title: "Rognage et mise &#224; l&#39;&#233;chelle d&#39;images dans GDI+ | Microsoft Docs"
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
  - "compresser des données, images"
  - "GDI+, rogner des images"
  - "GDI+, dimensionner des images"
  - "images (Windows Forms), compression"
  - "images (Windows Forms), rogner"
  - "images (Windows Forms), agrandissement"
  - "images (Windows Forms), mettre à l'échelle"
  - "rectangles, destination"
  - "rectangles, source"
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Rognage et mise &#224; l&#39;&#233;chelle d&#39;images dans GDI+
Vous pouvez utiliser la méthode <xref:System.Drawing.Graphics.DrawImage%2A> de la classe <xref:System.Drawing.Graphics> pour dessiner et positionner des images vectorielles et des images raster.  <xref:System.Drawing.Graphics.DrawImage%2A> est une méthode surchargée. Il existe donc plusieurs façons de lui fournir des arguments.  
  
## DrawImage, variantes  
 Une variante de la méthode <xref:System.Drawing.Graphics.DrawImage%2A> reçoit un objet <xref:System.Drawing.Bitmap> et un objet <xref:System.Drawing.Rectangle>.  L'objet Rectangle spécifie la destination de l'opération de dessin, c'est\-à\-dire le rectangle dans lequel l'image doit être dessinée.  Si la taille du rectangle de destination est différente de la taille de l'image d'origine, l'image est dimensionnée pour remplir le rectangle de destination.  L'exemple de code suivant montre comment dessiner trois fois la même image : sans dimensionnement, avec agrandissement et avec réduction.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 L'illustration suivante représente les trois images.  
  
 ![Mise à l'échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.png "AboutGdip03\_Art06")  
  
 Certaines variantes de la méthode <xref:System.Drawing.Graphics.DrawImage%2A> reçoivent comme paramètres un rectangle source et un rectangle de destination.  Le rectangle source spécifie la portion de l'image d'origine à dessiner.  Le rectangle de destination délimite la zone où cette portion de l'image doit être dessinée.  Si les deux rectangles ne sont pas de taille identique, l'image est dimensionnée pour remplir le rectangle de destination.  
  
 L'exemple de code suivant indique comment construire un <xref:System.Drawing.Bitmap> à partir du fichier Runner.jpg.  L'image entière est dessinée sans dimensionnement à la position \(0, 0\).  Une petite portion de l'image est ensuite dessinée deux fois : une fois avec compression et une fois avec expansion.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 L'illustration suivante représente l'image non ajustée et les portions réduite et agrandie de l'image.  
  
 ![Rognage et mise à l'échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.png "AboutGdip03\_Art07")  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)